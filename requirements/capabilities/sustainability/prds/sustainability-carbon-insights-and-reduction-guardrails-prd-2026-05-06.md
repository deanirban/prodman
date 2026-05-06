# Sustainability Carbon Insights and Reduction Guardrails (PRD)

All fields in this document are mandatory. Do not delete any questions or fields.
If a field does not apply, write N/A.

## Document Metadata

| Field | Value |
| --- | --- |
| Target release | PI-2026-Q4 (Nov 2026) |
| Epics | Sustainability Carbon Insights and Reduction Guardrails |
| Document status | Draft 06-May-2026 |
| Product Manager (document owner) | GLCP PM - Sustainability Capability |
| Program Manager | Sustainability Program Manager |
| UX Designer(s) | Sustainability UX Lead |
| FE/UI Dev owner | Sustainability UI Engineering Lead |
| BE Dev owner | Sustainability Data Services Lead |
| QA/UAT | Sustainability QA Lead |
| Collaboration contacts (Storage, Compute, IT, External Vendors, etc.) | Data Analytics, Consumption Data Services, Security, Compliance |

## Change Log

| Date | Author | Description |
| --- | --- | --- |
| 06-May-2026 | PM + Copilot draft | Initial sample capability PRD for team practice |
| 06-May-2026 | PM | Added KPI, constraints, and dependency details |

## Acronyms and Terms

- ESG: Environmental, Social, and Governance.
- Emissions Factor: Conversion value used to estimate carbon impact from energy or usage data.
- Scope 2: Indirect emissions from purchased electricity.
- Carbon Intensity: Emissions per workload unit or resource unit.

## Problem Statement

Platform users cannot consistently view, compare, and act on sustainability impact data across services. This creates low confidence in ESG reporting and limited ability to reduce carbon footprint through platform-driven actions.

## Problem Description

- From the user perspective, what problem needs to be solved?
Users need one trusted place to view sustainability metrics and understand reduction actions tied to their workloads.
- What brought us to this change or improvement?
Customer feedback indicates fragmented sustainability reporting and no guided optimization path.
- What pain points frequently come up for users?
Inconsistent metrics across services, unclear emissions assumptions, and lack of actionable recommendations.
- What specific user scenarios are affected?
Quarterly ESG reporting, architecture optimization reviews, and procurement sustainability assessments.
- Where does the problem present itself (context, situation, digital or physical space)?
GLCP dashboards and exported reports used by ops teams and sustainability stakeholders.
- Why does this matter for users and for the business?
It improves trust, supports compliance commitments, and helps customers optimize workload placement.
- What is the impact on the business if we do not do this?
Lower platform stickiness, missed ESG differentiation, and potential revenue risk in sustainability-sensitive deals.
- Do not define the solution here.
Acknowledged; this section describes only problem and impact.

## History/Context

- What do we have today (if anything)?
Basic usage and infrastructure telemetry exists, but sustainability insights are fragmented across teams.
- Explain for someone new to this area.
Current data can estimate impact, but there is no unified customer-facing sustainability capability with guardrails.
- Add screenshots if available.
N/A
- Add links to existing workflows or experiences.
N/A
- Describe the current workflow or journey map.
Users collect data manually, reconcile assumptions in spreadsheets, and report sustainability outcomes outside the platform.

## Business Goals and Objectives

- How are we measuring success?
Adoption of sustainability dashboard, recommendation usage, and reduction in high-intensity workload patterns.
- What are the KPIs?
Monthly active sustainability users, recommendation acceptance rate, and estimated avoided emissions.
- What telemetry or data should be collected?
Dashboard views, export events, recommendation interactions, policy violations, and remediation completion events.
- What does successful implementation look like?
Customers can produce credible sustainability reports and execute measurable reduction actions directly from GLCP.
- What happens if we do not do this?
Customers continue external/manual processes and perceive GLCP as weak in sustainability operations.

## Out of Scope (Non-Goals)

- What specifically are we not trying to accomplish?
Real-time market trading optimization and external carbon credit purchasing workflows.
- What goals are intentionally not part of this PRD?
Scope 1 direct emissions modeling for customer-owned non-platform facilities.

## Account Type Considerations

- Is this capability applicable to standalone customers?
Yes.
- Is this capability applicable to MSP? If yes, explain differences from standalone.
Yes; MSP needs tenant-level rollups and policy inheritance controls.
- Is this capability applicable to MSP tenants? If yes, explain differences from standalone.
Yes; tenant dashboards show scoped metrics and delegated reporting views.

## On-Prem Considerations

- Is this capability applicable to Central on Prem (COP)?
Yes, where telemetry connectors are available.
- Is this capability applicable to general on-prem?
Yes, with connector prerequisites and supported data source constraints.

## Constraints to Consider

### User Constraints

Users may not have sustainability domain expertise and need clear assumptions and guidance.

### Technical Constraints

Data quality depends on service telemetry completeness and region-specific emissions factors.

### Timeline and Launch Constraints

Target phased rollout across two increments with pilot accounts before broad availability.

## Dependencies

- Are there required dependencies?
Yes.
- Example: BRIM integration, GTS integration, Unified APIs, BU systems.
Dependencies include Data Analytics pipelines, Consumption Data Services APIs, account/tenant RBAC, and compliance export services.

## Implications to Be Aware Of

- What implications exist after implementation?
Customers may use reported sustainability data for executive and regulatory decision-making, requiring strict metric consistency.
- What are implications for partners and resellers?
Partners need delegated visibility models and report-sharing permissions.

## Greenfield vs Brownfield

- Is there a difference in experience for greenfield vs brownfield customers?
Yes.
- If yes, describe the differences.
Greenfield customers start with default baselines; brownfield customers require historical data backfill and reconciliation.

## Scale Inputs

- Is this built for specific customers?
Initial pilot for enterprise customers with active ESG programs.
- Is a progressive rollout plan needed?
Yes; pilot -> limited GA -> broad GA.
- Target scale: customers, users, devices, subscriptions, and ramp prediction.
Year-1 target: 250 customers, 3,000 active users, 20,000 monitored resources.
- If this capability is for a BU, include BU scale prediction.
Sustainability capability expected to grow 2.5x year-over-year in active reporting accounts.

## Customer Facing Audit Log Requirements

- Link to audit log guidelines.
N/A
- Required user-visible audit events.
Metric baseline changes, recommendation accept/reject events, policy updates, and report export events.

## Customer Notification Requirements

- Are notifications required for specific actions?
Yes.
- Who receives them?
Account administrators, sustainability leads, and delegated operators.
- Delivery channel (in-app, email, webhook, etc.).
In-app and email for MVP; webhook in later phase.

## Security and Compliance Considerations

- Any special security or compliance requirements (e.g., encryption, CIS, FedRAMP).
Data encryption at rest/in transit, tenant isolation, auditability, and regional data handling compliance.

## User Personas and Mindsets

Check all that apply and explain relevance:
- The Executives: Need progress and risk summaries for ESG commitments.
- The IT Decision Makers: Need cost-impact and sustainability tradeoff visibility.
- The VPs and Directors of Cloud: Need governance and optimization outcomes.
- The Technologists: Need actionable insights tied to architecture decisions.
- The Cloud Technologists: Need workload-level intensity visibility.
- The Cloud/Datacenter Owners: Need optimization levers and policy controls.
- The Cloud Architects: Need design-time and runtime sustainability guidance.
- The Data Practitioners: Need trusted metrics and exportable data.
- The Data Scientists: Need assumptions and model explainability.
- The Data Driven Developer: Need API access to sustainability metrics.
- The Engineers: Need remediation workflows and policy outcomes.
- The Application Owners: Need workload-level sustainability recommendations.
- The Developers: Need telemetry and API integration guidance.
- The DevOps Engineers: Need alerts and automation hooks.
- The Site Reliability Engineers: Need reliability-safe optimization recommendations.
- Other: Sustainability officers and compliance managers.

## RBAC

- Does this PRD introduce a new GLCP role?
No.
- What permission/resource granularity is needed?
View metrics, manage policies, export reports, and manage recommendations at account/workspace/tenant levels.
- Does this PRD introduce new GLCP permission and resource?
No new role; extends existing permissions on sustainability resources.
- If no, list existing permissions tied to current roles.
Account Administrator (full), Operator (view + apply allowed actions), Observer (view only).
- If yes, complete the matrix below.

| Resource + Permission | Account Administrator | Observer | Operator | TAC Admin | CCS Admin | Application Admin |
| --- | --- | --- | --- | --- | --- | --- |
| Sustainability dashboard view | View | View | View | View | View | N/A |
| Sustainability policy manage | Edit | N/A | Edit | Edit | Edit | N/A |
| Sustainability report export | Edit | View | Edit | Edit | Edit | N/A |
| Recommendation action apply | Edit | N/A | Edit | Edit | Edit | N/A |

## Supportability

What should support teams be able to do for this capability?
Support should inspect metric lineage, view policy decisions, replay recommendation outcomes, and troubleshoot export failures.

## User Testing Research

- What research exists?
Early interviews with sustainability-focused enterprise customers and internal pilot feedback.
- Should additional studies be run?
Yes; usability and trust calibration studies before broad rollout.
- Add links to completed studies.
N/A

## User Experience Designs

Add Figma links and design artifacts when available.
N/A

## Requirements in Plan

Use Importance to rank features needed earlier in design and delivery.
High importance indicates MVP-level requirements.

| # | Title | Description | Importance (high/medium/low) | MVP (y/n) | Notes (UX needed, epic link) |
| --- | --- | --- | --- | --- | --- |
| 1 | Sustainability dashboard baseline | Unified visibility for carbon intensity and trend metrics across workloads | high | y | UX needed; epic: Sustainability Carbon Insights and Reduction Guardrails |
| 2 | Recommendation engine | Actionable recommendations with expected impact and confidence | high | y | UX needed; dependency on analytics pipeline |
| 3 | Policy guardrails | Policy thresholds and violation handling for sustainability goals | medium | y | Requires RBAC validation |
| 4 | Reporting export | Exportable summaries for ESG and internal governance reporting | medium | y | API + UI support |

## FAQs

List frequently asked questions and answers for this PRD.

| Question | Answer |
| --- | --- |
| How are emissions estimates calculated? | Using workload telemetry with region-specific emissions factors and documented assumptions. |
| Can customers override recommendations? | Yes, with policy-aware controls and auditable actions. |
| Is this available for MSP tenants? | Yes, with scoped tenant views and delegated access. |
