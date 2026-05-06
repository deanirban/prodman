# ML-Powered Anomaly Detection: Time-Series and Cross-Signal Correlation

## Problem Statement

Enterprise datacenter operators running Juniper Mist networks are blind to network anomalies until they manifest as user-facing outages or performance degradation. Current detection methods rely on static thresholds (interface utilization >80%, latency >100ms), which generate 60%+ false positives and miss subtle anomalies like asymmetric traffic patterns, cascading client churn, or bandwidth hoarding from rogue devices. This forces operators into reactive firefighting mode: MTTR averages 45 minutes, and teams spend 40–60% of their time triaging false alarms instead of strategic work. The broken moment: an operator discovers a critical anomaly only when a customer calls in to report connectivity issues.

## Goal

Deliver real-time, ML-powered anomaly detection for Juniper Mist networks that:
1. **Detects genuine anomalies** with <5% false-positive rate (vs. 60%+ rule-based)
2. **Correlates cross-signal root causes** (e.g., "client churn triggered by AP power loss + backhaul latency spike")
3. **Reduces mean time to resolution (MTTR)** from 45 minutes to <18 minutes (60% improvement)
4. **Operates in real-time** (<500ms latency from telemetry ingestion to insight delivery)
5. **Scales to 10,000+ devices per customer** with sub-100ms inference latency (p99)

Success: Pilot customers achieve 50%+ MTTR reduction and <5% false positives within 8 weeks of PoC launch.

## Functional Requirements

### ML Model Training & Inference

1. **Time-Series Anomaly Detection (Isolation Forest + LSTM)**
   - Train on 30-day rolling baseline of telemetry (ingress/egress traffic, latency, jitter, client count, AP power, band utilization)
   - Real-time scoring: for each new metric point, compute anomaly score (0–1; >0.75 = anomaly)
   - Adaptive baseline: retrain models daily to account for time-of-day patterns, day-of-week effects, seasonal trends
   - Handle data gaps gracefully (missing telemetry for <5 min = forward fill; >5 min = reset baseline)

2. **Cross-Signal Correlation Engine**
   - Link related anomalies within 5-min sliding window (e.g., "AP power off" → expected drop in client count 2 min later)
   - Score causality confidence (0–1); confidence >0.8 = likely root cause
   - Generate human-readable correlation narratives: "AP Building-A-Floor-3 went offline (timestamp T); client churn spiked 2 min later"

3. **Model Performance & Monitoring**
   - Track model accuracy (precision, recall, F1) on hold-out validation set (20% of data)
   - Alert if accuracy drops below 85% for any model; trigger auto-retraining
   - Inference latency tracking (p50, p95, p99); alert if p99 > 500ms

### Data Pipeline & Feature Engineering

4. **Real-Time Telemetry Ingest from Juniper Mist**
   - Ingest via Mist REST API (poll every 30 sec) + Mist webhooks (event-driven)
   - Extract features: per-AP, per-SSID, per-client-type, per-band
   - Normalize and handle outliers (e.g., temporary spikes from device reboots)

5. **Feature Store & Data Warehouse**
   - Append telemetry to time-series DB (e.g., InfluxDB or Postgres with TSDB extension)
   - Hourly aggregation for trend analysis; raw 30-sec data for real-time anomaly scoring
   - Data retention: 90 days raw, 12 months aggregated

### Anomaly Output & Presentation

6. **Anomaly Event Schema**
   - Each anomaly record: timestamp, device_id, workspace_id, anomaly_type, severity (critical/high/medium), affected_metric, anomaly_score, confidence, root_cause_candidate, recommendation
   - Persist to database for audit, trends, reporting

7. **Real-Time Alert / Notification Pathway**
   - On anomaly detection: publish event to GreenLake Alerting Service
   - Deduplicate within 10-min window (if same device, same metric, same root cause → single alert)
   - Support alert rules: critical anomalies → always notify; medium → daily digest

### Tuning & Feedback Loop

8. **Feedback & Model Refinement**
   - Operators can mark anomalies as "false positive" or "true positive" in dashboard
   - Collect feedback; retrain models weekly using feedback-labeled data
   - A/B test model versions (new vs. baseline); deploy winner if ≥95% performance parity

## Acceptance Criteria

### Positive Cases

1. ✓ **Real AP Power Loss**: When an AP powers off, service detects client count drop within 30 sec; confidence >0.9; root-cause narrative: "AP [name] offline"
2. ✓ **Backhaul Latency Spike**: When WAN link is congested, latency anomaly detected; correlated with upstream device anomaly (if available)
3. ✓ **Client Churn Cascade**: When rogue device blocks DHCP, client count drops sharply; anomaly detected; recommendation: "DHCP block suspected; check rogue AP"
4. ✓ **Asymmetric Traffic**: When one SSID receives 10x ingress traffic, anomaly detected; severity high (potential DoS); customer alerted
5. ✓ **Temporal Pattern**: Monday 9 AM spike in client count (normal behavior) does NOT trigger anomaly (baseline adjusts for time-of-day)
6. ✓ **Multi-Signal Correlation**: Device failure (power loss + latency spike + client drop all within 30 sec) → single correlated anomaly event (not 3 separate events)
7. ✓ **Sub-500ms Latency**: Anomaly detected and delivered to GreenLake dashboard within 500ms of metric arrival (p99)
8. ✓ **Scale to 10K Devices**: Service processes 10K devices, 50K metrics/sec, <100ms inference latency (p99)

### Negative Cases

1. ✓ **False-Positive Suppression**: Rule-based anomalies (>80% utilization) not surfaced unless ML confirms (target: <5% false-positive rate)
2. ✓ **Cascading Alerts Suppressed**: When correlated event detected, child anomalies not separately surfaced (1 rich event instead of 5 noise alerts)
3. ✓ **No Alert on Transient Blip**: 1-sec latency spike (not sustained) not flagged as anomaly
4. ✓ **Graceful Degradation**: If ML model fails, system does not break; fall back to rule-based detection with explicit "degraded mode" indicator

### Non-Functional Requirements

5. ✓ **Accuracy**: Precision ≥0.95, Recall ≥0.90 on hold-out test set (baseline: rule-based ~0.4 precision, 0.7 recall)
6. ✓ **Availability**: Model training does not block real-time inference (async retraining, model versioning)
7. ✓ **Data Privacy**: Telemetry processed per workspace; cross-workspace data never mixed; audit logs track all model decisions
8. ✓ **Explainability**: For each anomaly, operator can drill into "why" (which signals triggered, confidence scores, correlation chain)

## Non-Goals (Phase 2 / Follow-On)

- Multi-vendor correlation (Cisco, Arista networks) → Phase 2 epic
- Custom ML model per customer → deferred; shared models sufficient for GA
- Real-time model retraining (hourly retraining acceptable; real-time training out of scope)
- Self-healing (auto-remediation) → separate epic; operator-driven triage only for GA

## Dependencies

### Upstream (Must Complete First)

1. **Juniper Mist Telemetry Ingestion & Real-Time Pipeline** (parallel epic)
   - Responsible for telemetry data availability, normalization, schema consistency
   - ML team consumes telemetry from this pipeline's output

2. **GreenLake Infrastructure** (existing)
   - Kubernetes cluster for model training/inference; auto-scaling
   - Postgres/InfluxDB for feature store; shared by all services
   - GreenLake Alerting Service for fanout

### Downstream (Depends on This Epic)

1. **Guided Root-Cause Analysis & Operator Triage UX** (parallel epic)
   - Consumes anomaly events from this epic; renders in dashboard
   - Feedback from UI → feeds back to model retraining

2. **GreenLake Integration: Dashboard, Alerting, IAM** (parallel epic)
   - Visualizes anomalies and metrics from this service

## Metrics & Success Criteria

### Primary Outcome Metrics

- **MTTR Improvement**: Pilot customers achieve ≥50% MTTR reduction (baseline 45 min → target <22 min)
- **False-Positive Rate**: <5% false positives (vs. 60% for rule-based)
- **Anomaly Detection Latency**: <500ms (p99) from telemetry ingestion to operator alert

### Secondary / Guardrail Metrics

- **Model Accuracy**: Precision ≥0.95, Recall ≥0.90
- **Inference Latency**: <100ms (p99) for 10K-device workload
- **Data Freshness**: Anomalies detected within 30 sec of anomaly onset (baseline telemetry: 30-sec intervals)
- **Correlation Accuracy**: ≥80% of multi-signal anomalies correctly attributed to root cause (validated by operator feedback)

### Adoption & Quality Indicators

- **Model Retraining Frequency**: Daily (sufficient for weekly feedback loop)
- **Operator Feedback Loop**: ≥20% of anomalies marked as "true positive" or "false positive" by pilots (used to tune models)
- **Alert Fatigue Score**: <2 alerts/device/day (vs. 8–10 for rule-based)

## Implementation Strategy & Phasing

### Phase 1 (Q3 2026 – Weeks 1–6): MVP Model Training & Inference

- Collect 2 weeks of production telemetry from pilot customers
- Train Isolation Forest + LSTM models on baseline data
- Deploy real-time inference (batch scoring every 30 sec)
- Test on small cohort (1–2 pilot sites); validate accuracy & latency
- Manual feedback loop via Slack/email for model refinement

### Phase 2 (Q3 2026 – Weeks 7–10): Cross-Signal Correlation & Dashboard Integration

- Implement correlation engine (link multi-signal anomalies within 5-min window)
- Integrate with GreenLake dashboard widget (show anomalies + recommended actions)
- Automated feedback collection (UI buttons: "Mark as False Positive" / "Mark as True Positive")
- Weekly model retraining using feedback

### Phase 3 (Q4 2026): Production Scaling & HA

- Multi-region deployment (US-East, US-West, EU, APAC)
- Auto-scaling: scale inference to 10K devices, p99 latency <100ms
- Model versioning & canary deployment (test new models on 10% of traffic before rollout)
- SLA monitoring & incident response playbooks

## Ownership & Resourcing

- **Data Science Lead**: ML model development, training, accuracy testing
- **Backend Engineer**: Telemetry ingestion pipeline, feature store, inference service, real-time alerting
- **Infrastructure Engineer**: Model training infrastructure (auto-scaling, monitoring, cost optimization)
- **QA Engineer**: Model validation, edge-case testing, performance benchmarking

**Estimated Effort**: 12–16 person-weeks (Data Science: 6 weeks, Backend: 8 weeks, Infrastructure: 4 weeks, QA: 4 weeks)

## References & Related Epics

- **Related Epic**: Juniper Mist Telemetry Ingestion & Real-Time Pipeline (data source)
- **Related Epic**: Guided Root-Cause Analysis & Operator Triage UX (consumer of anomalies)
- **Related Epic**: Production Scaling: HA, Multi-Region, Monitoring (operational hardening)

---

**Status**: Draft – Under Review  
**Workspace**: GLCP18 (Juniper-Datacenter)  
**Date**: May 6, 2026  
**Last Updated**: Testing change request process
