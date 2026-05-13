# Outcome Oriented Epic

Frames an initiative around the business or user outcome it must achieve rather than a list of features to ship, keeping teams focused on value over output.

## Format

### Desired Outcome

* **Who:** {user segment or stakeholder}
* **Current State:** {what they experience or can do today}
* **Target State:** {what they should experience or be able to do after the epic}
* **Business Value:** {why this outcome matters to the organisation}

### Success Metrics

* **Primary Metric:** {metric name} moves from {baseline} to {target} by {date}
* **Guard Rail Metric:** {metric that must not degrade} stays above/below {threshold}
* **Leading Indicator:** {early signal} observed within {time box}

### Scope Boundary

* **In Scope:** {capabilities or areas included}
* **Out of Scope:** {explicit exclusions}
* **Dependencies:** {upstream epics, teams, or systems — {id or name}}

## Examples

### Example 1 — Self-Serve Billing

**Desired Outcome**
* **Who:** SMB customers on a paid plan
* **Current State:** Must contact support to upgrade, downgrade, or update payment method
* **Target State:** Can manage their entire subscription lifecycle without contacting support
* **Business Value:** Reduces support ticket volume by ~30% and increases upgrade conversion

**Success Metrics**
* **Primary Metric:** Self-serve subscription changes rise from 10% to 70% of all changes by Q3
* **Guard Rail Metric:** Support CSAT does not drop below 4.2
* **Leading Indicator:** Portal page visits ≥ 500/week within first 2 weeks of launch

**Scope Boundary**
* **In Scope:** Plan upgrade/downgrade, payment method update, invoice download
* **Out of Scope:** Custom enterprise contracts, usage-based billing overrides
* **Dependencies:** Stripe integration (E-09), Auth epic (E-12)

## Leading Questions

* What does success look like for the user — not what we ship, but what they can do differently?
* What is the single primary metric that best captures the desired outcome?
* What must not get worse as a result of this epic (guard rail metrics)?
* What is explicitly out of scope to prevent the epic from expanding?
* How does achieving this outcome connect to a company-level OKR or strategic goal?
