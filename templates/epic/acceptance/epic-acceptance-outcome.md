# Outcome-Based Epic Acceptance

Verifies that the epic has delivered its intended business or user outcome, not just that features were shipped.

## Format

### Outcome Verification

* **Primary Metric:** {metric} has moved from {baseline} to {target} as measured by {measurement method}
* **Guard Rail Metrics:** {metric} has not degraded below {threshold}
* **Leading Indicators:** {early signal} was observed within {time box} post-launch

### Feature Completeness

* All child features {list feature IDs} have been individually accepted
* No P0 or P1 defects remain open against any child feature

### Stakeholder Sign-Off

* [ ] {Role 1} has reviewed and accepted the outcome data
* [ ] {Role 2} has confirmed business readiness
* [ ] {Role 3 — e.g. Security, Legal} has cleared any compliance requirements

### Operational Readiness

* Monitoring and alerting are in place for {key system signals}
* Runbook or incident playbook updated for {new failure modes}
* Rollback plan documented and tested

## Examples

### Example — Self-Serve Billing Epic

**Outcome Verification**
* **Primary Metric:** Self-serve subscription changes reached 68% (target: 70%) — accepted with PM approval
* **Guard Rail Metrics:** Support CSAT held at 4.4 (threshold: ≥ 4.2) ✓
* **Leading Indicators:** Portal page visits exceeded 500/week by day 10 post-launch ✓

**Feature Completeness**
* F-31, F-32, F-33 all accepted; zero open P0/P1 defects

**Stakeholder Sign-Off**
* [x] Product Owner confirmed outcome metrics
* [x] Finance confirmed invoice accuracy
* [x] Legal cleared PCI compliance requirements

**Operational Readiness**
* Billing error alerts configured in Datadog
* Incident playbook updated for failed payment webhook scenarios

## Leading Questions

* Did we actually move the primary metric — and if not, is the shortfall acceptable?
* Have all guard rail metrics held within acceptable bounds?
* Are all stakeholders who need to sign off identified and have they reviewed the data?
* Is the system operable — do we have monitoring, alerts, and a rollback plan?
* Are there any open defects or risks that should be tracked post-epic?
