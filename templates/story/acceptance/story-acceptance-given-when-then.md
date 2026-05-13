# Given-When-Then Story Acceptance

Specifies story acceptance using the Gherkin-style Given/When/Then format, producing scenarios that map directly to automated tests.

## Format

### Scenario {n} — {scenario name}

* **Given** {precondition or system state}
* **And** {additional precondition if needed}
* **When** {user action or system event}
* **Then** {expected outcome}
* **And** {additional assertion if needed}

### Edge Case Scenarios

* **Scenario {n} — {edge case name}:**
  * Given {boundary condition}
  * When {action}
  * Then {expected handling}

### Definition of Done

* [ ] All scenarios above pass as automated tests
* [ ] Code reviewed and approved
* [ ] No new linting or type errors
* [ ] Relevant documentation updated

## Examples

### Example — Create Tenant Story

**Scenario 1 — Successful tenant creation**
* Given I am authenticated with a JWT bearing `platform:admin` scope
* When I call `POST /v1/tenants` with `{"name": "acme", "region": "eu-west"}`
* Then the response status is 201
* And the response body contains `tenant_id`, `namespace`, and `api_key`
* And a tenant record with name "acme" exists in the database scoped to "eu-west"

**Scenario 2 — Duplicate tenant name**
* Given a tenant named "acme" already exists
* When I call `POST /v1/tenants` with `{"name": "acme"}`
* Then the response status is 409
* And the response body contains `{"error": "Tenant name must be unique"}`

**Scenario 3 — Missing required field**
* Given I am authenticated with `platform:admin` scope
* When I call `POST /v1/tenants` with `{"region": "eu-west"}` (no name)
* Then the response status is 400
* And the response body contains a validation error referencing the `name` field

**Scenario 4 — Insufficient permissions**
* Given I am authenticated with a JWT bearing `platform:viewer` scope
* When I call `POST /v1/tenants` with a valid payload
* Then the response status is 403

**Definition of Done**
* [x] All 4 scenarios implemented as integration tests and passing
* [x] Code reviewed by 2 engineers
* [x] No linting errors
* [x] OpenAPI spec updated to reflect 409 response

## Leading Questions

* Does each scenario map to exactly one test case — is it atomic?
* Have we covered the most important error conditions, not just the happy path?
* Are the "Then" statements specific enough to be asserted in code without ambiguity?
* Are there boundary values (min/max lengths, empty inputs) that need their own scenarios?
* Can all scenarios be automated, or are any manual-only — and is that acceptable?
