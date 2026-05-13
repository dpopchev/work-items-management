# STORY ACCEPTANCE CRITERIA

Defines the precise, testable conditions a story must satisfy before it can be marked done.

## Format

* **Scenario {n}:** Given {precondition}, when {action}, then {expected outcome}
* **Edge Case:** {boundary or failure condition and expected behaviour}
* **Data Validation:** {input constraints or field rules that must be enforced}
* **Negative Test:** {what must NOT happen under {condition}}
* **Definition of Done Checklist:**
  * [ ] Code reviewed and approved
  * [ ] Tests written and passing
  * [ ] No new linting or type errors
  * [ ] Relevant docs or comments updated

### Example

* **Scenario 1:** Given a valid operator JWT, when `POST /tenants` is called with `{"name": "acme"}`, then a 201 response is returned containing a unique `tenant_id` and `namespace`
* **Scenario 2:** Given the tenant name "acme" already exists, when `POST /tenants` is called again with the same name, then a 409 Conflict is returned
* **Edge Case:** Tenant name with special characters returns 422 with message "Name must be alphanumeric"
* **Data Validation:** `name` field is required, 3-64 chars, alphanumeric and hyphens only
* **Negative Test:** A user with `viewer` role must not be able to create a tenant; expect 403
* **Definition of Done Checklist:**
  * [ ] Code reviewed and approved
  * [ ] Unit tests cover happy path and all listed scenarios
  * [ ] Integration test validates DB persistence
  * [ ] No new linting or type errors
  * [ ] OpenAPI spec updated

## Leading Questions

* What is the exact happy-path scenario in Given/When/Then form?
* What edge cases or boundary conditions are in scope for this story?
* What input validation rules must be enforced?
* What must explicitly NOT happen (negative scenarios)?
* Is the Definition of Done checklist complete for this story's context?
