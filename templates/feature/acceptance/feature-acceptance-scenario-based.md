# Scenario-Based Feature Acceptance

Validates a feature by specifying concrete scenarios in Given/When/Then form, covering happy paths, edge cases, and error conditions.

## Format

### Happy Path Scenarios

* **Scenario {n} — {name}:**
  * Given {precondition}
  * When {user or system action}
  * Then {expected outcome}

### Edge Cases

* **Scenario {n} — {name}:**
  * Given {boundary condition}
  * When {action}
  * Then {expected handling}

### Error & Failure Scenarios

* **Scenario {n} — {name}:**
  * Given {error condition}
  * When {action}
  * Then {error response and recovery path}

### Non-Functional Acceptance

* **Performance:** {scenario} completes within {threshold} under {load condition}
* **Security:** {access control or data isolation rule} is enforced in all scenarios
* **Accessibility:** {WCAG level} compliance verified for all new UI components

## Examples

### Example — Tenant Provisioning API

**Happy Path**
* **Scenario 1 — Create Tenant:**
  * Given a valid operator JWT with `platform:admin` scope
  * When `POST /tenants` is called with `{"name": "acme", "region": "eu-west"}`
  * Then 201 is returned with `tenant_id`, `namespace`, and `api_key`

**Edge Cases**
* **Scenario 2 — Duplicate Name:**
  * Given a tenant named "acme" already exists
  * When `POST /tenants` is called with `{"name": "acme"}`
  * Then 409 Conflict is returned with `{"error": "Tenant name must be unique"}`

**Error Scenarios**
* **Scenario 3 — Namespace Service Timeout:**
  * Given the downstream namespace service is unavailable
  * When `POST /tenants` is called
  * Then 202 Accepted is returned with a `status_url` for async polling; retry is attempted up to 3 times

**Non-Functional**
* P95 latency ≤ 200 ms for tenant creation under 50 concurrent requests
* A `viewer`-scoped JWT must receive 403 for all write operations

## Leading Questions

* Are all user-facing happy paths covered with at least one scenario each?
* What are the most likely edge cases — have we covered boundary values and duplicate states?
* What happens when a downstream dependency fails — is the degraded behaviour specified?
* Are non-functional requirements (performance, security, accessibility) testable as stated?
* Is each scenario atomic enough to be implemented as a single automated test?
