# Service Initiative Template (PRD)

All fields in this document are mandatory. Do not delete any questions or fields.
If a field does not apply, write N/A.

## Document Metadata

| Field | Value |
| --- | --- |
| Target release | PI-2026-Q3 (Aug 2026) |
| Epics | HC-PC Guided Capacity Optimization |
| Document status | Draft 06-May-2026 |
| Product Manager - GLCP (document owner) | GLCP PM - HC-PC |
| Product Manager - BU | HPE Private Cloud BU PM |

## Reviewers

| Reviewer | Date Reviewed |
| --- | --- |
| HC-PC Engineering Lead | 06-May-2026 |
| GLCP Architecture | 06-May-2026 |

## Approvers

| Approver | Date Approved |
| --- | --- |
| GLCP Product Director | Pending |
| HC-PC BU Product Leader | Pending |

## Change Log

| Date | Author | Description |
| --- | --- | --- |
| 06-May-2026 | Copilot + PM Draft | Initial draft from service PRD template |
| 06-May-2026 | HC-PC PM | Added requirements and workflow details |
| 06-May-2026 | HC-PC PM | Added pilot validation detail and sync verification update |

## 1. Executive Summary

This initiative introduces guided capacity optimization for HC-PC so operators can proactively identify risk, evaluate remediation options, and execute right-sizing actions with governance and auditability.

## 2. Market Trends, TAM, and HPE Opportunity (BU PM)

- Market overview for this service.
AIOps-driven capacity optimization is becoming baseline for hybrid/private cloud operations as enterprises seek predictable performance with lower overprovisioning.
- TAM and opportunity size for HPE.
Capacity efficiency and proactive operations represent a large expansion opportunity across installed HC-PC enterprise accounts where operational savings and SLA improvements are measurable.
- What happens if we do not implement this service?
Customers continue with reactive capacity operations, increasing SLA risk, support burden, and potential churn versus competitors with proactive optimization.

## 3. Customer Profiles and GTM (BU PM)

- Target customer types (e.g., enterprise, SMB, MSP).
Enterprise IT operators, platform SRE teams, and managed private cloud admins.
- GTM model (high-touch sales, partner-led, MSP, self-serve, etc.).
High-touch enterprise and partner-led expansion within existing HC-PC subscriptions.

## 4. ISV Integrations (BU PM)

- Must-have ISV integrations.
ServiceNow ITSM (incident/change), Splunk observability export.
- Nice-to-have ISV integrations.
Datadog and Dynatrace signal enrichment.

## 5. Competitive Analysis and Value Proposition (BU PM)

- Competitor comparison and maturity.
Major competitors provide proactive recommendations but often lack transparent rationale and platform-native governance controls for private cloud execution.
- Core value proposition for this service.
HC-PC delivers explainable recommendations, built-in approval controls, and closed-loop outcome tracking in one native operator workflow.

## 6. End User Personas and Workflows (BU PM and GLCP PM)

- Target personas for this service.
Platform operator, SRE lead, operations manager, and support engineer.
- Typical user workflows.
Review risk dashboard, inspect recommendations, run simulation, approve change, apply remediation, monitor outcomes.

## 7. Service Type, Overview, and High-Level Architecture (BU PM and GLCP PM)

- Service type (IaaS, SaaS, etc.).
SaaS control-plane capability for private cloud operations.
- GLCP native or non-native.
GLCP native extension integrated into HC-PC workspace experiences.
- If service is inside a GLCP app, describe placement and ownership.
Feature is embedded in HC-PC operations area; owned jointly by HC-PC BU and GLCP platform teams.

## 8. Platform Requirements

### 8.1 Workspace, IAM, User Management, RBAC, SLA, HA, Expected Load

#### 8.1.1 Requirement 1: IAM (link to Aha)

| Field | Details |
| --- | --- |
| Persona | Platform operator |
| Description | Enforce role-based permissions for viewing recommendations and executing remediation actions |
| Workflow | Operator reviews recommendations; approver role authorizes high-impact actions |
| UI/UX | Permission-gated controls with approval prompts and audit breadcrumbs |
| Security | Least privilege, scoped tokens, and session-bound authorization checks |
| Compliance | Full activity logging and retention aligned with enterprise policy |
| APIs to be published | Recommendation access API and remediation approval API |
| Dependencies (BU product, IT, other systems) | GLCP IAM, policy engine, audit pipeline |

#### 8.1.2 Requirement 2: IAM (link to Aha)

| Field | Details |
| --- | --- |
| Persona | Operations manager |
| Description | Delegate approval authority by workspace and cluster scope |
| Workflow | Manager configures delegated approvers and policy thresholds |
| UI/UX | Policy configuration panel with validation and preview |
| Security | Immutable policy history with dual-control option |
| Compliance | Change records exportable for audits |
| APIs to be published | Approval policy management API |
| Dependencies (BU product, IT, other systems) | IAM groups, compliance reporting service |

### 8.2 Demo/Trial/Eval (link to Aha)

- Is there an existing or proposed demo/trial/eval plan?
Yes. A guided sandbox flow will demonstrate recommendation generation, simulation, and approval workflow on synthetic fleet data.

#### 8.2.1 Requirement 1: Demo (link to Aha)

| Field | Details |
| --- | --- |
| Persona | Solutions engineer |
| Description | Launch demo tenant with pre-seeded telemetry and suggested actions |
| Workflow | Provision demo workspace, execute sample recommendation, show outcome tracking |
| UI/UX | Demo mode banner and step-by-step walkthrough |
| Security | Demo tenant isolated from production data |
| Compliance | Demo data set is synthetic and non-customer |
| APIs to be published | Demo bootstrap API |
| Dependencies (BU product, IT, other systems) | Demo tenant provisioning service |

#### 8.2.2 Requirement 2: Demo (link to Aha)

| Field | Details |
| --- | --- |
| Persona | Product specialist |
| Description | Export pre/post remediation reports for customer review |
| Workflow | Execute simulation, apply mock remediation, export comparative report |
| UI/UX | One-click export from outcome panel |
| Security | Export controlled by RBAC |
| Compliance | Audit event generated for report export |
| APIs to be published | Report export API |
| Dependencies (BU product, IT, other systems) | Reporting service, object storage |

### 8.3 Quote/Buy/Expand/Renew

How is this purchased and where does this flow happen?
Packaged as an HC-PC add-on capability and surfaced in standard renewal/expansion motions.

### 8.4 Customer Enablement

How do customers start using this service?
Enablement through in-product onboarding checklist, guided tutorial, and operations playbook.

### 8.5 Inventory/Fleet and Subscription Management

Is subscription lifecycle managed on or off platform?
On platform through existing HC-PC subscription management controls.

### 8.6 Consumption and Usage Reporting

How is usage metered and reported?
Usage metered by monitored clusters, recommendation evaluations, and executed remediations with monthly reporting.

### 8.7 Case Management (Support Cases)

Who owns case management and where is it exposed?
Support ownership remains with HC-PC operations support through unified support workflow.

### 8.8 Unified Health and Support Automation

What inputs and automations apply to this service?
Capacity risk breaches and failed remediation attempts trigger automated alerts and optional case creation.

### 8.9 Region Support

Single region, multi-region, or global?
Multi-region with phased rollout starting in US and EU regions.

### 8.10 Data Governance and Privacy

Describe governance, data residency, and privacy expectations.
Operational telemetry stored per regional residency policy; no PII required for recommendation logic.

### 8.11 GLCP Main Dashboard Changes

Any dashboard updates needed for service onboarding or operations?
Add capacity risk summary tile and remediation outcomes widget on HC-PC dashboard.

### 8.12 Scale Inputs

- Is this for specific customers?
Initial wave targets enterprise HC-PC tenants with larger cluster fleets.
- Progressive rollout plan.
Canary in 5 tenants, then 20, then broad availability.
- Target customers/users/devices/subscriptions and ramp prediction.
Target 150 tenants and 2,000 clusters in first two quarters.
- Target requests per second.
20 RPS average with 80 RPS peak during recommendation refresh windows.
- BU scale prediction.
Expected 3x growth in managed clusters within 12 months.
- Any heavily utilized platform capabilities (events, retries, etc.).
High utilization expected for events, notification fanout, and retry pipelines.

### 8.13 Integrations with Other Services

Describe inbound and outbound integrations.
Inbound telemetry from HC-PC collectors; outbound actions to orchestration engines, support automation, and reporting.

### 8.14 Special Security and Compliance Requirements

Document requirements beyond baseline standards.
SOC2 auditability, approval controls for high-impact actions, and tamper-evident audit logs.

### 8.15 On-Prem Requirements

Cloud only, on-prem only, or hybrid expectations.
Hybrid operational model: cloud control plane managing private cloud/on-prem environments.

### 8.16 Documentation

What documentation must be updated and where will it live?
Update HC-PC admin guide, API docs, and operations runbook in developer portal and customer docs center.

## 9.0 Pivot Report: Epics per Initiative

Create and insert a pivot report for PRD epics in this section.
N/A for initial draft; to be added after epics are linked in Aha.
