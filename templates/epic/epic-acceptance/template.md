# EPIC ACCEPTANCE CRITERIA

Defines the conditions that must be satisfied for the epic to be considered complete and ready for release.

## Format

* **Business Outcome:** {measurable result that confirms the strategic goal is met}
* **Feature Completeness:** {all child features {feature-ids} are accepted}
* **Non-Functional Requirements:** {performance, security, compliance thresholds met}
* **Stakeholder Sign-off:** {list of roles who must approve, e.g. Product Owner, Architect}
* **Documentation:** {updated docs, runbooks, or ADRs required}
* **Rollout Gate:** {deployment, feature flag, or go-live condition}

### Example

* **Business Outcome:** 5 enterprise tenants onboarded with isolated data verified by security audit
* **Feature Completeness:** All features F-44, F-45, F-46 accepted
* **Non-Functional Requirements:** Tenant isolation confirmed via penetration test; P95 latency ≤ 300 ms
* **Stakeholder Sign-off:** Product Owner, Security Lead, Engineering Director
* **Documentation:** Multi-tenancy runbook published in Confluence
* **Rollout Gate:** Feature flag enabled for pilot tenants only

## Leading Questions

* What measurable outcome proves the strategic goal was achieved?
* Which child features must all be accepted before the epic closes?
* Are there non-functional constraints (security, performance, compliance) at the epic level?
* Who are the stakeholders required to formally sign off?
* What documentation or operational artifacts must exist before release?
