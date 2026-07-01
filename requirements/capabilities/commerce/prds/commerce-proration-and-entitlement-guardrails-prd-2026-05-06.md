# Capabilities Initiative Template (PRD)

All fields in this document are mandatory. Do not delete any questions or fields.
If a field does not apply, write N/A.

## Document Metadata

| Field | Value |
| --- | --- |
| Target release | PI-2026-Q3 (Aug 2026) |
| Epics | Commerce Self-Serve Proration Preview; Commerce Subscription Entitlement Enforcement |
| Document status | Draft 06-May-2026 |
| Product Manager (document owner) | Commerce PM - GLCP |
| Program Manager | GLCP Program Manager - Commerce Track |
| UX Designer(s) | Commerce UX Lead |
| FE/UI Dev owner | Commerce Portal FE Lead |
| BE Dev owner | Commerce Platform BE Lead |
| QA/UAT | Commerce QA Manager |
| Collaboration contacts (Storage, Compute, IT, External Vendors, etc.) | BRIM team, Tax engine team, Subscription platform team |

## Change Log

| Date | Author | Description |
| --- | --- | --- |
| 06-May-2026 | Commerce PM + Copilot | Initial sample PRD draft for team practice |
| 06-May-2026 | Commerce PM | Added KPI, scale, and RBAC detail |

## Acronyms and Terms

Define any non-obvious terms and acronyms.

- BRIM: Billing and Revenue Innovation Management stack used for rating/invoicing.
- Entitlement: Contract-based access and quota rights for purchased subscriptions.
- Proration: Partial-cycle charge adjustment when plan or quantity changes mid-cycle.
- MSP: Managed Service Provider account model.

## Problem Statement

Should be drafted by product management and reviewed/finalized with design and stakeholders.

Commerce users cannot reliably preview proration outcomes or enforce subscription entitlements consistently across UI and API workflows, resulting in billing disputes, over-consumption risk, and support escalations.

Helpful references:
- Nielsen Norman Group: Problem Statements in UX Discovery
- iSixSigma: How to Write an Effective Problem Statement

## Problem Description

- From the user perspective, what problem needs to be solved?
Subscription admins need to know pricing impact before confirming plan changes and need contract limits enforced at transaction time.
- What brought us to this change or improvement?
Repeated support incidents and finance reconciliation effort from post-facto billing corrections.
- What pain points frequently come up for users?
Unexpected invoices, unclear line-item differences, and delayed entitlement-denial explanations.
- What specific user scenarios are affected?
Mid-cycle upgrades/downgrades, add-on quantity changes, and API-driven provisioning beyond entitled limits.
- Where does the problem present itself (context, situation, digital or physical space)?
Commerce UI plan-change flow, subscription APIs, and downstream fulfillment calls.
- Why does this matter for users and for the business?
Users lose trust in commerce accuracy; business incurs revenue leakage and higher support costs.
- What is the impact on the business if we do not do this?
Higher churn risk, ongoing billing disputes, slower renewals, and compliance exposure.
- Do not define the solution here.
Confirmed. This section describes only the problem.

## History/Context

- What do we have today (if anything)?
Basic price summaries are shown, but no full proration simulation and no centralized server-side entitlement middleware across all endpoints.
- Explain for someone new to this area.
Today, UI and backend validations are not fully aligned; some checks occur late in the workflow.
- Add screenshots if available.
N/A in sample PRD.
- Add links to existing workflows or experiences.
N/A in sample PRD.
- Describe the current workflow or journey map.
Admin selects plan update, receives incomplete estimate, confirms change, and later sees invoice differences or entitlement blocks from downstream systems.

## Business Goals and Objectives

- How are we measuring success?
Reduction in billing-related support cases and increased first-pass success rate for valid plan changes.
- What are the KPIs?
1. Billing dispute ticket rate for plan-change flows.
2. Proration preview-to-confirm conversion rate.
3. Entitlement denial clarity score from support QA.
4. Entitlement check p95 latency.
- What telemetry or data should be collected?
Preview request events, confirmation events, entitlement allow/deny events, denial reasons, and downstream correction events.
- What does successful implementation look like?
Users can see clear pre-confirmation proration details and API/UI flows enforce the same entitlement decisions.
- What happens if we do not do this?
Continued support burden, revenue leakage, and trust degradation.

## Out of Scope (Non-Goals)

- What specifically are we not trying to accomplish?
Retroactive invoice re-rating for historical billing periods.
- What goals are intentionally not part of this PRD?
Global tax policy redesign and contract authoring workflow redesign.

## Account Type Considerations

- Is this capability applicable to standalone customers?
Yes.
- Is this capability applicable to MSP? If yes, explain differences from standalone.
Yes. MSP requires tenant-aware entitlement context and delegated admin visibility.
- Is this capability applicable to MSP tenants? If yes, explain differences from standalone.
Yes. Tenant-level proration preview and scoped entitlement enforcement apply with MSP parent-policy inheritance.

## On-Prem Considerations

- Is this capability applicable to Central on Prem (COP)?
N/A for current phase.
- Is this capability applicable to general on-prem?
N/A for current phase.

## Constraints to Consider

### User Constraints

- Example: limitations of what users can or cannot do.
Users without subscription-admin privileges cannot view cost deltas or execute plan changes.

### Technical Constraints

- Example: backend limitations.
Pricing and entitlement checks depend on BRIM and policy engine availability; fallback behavior must be deterministic.

### Timeline and Launch Constraints

- Note timing, PI boundaries, launch dependencies, or date constraints.
Targeting PI-2026-Q3 with phased rollout after readiness sign-off from finance and support.

## Dependencies

- Are there required dependencies?
Yes.
- Example: BRIM integration, GTS integration, Unified APIs, BU systems.
BRIM rating API, entitlement policy engine, subscription inventory APIs, audit/event pipeline, notification service.

## Implications to Be Aware Of

- What implications exist after implementation?
Support playbooks and finance reconciliation processes require updates.
- What are implications for partners and resellers?
Partners need clearer denial reasons and preview artifacts for customer communication.

## Greenfield vs Brownfield

- Is there a difference in experience for greenfield vs brownfield customers?
Yes.
- If yes, describe the differences.
Greenfield customers use new flows by default; brownfield customers require migration compatibility checks for legacy plans.

## Scale Inputs

- Is this built for specific customers?
Initially prioritized for enterprise and MSP cohorts with high subscription-change volume.
- Is a progressive rollout plan needed?
Yes. Canary 5 tenants, then 25, then broad rollout.
- Target scale: customers, users, devices, subscriptions, and ramp prediction.
Target 200 customers, 1,500 admin users, 300k subscriptions in first two quarters.
- If this capability is for a BU, include BU scale prediction.
Commerce BU predicts 2.5x increase in subscription-change events over 12 months.

## Customer Facing Audit Log Requirements

- Link to audit log guidelines.
N/A (link to be added by audit owner).
- Required user-visible audit events.
Proration preview requested, plan change confirmed, entitlement denied, entitlement override granted.

## Customer Notification Requirements

- Are notifications required for specific actions?
Yes.
- Who receives them?
Subscription admins and optional billing contacts.
- Delivery channel (in-app, email, webhook, etc.).
In-app and email in MVP; webhook as post-MVP.

## Security and Compliance Considerations

- Any special security or compliance requirements (e.g., encryption, CIS, FedRAMP).
Role-based access controls, encrypted transport/storage, immutable audit logs, and policy decision traceability.

## User Personas and Mindsets

Check all that apply and explain relevance:
- The Executives: Relevant for spend governance visibility.
- The IT Decision Makers: Relevant for policy controls and risk management.
- The VPs and Directors of Cloud: Relevant for cost optimization and standardization.
- The Technologists: Relevant for API behavior and automation.
- The Cloud Technologists: Relevant for subscription and quota operations.
- The Cloud/Datacenter Owners: Relevant for contract-bound usage governance.
- The Cloud Architects: Relevant for integration and policy design.
- The Data Practitioners: N/A.
- The Data Scientists: N/A.
- The Data Driven Developer: Relevant for API-first subscription operations.
- The Engineers: Relevant for implementation and supportability.
- The Application Owners: Relevant for add-on and plan lifecycle impacts.
- The Developers: Relevant for entitlement API integration.
- The DevOps Engineers: Relevant for automation pipeline controls.
- The Site Reliability Engineers: Relevant for reliability and fallback behavior.
- Other: Finance operations analysts (billing validation and reconciliation).

## RBAC

- Does this PRD introduce a new GLCP role?
No.
- What permission/resource granularity is needed?
Subscription-level view/preview/confirm permissions and entitlement override permission scope.
- Does this PRD introduce new GLCP permission and resource?
Yes.
- If no, list existing permissions tied to current roles.
N/A.
- If yes, complete the matrix below.

| Resource + Permission | Account Administrator | Observer | Operator | TAC Admin | CCS Admin | Application Admin |
| --- | --- | --- | --- | --- | --- | --- |
| Proration preview: view | Edit | View | View | View | View | View |
| Plan change: confirm | Edit | N/A | Edit | N/A | Edit | Edit |
| Entitlement override: grant temporary exception | Edit | N/A | N/A | Edit | Edit | N/A |

## Supportability

What should support teams be able to do for this capability?

Support teams should be able to inspect denial reason codes, replay preview calculations, and identify policy/version used for each decision.

## User Testing Research

- What research exists?
Support ticket clustering and customer interview summaries from commerce operations.
- Should additional studies be run?
Yes, moderated usability study for preview clarity and error comprehension.
- Add links to completed studies.
N/A in sample PRD.

## User Experience Designs

Add Figma links and design artifacts when available.

N/A in sample PRD.

## Requirements in Plan

Use Importance to rank features needed earlier in design and delivery.
High importance indicates MVP-level requirements.

| # | Title | Description | Importance (high/medium/low) | MVP (y/n) | Notes (UX needed, epic link) |
| --- | --- | --- | --- | --- | --- |
| 1 | Proration simulation engine integration | Compute pre-confirmation line-item deltas for supported plan-change scenarios | high | y | UX required; epic: commerce-self-serve-proration-preview.md |
| 2 | Entitlement middleware enforcement | Enforce server-side allow/deny on protected commerce API endpoints | high | y | UX minimal; epic: commerce-subscription-entitlement-enforcement.md |
| 3 | Denial reason transparency | Return structured human-readable and machine-readable denial reasons | medium | y | UX copy needed; ties to support flows |
| 4 | Webhook notifications for entitlement events | Notify external systems of denial/override decisions | low | n | Post-MVP integration track |

## FAQs

List frequently asked questions and answers for this PRD.

| Question | Answer |
| --- | --- |
| FAQ 1 | Does this change historical invoices? No, this PRD is forward-looking and does not re-rate closed billing periods. |
| FAQ 2 | Will all API clients get consistent enforcement? Yes, server-side middleware enforces policy independent of client channel. |
| FAQ 3 | Can MSP parent admins view tenant-level impacts? Yes, with delegated scope and tenant boundary controls. |
