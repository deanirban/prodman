# Commerce Self-Serve Proration Preview

**Problem Statement:**

Customers and sales admins cannot preview proration impact before making plan changes, leading to billing surprises and support escalations.

**Context **(optional)**:**

- Business objective: Reduce billing confusion and support volume during subscription changes.
- Previous work done: Existing quote/plan-change flows show final totals only after submission.
- PRD link: N/A

**Goal:**

As a subscription admin, I want to preview prorated charges before confirming plan changes, so that I can make informed billing decisions.

- Targeted User Persona: Subscription admin, finance operations analyst.
- Benefit, Value to customer: Billing transparency and fewer corrective support cases.

**Workflows (User and System Interactions):**

- Admin selects plan change in commerce UI.
- System computes projected proration for current cycle.
- Admin reviews line-item breakdown and confirms or cancels change.
- System records acceptance and finalizes chosen action.

**Functional Requirements:**

- Compute proration preview for upgrade, downgrade, and mid-cycle add-on scenarios.
- Show line-item delta, tax estimate, and effective-date assumptions.
- Provide API response parity with UI preview values.
- Store audit trail for preview and confirmation events.

**Acceptance Criteria:**

- Positive functional scenarios: Preview is shown before confirmation for supported changes.
- Negative functional scenarios: Invalid plan transitions return actionable validation errors.
- Out of Scope functional scenarios: Multi-currency reconciliation adjustments.
- Monitoring/Observability: Metrics for preview requests, errors, and conversion to confirm.
- Security Audit Complete: No critical security findings for feature scope.
- ATA status: No Critical/High gaps; Medium/Low mitigations tracked.
- Pen Test Criteria: No CAT1 findings.
- Compliance Audit complete: Required audit events are retained.

**Dependencies:**

- Internal within GLP services: Commerce rating service, tax service, subscription policy engine.
- External on BUs: Finance reporting export integration.
