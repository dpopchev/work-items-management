# Demo Script Story Acceptance

Structures acceptance as a step-by-step walkthrough a developer or QA engineer performs to demonstrate the story is complete — useful for UI features and workflows that are hard to fully automate.

## Format

### Pre-Demo Setup

* **Environment:** {staging / UAT / local with seed data}
* **Test Data Required:** {specific accounts, records, or state needed}
* **Credentials:** {role and account to use for demo}

### Demo Steps

* **Step {n} — {action name}:**
  * Action: {what to do}
  * Expected Result: {what should be visible or returned}
  * Pass Criteria: {specific assertion — e.g. "Button is disabled", "Toast reads X", "Record exists in DB"}

### Rollback / Cleanup

* {steps to restore test environment to its original state after demo}

### Sign-Off

* [ ] Developer self-tested and all steps pass
* [ ] Product Owner or QA witnessed demo and accepted
* [ ] Test environment cleaned up

## Examples

### Example — Tenant Creation UI (Admin Portal)

**Pre-Demo Setup**
* **Environment:** Staging
* **Test Data Required:** No existing tenant named "demo-acme"
* **Credentials:** `operator-test@example.com` with `platform:admin` role

**Demo Steps**

* **Step 1 — Navigate to Tenants:**
  * Action: Log in and click "Tenants" in the left sidebar
  * Expected Result: Tenants list page loads with existing tenants visible
  * Pass Criteria: Page title reads "Tenants" and list renders within 1 second

* **Step 2 — Open New Tenant Form:**
  * Action: Click "+ New Tenant" button
  * Expected Result: Modal dialog opens with Name and Region fields
  * Pass Criteria: Modal visible; both fields empty; "Create" button disabled

* **Step 3 — Submit Valid Tenant:**
  * Action: Enter name `demo-acme`, select region `EU West`, click "Create"
  * Expected Result: Modal closes; success toast appears; new row visible in list
  * Pass Criteria: Toast reads "Tenant demo-acme created successfully"; row shows name, region, status "Active"

* **Step 4 — Attempt Duplicate Name:**
  * Action: Open form again, enter `demo-acme`, click "Create"
  * Expected Result: Inline error shown on name field
  * Pass Criteria: Error message reads "Tenant name must be unique"; form stays open

* **Step 5 — Verify API Key:**
  * Action: Click on `demo-acme` row; navigate to "Credentials" tab
  * Expected Result: API key displayed (masked) with "Copy" and "Rotate" actions
  * Pass Criteria: Key is present and masked by default; Copy button copies to clipboard

**Rollback / Cleanup**
* Delete `demo-acme` tenant via `DELETE /v1/tenants/{id}` after demo

**Sign-Off**
* [ ] Developer self-tested — all 5 steps pass
* [ ] Product Owner witnessed and accepted
* [ ] `demo-acme` tenant deleted from staging

## Leading Questions

* Is the test data setup clearly defined — can someone other than the developer run this demo?
* Does each step have a specific, unambiguous pass criterion — not just "looks correct"?
* Are failure scenarios included in the demo, not just the happy path?
* Is the cleanup procedure complete — will the environment be stable for the next demo?
* Does the Product Owner need to witness this, or can developer self-sign-off suffice?
