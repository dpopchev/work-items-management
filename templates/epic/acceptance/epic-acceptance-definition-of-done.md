# Definition of Done Epic Acceptance

A structured checklist ensuring an epic meets all engineering, quality, operational, and compliance standards before it is formally closed.

## Format

### Delivery Checklist

* [ ] All child features {list IDs} are accepted and merged to main
* [ ] No open P0 or P1 defects; P2 defects triaged and scheduled
* [ ] Feature flags cleaned up or documented with removal date
* [ ] Dead code and temporary scaffolding removed

### Quality Gates

* [ ] Test coverage meets or exceeds {threshold}% across all new code paths
* [ ] Performance benchmarks validated: {metric} ≤ {threshold} under {load condition}
* [ ] Security review completed — findings at {severity} or above resolved
* [ ] Accessibility audit passed for any UI changes

### Operational Readiness

* [ ] Observability: logs, metrics, and traces instrumented for new components
* [ ] Alerts configured for {critical failure conditions}
* [ ] Runbook updated and reviewed by on-call team
* [ ] Capacity planning reviewed for production load

### Documentation & Compliance

* [ ] Architecture Decision Records (ADRs) written for significant decisions
* [ ] API documentation updated and published
* [ ] Compliance sign-off obtained from {team — e.g. Security, Legal, Privacy}
* [ ] Release notes drafted for {internal / external} audience

### Stakeholder Acceptance

* [ ] Product Owner has reviewed and signed off
* [ ] Demo conducted with key stakeholders
* [ ] Known limitations and follow-on work logged as issues

## Examples

### Example — Multi-Tenant Support Epic

* [x] F-44, F-45, F-46 accepted and merged
* [x] Zero open P0/P1; 3 P2 defects scheduled for next sprint
* [x] `enable_multi_tenant` flag removed after full rollout
* [x] Coverage at 94% across tenant service
* [x] P95 latency 187 ms under 200 concurrent tenant requests (target ≤ 300 ms)
* [x] Penetration test completed — no critical findings
* [x] Datadog dashboard created for tenant provisioning errors
* [x] Runbook published: "Tenant Isolation Incident Response"
* [x] ADR-019 written for namespace isolation approach
* [x] Security and Legal signed off for GDPR compliance
* [x] Product Owner demo completed; release notes published

## Leading Questions

* Are there any checklist items that cannot be completed — and is the risk accepted in writing?
* Have feature flags been addressed — either removed or given a documented sunset date?
* Does the on-call team feel confident supporting the new system with the runbook provided?
* Have all compliance and security reviews been completed with findings resolved?
* Have known limitations and technical debt items been logged for future sprints?
