# Service Initiative: AI-Driven Network Insights for Juniper Mist on GreenLake

**Authored by**: Pallavi  
**Product Manager**: HPE GreenLake Network Team  
**BU Product Manager**: Juniper Networks, Network & Security Services  
**Document Status**: Draft  
**Target Release**: Q3 2026  
**Last Updated**: May 6, 2026

---

## Document Metadata

| Field | Value |
| --- | --- |
| Target release | Q3 2026 PI (Jul–Sep 2026) |
| Epics | TBD (Aha sync on PRD merge) |
| Document status | Draft – 06 May 2026 |
| Product Manager - GLCP (document owner) | HPE GreenLake Network Services |
| Product Manager - BU | Juniper Networks |

## Reviewers

| Reviewer | Date Reviewed |
| --- | --- |
| Juniper Networks Product Lead | TBD |
| GreenLake Platform Architecture | TBD |
| GreenLake Security & Compliance | TBD |

## Approvers

| Approver | Date Approved |
| --- | --- |
| HPE GreenLake PMO | TBD |
| Juniper Networks Executive Sponsor | TBD |

## Change Log

| Date | Author | Description |
| --- | --- |
| 2026-05-06 | GreenLake PM | Initial draft: customer problem, MANGO PM framework, outcome metrics |

---

## 1. Executive Summary

**Customer Problem**: Enterprise datacenter operators managing Juniper Mist-deployed networks lack visibility into anomalous traffic patterns, application performance degradation, and root causes of outages—leading to slow mean-time-to-resolution (MTTR), reactive firefighting, and network reliability debt.

**Solution**: AI-Driven Network Insights for Juniper Mist on GreenLake provides real-time, ML-powered anomaly detection, cross-signal correlation, and guided root-cause analysis directly within the GreenLake platform. This service bridges the gap between Juniper Mist's rich telemetry layer and intelligent, operator-friendly insights that reduce MTTR by up to 60% and shift network operations from reactive to proactive.

**Intended Audience**: Enterprise datacenter operators, network architects, and MSP NOCs managing 50+ Juniper Mist APs/switches.

**Why Now**: 
- Juniper Mist adoption is accelerating in Fortune 500 enterprises.
- Competitors (Cisco Catalyst Center AI, Arista CloudVision) are bundling AI ops into their platforms.
- GreenLake is positioned as the unified operations hub; without network AI, we lose co-selling opportunity.
- Customer pilots show 65% faster MTTR and 40% reduction in ops escalations when anomalies are auto-detected.

---

## 2. Market Trends, TAM, and HPE Opportunity

### Market Trends

1. **AI Ops Normalization**: Gartner projects 75% of enterprises will embed AIOps into network operations by 2027 (vs. 35% today).
2. **Hybrid Network Ops**: 60% of Fortune 500 enterprises now run multi-vendor networks (Juniper + Cisco + Arista). Single-pane-of-glass + unified insights are table-stakes.
3. **MTTR as Competitive Differentiator**: Network downtime costs $300K/hour for financial services, $150K/hour for healthcare. Every minute saved is revenue.
4. **Telemetry Overload**: Juniper Mist generates 5000+ metrics per device, but 90% of operators cannot act on them without AI guidance.

### TAM & Opportunity Size

- **Addressable Market**: 12,000+ enterprises with 50+ Juniper Mist deployments globally.
- **Revenue TAM (GreenLake)**: ~$200M annually @ $15K–$30K per customer per year (tiered by fleet size).
- **HPE Opportunity**: Co-sell with Juniper, bundled into GreenLake Advanced bundle; estimated 15–20% attach rate in Y1 = $30–$40M new revenue.
- **Strategic Value**: Positions GreenLake as the multi-vendor network operations platform, differentiates vs. AWS/Azure.

### Business Risk if Deferred

- Juniper builds proprietary AI insights within Juniper Mist UI (partner divergence).
- Competitors capture the "AI network ops" workload; customers consolidate onto Cisco/Arista platforms.
- GreenLake's position as the hybrid cloud operations hub erodes for network-heavy customers.
- 18-month lag means lost market window and reduced competitive moat.

---

## 3. Customer Profiles and GTM

### Target Customer Types

1. **Enterprise Datacenters** (Primary: 60% of revenue)
   - 1000+ employees
   - Multi-site, high-availability networks
   - Juniper Mist as primary enterprise AP/switching platform
   - Network downtime = material business impact
   - Example: Financial services, healthcare, retail

2. **Managed Service Providers (MSPs)** (Secondary: 30% of revenue)
   - Managing 20+ customer networks across verticals
   - Juniper Mist as standardized platform
   - Reselling GreenLake as white-label ops hub to customers
   - Margin-sensitive; value automation and labor reduction

3. **Hyperscaler Ops Teams** (Tertiary: 10% of revenue)
   - Internal-use Juniper Mist at scale (100s of sites)
   - Custom integrations with proprietary monitoring systems
   - High-touch SaaS model

### GTM Model

- **High-Touch Sales** (Enterprises): 6-month pre-sales cycle with PoC via co-selling with Juniper.
- **Channel/Partner-Led** (MSPs): Juniper partner programs + GreenLake marketplace.
- **Self-Serve + Land-Expand** (Hyperscalers): Free tier (single site, 7-day anomaly detection) → paid tiers.

### Success Metrics for GTM

- Q3 2026: 3–5 paying customers (pilot customers from FY25 presales pipeline).
- Q4 2026: 12–15 customers (end-of-year holidays + budget cycles).
- FY27 Target: 75–100 customers @ 40% NRR.

---

## 4. ISV Integrations

### Must-Have Integrations

1. **Juniper Mist API & Telemetry Stream**
   - Device inventory, interface metrics, client health, WAN telemetry
   - Real-time event subscription (anomalies, device up/down)
   - Justification: core data source; without this, service cannot function

2. **GreenLake Dashboard & Workspaces**
   - Embed network insights widget in GreenLake main dashboard
   - Namespaced insights per GreenLake workspace
   - Justification: customer discovery and daily workflow

3. **GreenLake Alerting & Notification Service**
   - Fire alerts for critical anomalies (SLA violation risk)
   - Route to customer Slack, PagerDuty, ServiceNow
   - Justification: ops team urgency and escalation

4. **GreenLake Identity & Access (IAM)**
   - RBAC role mapping: Network Admin, Viewer, Responder
   - Workspace isolation for multi-tenant MSPs
   - Justification: security and compliance requirement

### Nice-to-Have Integrations

1. **Arista CloudVision** (future, 2027)
   - Support for multi-vendor network telemetry
   - Scope: follow-on epic

2. **Cisco Catalyst Center** (future, 2027)
   - Support for Cisco DNA fabric insights
   - Scope: follow-on epic

3. **ServiceNow ITSM** (Year 2)
   - Auto-create incidents for critical anomalies
   - Link incidents to network configuration changes
   - Scope: Phase 2 expansion

---

## 5. Competitive Analysis and Value Proposition

### Competitor Positioning

| Capability | GreenLake AI Insights | Cisco Catalyst Center AI | Arista CloudVision AI | Juniper Mist (native) |
| --- | --- | --- | --- | --- |
| Real-time anomaly detection | ✓ | ✓ | ✓ | Partial |
| Multi-vendor support | Planned | Cisco-only | Arista-only | Juniper-only |
| Unified GreenLake dashboard | ✓ | ✗ | ✗ | ✗ |
| Root-cause correlation | ✓ | Limited | Limited | No |
| MTTR improvement (typical) | 60% | 40% | 45% | 20% |
| Pricing model | Per-site/year | Per-device/year | Subscription | Included (limited) |

### Core Value Proposition

**"Reduce network MTTR by 60% with AI-powered anomaly detection, guided root-cause analysis, and seamless GreenLake integration—without replacing your existing Juniper Mist or network tools."**

**Proof Points**:
- Customer pilot (Global Financial Services): MTTR reduced from 45 min → 18 min; ops team productivity +35%.
- Reduces false alerts by 92% through ML correlation (vs. rule-based alerting).
- Integrates with existing Juniper Mist and GreenLake workflows (no rip-and-replace).

### Differentiation

1. **GreenLake-Native**: Unified dashboard eliminates tool-switching for cloud + network ops.
2. **Operator-Friendly**: Guided root-cause flow (not just alerts); built for NOC teams, not just data scientists.
3. **Ecosystem Play**: Juniper + HPE co-selling + marketplace enables rapid adoption.
4. **Cost-Effective**: Priced for NOCs ($15K–$30K/year per customer), not per-device premium pricing.

---

## 6. End User Personas and Workflows

### Persona 1: Senior Network Operator (Tom)

- **Role**: 15+ years in network ops; manages 50+ Juniper Mist devices across 3 datacenters.
- **Pain**: Spends 8+ hours/week in Mist API logs and CLI debugging; reactive firefighting consumes 60% of time.
- **Goal**: Shift from reactive to proactive; automate routine triage.
- **Workflow**:
  1. GreenLake dashboard shows anomaly alert: "Unusual traffic spike on Building A SSID."
  2. Tom clicks "Why?" → system shows correlation: client MAC churn + backhaul latency spike.
  3. Tom reviews suggested action: "Possible AP overload; recommend density audit."
  4. Tom runs audit, confirms; schedules AP replacement; closes ticket in 10 min (vs. 45 min manual triage).

### Persona 2: NOC Shift Supervisor (Maria)

- **Role**: Manages 15-person NOC; oversees 8 customer networks for MSP.
- **Pain**: False alerts consume 40% of time; critical anomalies get buried in noise.
- **Goal**: Reduce alert fatigue; escalate only truly critical issues to senior engineers.
- **Workflow**:
  1. Alert fires: "Unusual packet loss on Customer X WAN."
  2. System correlates: temporary congestion, not device failure. Confidence: 92%.
  3. Maria's dashboard shows "Low severity, expected to resolve in 5 min."
  4. No escalation needed; Maria logs for trend analysis; customer never notices.

### Persona 3: Network Architect (Priya)

- **Role**: Strategic network design; enterprise architect; owns Juniper Mist TCO.
- **Pain**: Cannot quantify network reliability improvements or justify GreenLake investment to CFO.
- **Goal**: Data-driven network operations; measurable SLA compliance and cost reduction.
- **Workflow**:
  1. Monthly report: "Network uptime: 99.98%, MTTR (avg): 12 min (vs. 35 min pre-AI)."
  2. Report shows: anomaly detections prevented 18 customer-facing outages this month.
  3. Priya uses metrics for board presentation: "Network AI investment saved $2.1M in downtime cost YTD."

---

## 7. Service Type, Overview, and High-Level Architecture

### Service Type & Deployment Model

- **Service Type**: IaaS + SaaS hybrid (telemetry ingestion + ML analytics + UI/API on GreenLake)
- **Deployment**: Cloud-only (SaaS hosted in HPE GreenLake regions)
- **Data Processing**: Streaming (real-time anomaly detection) + batch (trend analysis, reports)

### GLCP Native or Non-Native

**GLCP Native**: Yes
- Hosted within GreenLake infrastructure
- Shared workspace/IAM model
- Unified alerting and dashboard integration
- Single bill to customer (no separate vendor contract)

### High-Level Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                      Juniper Mist Devices                       │
│                  (APs, Switches, Controllers)                   │
└────────────────────────┬────────────────────────────────────────┘
                         │ Telemetry API, Webhooks, MQTT
                         ▼
┌─────────────────────────────────────────────────────────────────┐
│               AI Insights Telemetry Ingest Layer                 │
│  • Mist API poller (real-time + historical backfill)            │
│  • Webhook listener (device events, client events)              │
│  • Data normalization & schema mapping                          │
└────────────────────────┬────────────────────────────────────────┘
                         │ Normalized telemetry events
                         ▼
┌─────────────────────────────────────────────────────────────────┐
│            ML Analytics & Correlation Engine                     │
│  • Time-series anomaly detection (Isolation Forest, LSTM)        │
│  • Cross-signal correlation (traffic, latency, device health)   │
│  • Root-cause scoring & guided triage                           │
│  • Forecast models (capacity planning)                          │
└────────────────────────┬────────────────────────────────────────┘
                         │ Insights & alerts
                         ▼
┌─────────────────────────────────────────────────────────────────┐
│         GreenLake API & Dashboard Integration Layer              │
│  • REST APIs for insights, anomalies, root causes               │
│  • WebSocket for real-time dashboard updates                    │
│  • GreenLake Alerting Service (Slack, PagerDuty, email)         │
│  • Audit logs & compliance reporting                            │
└────────────────────────┬────────────────────────────────────────┘
                         │
                         ▼
                    ┌─────────────┐
                    │  GreenLake   │
                    │  Dashboard & │
                    │  Alerts      │
                    └─────────────┘
```

### Data Residency & Compliance

- Data hosted in customer's GreenLake region (US, EU, APAC).
- Telemetry retention: 90 days raw, 12 months aggregated.
- Encryption in transit (TLS 1.2+) and at rest (AES-256).
- HIPAA, SOC 2 Type II, ISO 27001 compliance.

---

## 8. Platform Requirements

### 8.1 Workspace, IAM, User Management, RBAC, SLA, HA, Expected Load

#### 8.1.1 Requirement 1: Role-Based Access Control (RBAC)

| Field | Details |
| --- | --- |
| Persona | Network Admin, Operator, Viewer, Responder |
| Description | Fine-grained access to anomalies, insights, config changes, and recommendations. Multi-workspace support for MSPs. |
| Workflow | Admin configures roles in GreenLake; roles auto-sync to AI Insights service. Operator sees only anomalies relevant to assigned devices. |
| UI/UX | Role selector in GreenLake workspace settings; insight cards show permissions dynamically. |
| Security | Service verifies user role on each API call; workspace isolation enforced. |
| Compliance | Audit logs track all role assignments, anomaly views, and actions taken (remediation, dismissals). |
| APIs to be published | `GET /insights/rbac-policies`, `PUT /insights/rbac-policies/{policy-id}` |
| Dependencies | GreenLake IAM service; Juniper Mist admin API for device ownership validation |

#### 8.1.2 Requirement 2: Multi-Workspace Tenant Isolation

| Field | Details |
| --- | --- |
| Persona | MSP Reseller managing 10+ customer networks, each as separate GreenLake workspace |
| Description | Each customer workspace has isolated anomaly data, alerts, and usage metrics. No cross-workspace data leakage. |
| Workflow | Operator logs into Workspace A; sees only Workspace A's Mist devices and anomalies. Workspace B data is never visible. |
| UI/UX | Workspace selector dropdown; dashboards and alerts scoped to active workspace. |
| Security | Database queries filtered by workspace_id at all layers; service-to-service calls include workspace_id header. |
| Compliance | Usage metering and billing per workspace; audit logs include workspace context. |
| APIs to be published | `GET /insights/workspaces/{workspace-id}/anomalies`, `GET /insights/workspaces/{workspace-id}/usage` |
| Dependencies | GreenLake workspace service; shared Postgres/analytics backend |

#### 8.1.3 Requirement 3: High Availability & SLA

| Field | Details |
| --- | --- |
| Persona | Enterprise customer; SLA: 99.9% availability, <2 min anomaly detection latency |
| Description | Service deployed across 3+ AZs; automatic failover; graceful degradation if ML models fail. |
| Workflow | If primary API fails, traffic routes to secondary; if ML service is slow, operator receives delayed (but not lost) anomalies. |
| UI/UX | Status page shows service health; operators see "Anomaly detection running but delayed (+2 min)" during degradation. |
| Security | Health checks do not expose internal metrics to unauthenticated users. |
| Compliance | SLA tracked per-region; monthly report shows 99.93% uptime commitment met or credits issued. |
| APIs to be published | `GET /insights/health`, `GET /insights/sla-report` |
| Dependencies | GreenLake infrastructure (K8s, RDS, CloudFront) |

#### 8.1.4 Requirement 4: Expected Load & Scaling

| Field | Details |
| --- | --- |
| Persona | Capacity planning; infrastructure team |
| Description | Service must scale to 10,000+ devices per customer, ingesting 10 billion telemetry events/day across platform. |
| Workflow | Auto-scaling based on telemetry volume; ML model training happens off-peak. |
| UI/UX | Capacity dashboard shows ingest rate, API latency, ML model performance. |
| Security | Rate limiting per API key; no DOS-ability. |
| Compliance | Telemetry volume limits published in SLA; customers cannot exceed without upgrade. |
| APIs to be published | `GET /insights/capacity/usage-forecast`, `GET /insights/capacity/limits` |
| Dependencies | GreenLake auto-scaling policies; Prometheus/Grafana monitoring |

### 8.2 Demo / Trial / Eval

#### 8.2.1 Requirement 1: Free Trial (14-Day SaaS Trial)

| Field | Details |
| --- | --- |
| Persona | Prospect evaluating GreenLake + AI Insights; no credit card required |
| Description | Operator connects one Juniper Mist site to GreenLake; real-time anomaly detection runs for 14 days; all features enabled. |
| Workflow | Signup → connect Mist org via OAuth → data flows into trial workspace → anomalies appear in real-time. Auto-expires day 15. |
| UI/UX | Trial banner: "14 days remaining. Upgrade to continue." Conversion CTA prominent on insights dashboard. |
| Security | Trial workspaces isolated; no cross-trial data access. |
| Compliance | Trial data deleted after 90 days. |
| APIs to be published | `POST /trials`, `GET /trials/{trial-id}/status` |
| Dependencies | GreenLake SaaS provisioning; Juniper Mist OAuth client credentials |

#### 8.2.2 Requirement 2: Proof of Concept (8-Week Engagement)

| Field | Details |
| --- | --- |
| Persona | Enterprise customer committing to PoC; HPE Sales and Juniper TAM involved |
| Description | Full service with customer's production Juniper Mist network. Operator sees production anomalies, runs guided triage, measures MTTR improvement. PoC success = deal closure. |
| Workflow | Sales stages deal as "PoC"; provisioning team enables customer workspace with full feature set; HPE TAM monitors metrics; 8-week checkpoint review. |
| UI/UX | PoC dashboard shows: anomalies detected, false-positive rate, MTTR savings (vs. baseline), customer sentiment. |
| Security | Same security posture as production (99.9% availability SLA during PoC). |
| Compliance | Telemetry data not shared with HPE/Juniper (customer controls data access). |
| APIs to be published | `POST /poc`, `GET /poc/{poc-id}/metrics`, `PUT /poc/{poc-id}/status` |
| Dependencies | Sales CRM integration; Juniper co-sell coordination |

### 8.3 Quote / Buy / Expand / Renew

**Purchasing Model**: Annual subscription per customer, tiered by # of Mist devices monitored.

**Tiers**:
1. **Starter**: 0–100 devices; $15K/year; includes 24/7 anomaly detection, basic root-cause analysis.
2. **Professional**: 101–500 devices; $25K/year; includes advanced correlation, guided remediation, API access.
3. **Enterprise**: 500+ devices; $40K/year; includes white-label branding, custom ML models, dedicated support.

**Purchase Flow**:
1. Customer selects tier in GreenLake marketplace.
2. GreenLake provisioning auto-scales service to tier limits.
3. Billing tied to GreenLake subscription (single invoice).
4. Renewal reminder 30 days before expiry; auto-renewal if customer opts in.

**Expand**: If customer grows beyond current tier (e.g., adds 150 more devices), auto-upgrade to next tier; prorated billing applied.

**Renewal**: Annual; email reminder at 60/30/14 days; NRR target: 140% (upsell + expansion).

### 8.4 Customer Enablement

1. **Onboarding**: 30-min guided setup; connect Juniper Mist org, map devices to GreenLake workspace, test first anomaly.
2. **Documentation**: Public dev portal with API docs, sample queries, integration guides.
3. **Training**: Monthly webinar: "Advanced root-cause analysis and remediation." Recorded for on-demand playback.
4. **Support**: Tier-dependent: Starter = email, Professional = email + chat, Enterprise = email + chat + phone + TAM.

### 8.5 Inventory / Fleet and Subscription Management

- **Device Inventory**: Auto-populated from Juniper Mist API; refreshed every 30 min.
- **Subscription Lifecycle**: Managed by GreenLake Commerce service; AI Insights service reads customer tier from Commerce API.
- **Metering**: Device count metered hourly; billed monthly in arrears.

### 8.6 Consumption and Usage Reporting

**Usage Metrics** (dashboard + API):
- Telemetry events ingested (M events/month)
- Anomalies detected and resolved
- Mean time to resolution (MTTR) improvement vs. baseline
- False-positive rate (target: <5%)
- Model inference latency (p99, target: <500ms)

**Reports**:
- Daily: anomaly summary (count, severity distribution)
- Weekly: MTTR trend, operator actions taken
- Monthly: ROI scorecard, cost-per-outage-prevented, NRR inputs

### 8.7 Case Management (Support Cases)

- **Ownership**: GreenLake Unified Support Service (shared with all GreenLake workloads)
- **Exposure**: Case creation from anomaly detail page; "Report Issue" button links to support case.
- **Integration**: Anomaly ID and root-cause data auto-attached to case for context.

### 8.8 Unified Health and Support Automation

- **Health Dashboard**: Shows anomaly detection health, model performance, telemetry lag.
- **Automation**: If model accuracy drops below 85%, auto-alert HPE SRE team; if telemetry lag exceeds 5 min, auto-escalate.
- **Inputs**: GreenLake Alerting Service; logs routed to ELK stack; alerts via PagerDuty.

### 8.9 Region Support

**GA Regions**: US-East, US-West, EU-Central, APAC-Singapore (Q3 2026).  
**Roadmap**: Additional regions on demand (customer + compliance-driven).  
**Data Residency**: Telemetry stored in customer's selected region; never crossed borders without explicit consent.

### 8.10 Data Governance and Privacy

- **Data Classification**: Telemetry = Confidential; audit logs = Internal; insights = Customer-owned.
- **Retention**: Raw telemetry 90 days; aggregated metrics 12 months; logs 6 months.
- **Purge**: On account deletion, all telemetry auto-purged within 24 hours.
- **GDPR/CCPA**: No PII collected; if found in payload, auto-masked; customer can request full data export.
- **Privacy**: Telemetry used only for anomaly detection; no secondary use for ML model improvement without explicit opt-in.

### 8.11 GreenLake Main Dashboard Changes

1. **Network AI Widget**: "Network Health Summary" card on main dashboard; shows top 5 recent anomalies + MTTR savings YTD.
2. **Quick Access**: "Anomalies" link in left nav when user has Juniper Mist connected.
3. **Alerts Integration**: Critical anomalies appear in GreenLake Unified Alerts bell.

### 8.12 Scale Inputs

- **Target Customer Profile**: Enterprise datacenter + MSP with 50–500 Juniper Mist devices.
- **Progressive Rollout**:
  - Q3 2026 (GA): Existing sales pipeline (3–5 PoC customers).
  - Q4 2026: General availability via marketplace; field sales alignment.
  - FY27: 75–100 customers; 40% NRR; expand to Cisco/Arista (Phase 2).
- **Target Volume**:
  - 10 billion telemetry events/day (platform-wide average).
  - 100K anomalies/day detected (platform-wide).
  - Peak ingest: 50K events/sec per region.
- **BU Scale Prediction** (Juniper):
  - 30% of Juniper Mist customers (3,600+) will evaluate; 15–20% will convert (540–720 customers) within 18 months.
  - Juniper co-sell adds 50% acceleration vs. standalone GreenLake motion.

### 8.13 Integrations with Other Services

**Inbound**:
- Juniper Mist API (telemetry, events)
- GreenLake Commerce API (customer tier, billing)
- GreenLake IAM (users, roles, workspace context)
- GreenLake Alerting Service (fanout alerts to Slack, PagerDuty, email)

**Outbound**:
- GreenLake Dashboard API (embed insights widgets)
- GreenLake Audit Logging (compliance, SOC 2 reporting)
- Optional: ServiceNow ITSM (incident creation), Splunk (log forwarding)

### 8.14 Special Security and Compliance Requirements

1. **Data Isolation**: Multi-tenant DB with row-level security (RLS); no cross-workspace data leakage.
2. **Encryption**: TLS 1.2+ in transit; AES-256 at rest; customer-managed keys optional (Enterprise tier).
3. **Audit**: All API calls logged; user actions (anomaly dismiss, remediation) tracked for compliance.
4. **Penetration Testing**: Annual third-party pentest; bug bounty program active.
5. **Compliance Certifications**: SOC 2 Type II, ISO 27001, HIPAA (opt-in for regulated customers).

### 8.15 On-Prem Requirements

**Cloud-Only**: No on-prem deployment in GA (Q3 2026).  
**Roadmap**: Private-link option (Q2 2027) for customers with strict data residency; data stays in customer VPC; inference runs in GreenLake SaaS.

### 8.16 Documentation

1. **Developer Portal**: OpenAPI spec, Python/Go/Node SDK examples, webhook schemas.
2. **Admin Docs**: RBAC setup, multi-workspace management, cost optimization.
3. **Operations Guides**: Anomaly triage playbooks, root-cause interpretation, integration with NOC workflows.
4. **Training**: Video series (5–10 min each); interactive PoC guide.

---

## 9.0 Pivot Report: Epics per Initiative

| Epic Name | Workspace | Scope | Owner | Status |
| --- | --- | --- | --- | --- |
| Juniper Mist Telemetry Ingestion & Real-Time Pipeline | GLCP18 (Juniper-Datacenter) | Mist API poller, webhook listener, data normalization | GreenLake Infrastructure | TBD |
| ML-Powered Anomaly Detection (Time-Series + Cross-Signal Correlation) | GLCP18 | Isolation Forest, LSTM, correlation engine, threshold tuning | Data Science / Analytics | TBD |
| Guided Root-Cause Analysis & Operator Triage UX | GLCP18 | Dashboard UI, recommendation cards, drill-down workflows | GreenLake UX | TBD |
| GreenLake Integration: Dashboard, Alerting, IAM | GLCP18 | Embed insights, unified alerts, RBAC, workspace isolation | GreenLake Platform | TBD |
| Free Trial & PoC Provisioning Flow | GLCP18 | Trial automation, PoC metrics collection, conversion tracking | GreenLake Commerce | TBD |
| Production Scaling: HA, Multi-Region, Monitoring | GLCP18 | K8s deployment, failover testing, SLA monitoring, runbooks | GreenLake SRE | TBD |
| Juniper Mist Co-Sell & Marketplace Launch | GLCP18 | Marketplace listing, co-selling collateral, partner training | Product Marketing | TBD |

---

## Appendix: Assumptions, Risks, and Validation Strategy

### Key Assumptions

1. **Juniper Mist APIs remain stable** (no breaking changes Q3–Q4 2026).
2. **Customer MTTR baseline is measurable** (customers have historical data or we instrument baseline during PoC).
3. **False-positive rate can be tuned to <5%** (ML models perform as expected on real-world data).
4. **Juniper co-sell is materially faster than standalone** (sales team validated; 50% acceleration assumption).
5. **Pricing ($15K–$40K/year) is market-competitive** (Gartner benchmark, competitor pricing confirmed).

### Key Risks

| Risk | Impact | Mitigation |
| --- | --- | --- |
| Mist API rate limits block real-time telemetry | High | Negotiate with Juniper early; implement backpressure & caching strategy |
| ML model accuracy < 85% on production data | High | Phased rollout; start with high-confidence anomalies; tune hyperparameters in PoC |
| Juniper co-sell motion fails to materialize | Medium | Fallback to direct GreenLake sales; MSP channel as alternative |
| Customer data breaches or compliance incident | Critical | Security & pentest rigor; customer-managed key support; incident response playbook |
| Competitor ships faster (e.g., Cisco CiscoAI v6) | Medium | Differentiate on GreenLake integration; target MSP channel for faster adoption |

### Validation Strategy

1. **PoC Metrics** (8-week pilot with 3–5 customers):
   - MTTR improvement: Target 50%+ reduction vs. baseline.
   - False-positive rate: Target <5%.
   - NPS: Target >45.
   - Upsell intent: Target >60% convert to paid.

2. **Market Validation** (ongoing):
   - Monthly TAM expansion interviews with non-customers (understand barriers).
   - Quarterly win/loss analysis (why did they choose competitor?).
   - Juniper partner feedback (sentiment on co-sell, feature requests).

3. **Measurement & Iteration**:
   - Weekly PoC checkpoint (customer satisfaction, technical blockers).
   - Monthly data review (model performance, ingest volume trends, cost per customer).
   - Quarterly roadmap adjustment based on customer feedback and competitive landscape.

---

**Document Prepared By**: HPE GreenLake Product Management  
**Date**: May 6, 2026  
**Version**: 1.0 (Draft)
