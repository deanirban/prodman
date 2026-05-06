# HC-PC Proactive Operations Health and Incident Prevention Service PRD

All fields in this document are mandatory. Do not delete any questions or fields.
If a field does not apply, write N/A.

## Document Metadata

| Field | Value |
| --- | --- |
| Target release | PI-2026-Q3 (Target GA: 30-Sep-2026) |
| Epics | GLCP17-E-Proposed-001, GLCP17-E-Proposed-002, GLCP17-E-Proposed-003 |
| Document status | Draft v1 (06-May-2026) |
| Product Manager - GLCP (document owner) | GLCP PM - HC-PC |
| Product Manager - BU | HC-PC BU PM |

## Reviewers

| Reviewer | Date Reviewed |
| --- | --- |
| HC-PC Engineering Lead |  |
| GLCP Platform Architect |  |

## Approvers

| Approver | Date Approved |
| --- | --- |
| GLCP PM Director |  |
| HC-PC BU PM Director |  |

## Change Log

| Date | Author | Description |
| --- | --- | --- |
| 2026-05-06 | GitHub Copilot + PM input | Initial draft PRD created from service template |
|  |  |  |

## 1. Executive Summary

HC-PC customers currently detect many operational issues after service degradation has already started, resulting in increased MTTR, avoidable incidents, and escalations. This PRD defines a proactive operations health capability for HC-PC that surfaces leading indicators, risk alerts, and guided actions before outages occur. The service targets ITOps and SRE personas, reducing reactive firefighting and improving service reliability outcomes.

## 2. Market Trends, TAM, and HPE Opportunity (BU PM)

Enterprise private cloud buyers increasingly evaluate platforms on day-2 operations maturity, especially incident prevention, health visibility, and guided remediation. Competing platforms emphasize operational analytics and proactive insights as standard capabilities, not add-ons.

HPE opportunity:
- Increase HC-PC stickiness through measurable reliability improvements.
- Reduce support cost-to-serve by lowering avoidable incidents and ticket volume.
- Improve expansion and renewal likelihood by proving operational value in first 90 days.

What happens if we do not implement this service:
- Continued reactive operations posture.
- Higher incident rates and lower customer confidence.
- Competitive disadvantage in renewal and net-new opportunities where proactive operations is a buying criterion.

## 3. Customer Profiles and GTM (BU PM)

Target customers:
- Mid-to-large enterprise private cloud customers.
- Regulated industries requiring operational evidence and auditability.
- Existing HC-PC customers with recurring Sev2/Sev3 incident patterns.

GTM model:
- Included as an HC-PC service capability for existing customers.
- Partner-led enablement for managed service providers.
- CSM-assisted adoption playbook for top strategic accounts.

## 4. ISV Integrations (BU PM)

Must-have:
- ServiceNow (incident and change context enrichment).
- OpsRamp (alert and health signal federation where available).

Nice-to-have:
- PagerDuty (incident notification routing).
- Splunk (cross-platform observability correlation).

## 5. Competitive Analysis and Value Proposition (BU PM)

Competitive direction:
- Major platforms offer predictive health views, anomaly detection, and remediation guidance integrated into operations dashboards.
- Differentiation increasingly depends on practical guidance and reduced operational burden, not only raw telemetry.

HC-PC value proposition:
- Proactive risk visibility with clear recommended actions.
- Operationally actionable insights in GLCP workflows used by customers today.
- Evidence-backed reliability improvements (MTTD/MTTR and incident reduction) without requiring separate tooling adoption.

## 6. End User Personas and Workflows (BU PM and GLCP PM)

Target personas:
- ITOps Manager (service reliability owner).
- SRE / Operations Engineer (day-to-day incident responder).
- Cloud Platform Admin (policy and configuration owner).

Typical workflows:
1. Daily health review: user opens Health Summary and sees prioritized risks.
2. Preventive action: user drills into risk cluster and executes recommended remediations.
3. Incident avoidance validation: user confirms risk score reduction and no downstream incidents.
4. Weekly operations review: leadership reviews incident-prevention metrics and unresolved risks.

## 7. Service Type, Overview, and High-Level Architecture (BU PM and GLCP PM)

Service type:
- SaaS operations capability within HC-PC experience in GLCP.

GLCP placement:
- Service is exposed via HC-PC workspace experience in GLCP.
- Uses platform identity, RBAC, notification, and audit services.

High-level architecture:
- Signal ingestion from HC-PC operational telemetry and platform events.
- Risk scoring and correlation service computes prioritized risk items.
- Action recommendation layer maps risk patterns to remediation playbooks.
- UX surfaces summary, detail, and action workflows.

## 8. Platform Requirements

### 8.1 Workspace, IAM, User Management, RBAC, SLA, HA, Expected Load

#### 8.1.1 Requirement 1: IAM (link to Aha)

| Field | Details |
| --- | --- |
| Persona | ITOps Manager |
| Description | ITOps Manager can view org/workspace health posture and assign remediation ownership. |
| Workflow | Login -> open HC-PC Health -> filter by workspace -> assign recommended action owner. |
| UI/UX | Health dashboard with role-aware visibility and assignment controls. |
| Security | Read access to risk data must follow workspace scope boundaries. |
| Compliance | All assignments and status updates must be auditable. |
| APIs to be published | GET /health/risks, POST /health/risks/{id}/assign, PATCH /health/risks/{id}/status |
| Dependencies (BU product, IT, other systems) | GLCP IAM, HC-PC telemetry pipeline, audit service |

#### 8.1.2 Requirement 2: IAM (link to Aha)

| Field | Details |
| --- | --- |
| Persona | SRE / Operations Engineer |
| Description | SRE can view actionable remediation steps for owned workspaces and update execution state. |
| Workflow | Alert received -> open risk detail -> execute remediation -> mark complete -> attach evidence. |
| UI/UX | Guided action panel with prerequisites, expected impact, and confirmation prompts. |
| Security | Edit actions allowed only for roles with remediation permission. |
| Compliance | Action logs retained per GLCP retention policy. |
| APIs to be published | GET /health/risks/{id}, POST /health/risks/{id}/actions/{actionId}/execute |
| Dependencies (BU product, IT, other systems) | RBAC service, policy engine, support automation hooks |

### 8.2 Demo/Trial/Eval (link to Aha)

- Yes. A guided trial mode will be offered to strategic customers and partner demos.

#### 8.2.1 Requirement 1: Demo (link to Aha)

| Field | Details |
| --- | --- |
| Persona | ITOps Manager |
| Description | Demonstrate end-to-end risk detection to mitigation closure in a sample environment. |
| Workflow | Enable trial dataset -> open dashboard -> investigate top risk -> execute suggested action. |
| UI/UX | Demo tag on synthetic insights to differentiate from production data. |
| Security | Demo data isolated from customer production data. |
| Compliance | Demo mode usage logged for auditing. |
| APIs to be published | POST /demo/sessions, GET /demo/risks |
| Dependencies (BU product, IT, other systems) | Demo tenant provisioning, sample data generator |

#### 8.2.2 Requirement 2: Demo (link to Aha)

| Field | Details |
| --- | --- |
| Persona | Channel Partner |
| Description | Partner can run a standardized demo script for customer workshops. |
| Workflow | Partner launches demo workspace -> runs scripted journey -> exports summary PDF. |
| UI/UX | Step-by-step guided tour with predefined checkpoints. |
| Security | Partner demo scopes restricted to assigned demo tenant. |
| Compliance | Demo export excludes any real customer identifiers. |
| APIs to be published | GET /demo/playbook, POST /demo/export |
| Dependencies (BU product, IT, other systems) | Partner enablement tooling, documentation portal |

### 8.3 Quote/Buy/Expand/Renew

This capability is bundled in HC-PC service tier and does not require standalone purchase. Expansion and renewal messaging will highlight measurable reliability outcomes from the capability.

### 8.4 Customer Enablement

Customers access capability from HC-PC workspace navigation in GLCP. Enablement includes:
- In-app onboarding checklist.
- Admin guide and quick-start runbook.
- CSM-led workshop for strategic accounts.

### 8.5 Inventory/Fleet and Subscription Management

No separate subscription object required. Capability follows HC-PC workspace entitlement and supports multi-workspace fleet views for authorized roles.

### 8.6 Consumption and Usage Reporting

Usage will be reported through:
- Active workspaces using health dashboard.
- Number of risks identified/resolved.
- Time-to-remediation for top risk categories.

### 8.7 Case Management (Support Cases)

Case ownership remains with existing HC-PC support model. The capability can prefill support context and evidence package when escalation is required.

### 8.8 Unified Health and Support Automation

Service consumes platform and HC-PC health signals, contributes normalized risk events, and supports automated recommendation generation for recurrent patterns.

### 8.9 Region Support

Phase 1: US and EU regions for HC-PC managed tenants.
Phase 2: additional regions based on telemetry and support readiness.

### 8.10 Data Governance and Privacy

- Risk events stored according to workspace data residency policy.
- No PII beyond role/account identifiers required for assignment and audit.
- Logs and evidence links follow GLCP privacy and retention standards.

### 8.11 GLCP Main Dashboard Changes

Add a health posture widget showing:
- Active high-risk items.
- Trend (7-day risk trajectory).
- Link to HC-PC risk detail view.

### 8.12 Scale Inputs

- Initial target: top 50 HC-PC customers in pilot.
- 12-month target: 400+ customer workspaces.
- Expected concurrent users: 800 peak across regions.
- Target request throughput: 120 RPS read, 20 RPS write at peak.
- Heavy platform capabilities: events ingestion, retries for transient failures, notification fan-out.

### 8.13 Integrations with Other Services

Inbound:
- HC-PC telemetry and lifecycle events.
- Platform incident and change events.

Outbound:
- Notification service (in-app/email).
- Optional ITSM connectors for context sync.

### 8.14 Special Security and Compliance Requirements

- Must support FedRAMP-ready deployment posture where HC-PC environment requires it.
- Encryption at rest and in transit mandatory.
- Role-based least privilege enforcement for remediation actions.

### 8.15 On-Prem Requirements

Primary scope is cloud-delivered HC-PC operations. For disconnected/on-prem variants, provide read-only summary mode in phase 1 and evaluate action execution support in phase 2.

### 8.16 Documentation

Documentation updates required:
- HC-PC admin guide: proactive health operations section.
- Support runbook: risk-to-case escalation flows.
- API reference for published endpoints.
- Release notes and migration notes for existing operations workflows.

## 9.0 Pivot Report: Epics per Initiative

To be inserted after Aha initiative/epic linkage is finalized.
