# Hypothesis Driven Epic

Structured approach to define and manage initiatives where the focus shifts from just delivering to validating assumptions about user value.

## Format

### We Believe

* We believe doing {this initiative or capability}
* for {target users or segment}
* will achieve {change in behaviour or business direction}
* which we will know is true when we see {measurable signal in metric}

### If-Then

* If we {do this action / build this capability}
* then {those users} will {experience this benefit}
* measured by {metric and target threshold}

### Falsification Condition

* We will abandon or pivot if {counter-signal or threshold not met} after {time box or experiment}

## Examples

### Example 1 — Onboarding Friction

**We Believe**
* We believe simplifying the onboarding checklist
* for new free-tier users
* will achieve higher activation and week-1 retention
* which we will know is true when we see a 15% increase in users completing step 3 within 7 days

**If-Then**
* If we reduce onboarding steps from 8 to 4
* then new users will reach their first "aha moment" faster
* measured by time-to-first-value dropping below 5 minutes

**Falsification Condition**
* We will pivot if activation rate does not improve by ≥ 10% after 6 weeks of the new flow being live

### Example 2 — Multi-Tenant Isolation

**We Believe**
* We believe introducing tenant-level data isolation
* for enterprise customers
* will achieve higher conversion of pilot contracts to full licenses
* which we will know is true when we see 3 of 5 pilots convert within Q3

**If-Then**
* If we build a tenant provisioning API with scoped namespaces
* then enterprise admins will trust the platform with sensitive data
* measured by security audit pass rate and contract conversion rate

**Falsification Condition**
* We will stop investment if fewer than 2 pilots convert after the feature is GA for 8 weeks

## Leading Questions

* What assumption about user behaviour are we actually testing with this epic?
* Who precisely is the target user segment — can we be more specific than a broad persona?
* What is the single most important metric that would prove the hypothesis true?
* What counter-signal or result would cause us to stop or pivot?
* What is the minimum scope needed to run a valid test of the hypothesis?
