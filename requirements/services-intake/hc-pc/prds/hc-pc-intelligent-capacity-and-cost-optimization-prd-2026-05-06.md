# HC-PC Intelligent Capacity and Cost Optimization (PRD)

All fields in this document are mandatory. Do not delete any questions or fields.
If a field does not apply, write N/A.

## Document Metadata

| Field | Value |
| --- | --- |
| Target release | PI-2026-Q4 (Nov 2026) |
| Epics | HC-PC Intelligent Capacity and Cost Optimization |
| Document status | Draft 06-May-2026 |
| Product Manager - GLCP (document owner) | GLCP PM - HC-PC |
| Product Manager - BU | HC-PC BU PM |

## Reviewers

| Reviewer | Date Reviewed |
| --- | --- |
| HC-PC Engineering Lead | 06-May-2026 |
| GLCP Platform Architect | 06-May-2026 |

## Approvers

| Approver | Date Approved |
| --- | --- |
| GLCP Product Director | Pending |
| HC-PC BU Product Director | Pending |

## Change Log

| Date | Author | Description |
| --- | --- | --- |
| 06-May-2026 | PM + Copilot draft | Initial sample service-intake PRD for team practice |
| 06-May-2026 | HC-PC PM | Added scale, dependency, and compliance details |

## 1. Executive Summary

This PRD defines an HC-PC capability that detects capacity inefficiencies and cost hotspots, recommends optimization actions, and provides governed execution workflows to reduce overprovisioning while maintaining reliability SLAs.

## 2. Market Trends, TAM, and HPE Opportunity (BU PM)

- Market overview for this service.
Enterprise private cloud teams increasingly demand FinOps + performance optimization with explainable recommendations.
- TAM and opportunity size for HPE.
Significant upsell opportunity exists across current HC-PC customers seeking cost governance and workload efficiency.
- What happens if we do not implement this service?
Customers continue manual optimization and may shift to alternative platforms with stronger optimization tooling.

## 3. Customer Profiles and GTM (BU PM)

- Target customer types (e.g., enterprise, SMB, MSP).
Enterprise IT operations teams, SRE teams, and managed service providers.
- GTM model (high-touch sales, partner-led, MSP, self-serve, etc.).
High-touch enterprise expansion plus partner-led adoption in MSP scenarios.

## 4. ISV Integrations (BU PM)

- Must-have ISV integrations.
ServiceNow (change and incidents), Splunk (observability export).
- Nice-to-have ISV integrations.
Datadog, Dynatrace.

## 5. Competitive Analysis and Value Proposition (BU PM)

- Competitor comparison and maturity.
Competitors provide optimization suggestions but often lack governance controls and customer-trust explainability.
- Core value proposition for this service.
HC-PC delivers actionable optimization insights with policy guardrails, auditability, and confidence scoring.

## 6. End User Personas and Workflows (BU PM and GLCP PM)

- Target personas for this service.
Platform operator, SRE lead, cloud operations manager, support engineer.
- Typical user workflows.
Review risk dashboard, inspect recommendations, run simulation, request approval, execute optimization, monitor outcome.

## 7. Service Type, Overview, and High-Level Architecture (BU PM and GLCP PM)

- Service type (IaaS, SaaS, etc.).
SaaS control-plane optimization capability for private cloud operations.
- GLCP native or non-native.
GLCP native capability integrated in HC-PC workspace.
- If service is inside a GLCP app, describe placement and ownership.
Embedded in HC-PC operations workflows; jointly owned by GLCP platform and HC-PC BU.

## 8. Platform Requirements

### 8.1 Workspace, IAM, User Management, RBAC, SLA, HA, Expected Load

#### 8.1.1 Requirement 1: IAM (link to Aha)

| Field | Details |
| --- | --- |
| Persona | Platform operator |
| Description | Restrict optimization execution to authorized roles with explicit approval flow |
| Workflow | Operator reviews recommendation then submits action request to approver |
| UI/UX | Permission-aware controls and approval prompts |
| Security | Least-privilege enforcement and token-scoped operations |
| Compliance | Full audit trail for requests, approvals, and executions |
| APIs to be published | Recommendation read API, optimization request API |
| Dependencies (BU product, IT, other systems) | IAM service, RBAC policy engine, audit logs service |

#### 8.1.2 Requirement 2: IAM (link to Aha)

| Field | Details |
| --- | --- |
| Persona | Operations manager |
| Description | Configure delegated approvers and policy thresholds per workspace |
| Workflow | Manager defines policy and delegates approval scopes |
| UI/UX | Policy configuration wizard with validation feedback |
| Security | Dual-control option for high-impact actions |
| Compliance | Policy changes are immutable and exportable |
| APIs to be published | Policy management API |
| Dependencies (BU product, IT, other systems) | IAM groups, compliance reporting systems |

### 8.2 Demo/Trial/Eval (link to Aha)

- Is there an existing or proposed demo/trial/eval plan?
Yes. A sandbox tenant will demonstrate recommendation lifecycle from detection to approved execution.

#### 8.2.1 Requirement 1: Demo (link to Aha)

| Field | Details |
| --- | --- |
| Persona | Solutions engineer |
| Description | Demonstrate optimization outcomes on synthetic fleet data |
| Workflow | Load sample telemetry, generate recommendations, simulate action, review impact |
| UI/UX | Guided demo mode with walkthrough steps |
| Security | Isolated demo tenant with non-production data |
| Compliance | Synthetic datasets only |
| APIs to be published | Demo bootstrap API |
| Dependencies (BU product, IT, other systems) | Demo tenant provisioning service |

#### 8.2.2 Requirement 2: Demo (link to Aha)

| Field | Details |
| --- | --- |
| Persona | Product specialist |
| Description | Export pre/post-optimization impact report |
| Workflow | Execute simulation and generate impact comparison report |
| UI/UX | Export action on outcome panel |
| Security | Role-gated export capability |
| Compliance | Export events logged for audit |
| APIs to be published | Impact report export API |
| Dependencies (BU product, IT, other systems) | Reporting service, storage service |

### 8.3 Quote/Buy/Expand/Renew

How is this purchased and where does this flow happen?
Packaged as HC-PC optimization add-on, surfaced in standard expansion and renewal motions.

### 8.4 Customer Enablement

How do customers start using this service?
In-product onboarding checklist, setup wizard, and operations runbook guidance.

### 8.5 Inventory/Fleet and Subscription Management

Is subscription lifecycle managed on or off platform?
On-platform through existing HC-PC subscription management.

### 8.6 Consumption and Usage Reporting

How is usage metered and reported?
By monitored clusters, recommendations evaluated, and optimization actions executed.

### 8.7 Case Management (Support Cases)

Who owns case management and where is it exposed?
HC-PC support operations through unified support workflows.

### 8.8 Unified Health and Support Automation

What inputs and automations apply to this service?
High-risk recommendations and failed executions can auto-generate alerts and optional support cases.

### 8.9 Region Support

Single region, multi-region, or global?
Multi-region rollout starting with US and EU regions.

### 8.10 Data Governance and Privacy

Describe governance, data residency, and privacy expectations.
Operational telemetry stored according to regional residency policy; no customer PII required for recommendations.

### 8.11 GLCP Main Dashboard Changes

Any dashboard updates needed for service onboarding or operations?
Add optimization impact tile and cost-risk summary tile in HC-PC main dashboard.

### 8.12 Scale Inputs

- Is this for specific customers?
Initial pilot for selected enterprise HC-PC customers.
- Progressive rollout plan.
Pilot -> limited availability -> broad availability.
- Target customers/users/devices/subscriptions and ramp prediction.
Year-1 target: 180 customers, 2,500 active users, 18,000 managed resources.
- Target requests per second.
30 RPS average, 120 RPS peak during recommendation refresh windows.
- BU scale prediction.
Expected 3x growth in recommendation evaluations over 12 months.
- Any heavily utilized platform capabilities (events, retries, etc.).
Events pipeline, policy engine checks, notification fanout, retry orchestration.

### 8.13 Integrations with Other Services

Describe inbound and outbound integrations.
Inbound telemetry from HC-PC collectors; outbound actions to orchestration APIs, reporting services, and support automation.

### 8.14 Special Security and Compliance Requirements

Document requirements beyond baseline standards.
SOC2-aligned auditability, tamper-evident logs, and approval controls for high-impact actions.

### 8.15 On-Prem Requirements

Cloud only, on-prem only, or hybrid expectations.
Hybrid model: cloud control plane orchestrates optimization over private cloud/on-prem estates.

### 8.16 Documentation

What documentation must be updated and where will it live?
HC-PC admin guide, API reference, operator runbook, and troubleshooting playbooks.

## 9.0 Pivot Report: Epics per Initiative

Create and insert a pivot report for PRD epics in this section.
N/A for initial sample draft; to be added after linked epics are finalized.
