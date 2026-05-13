# User Story

The classic lightweight format expressing a unit of work from the perspective of the person who benefits, keeping the team focused on user value over technical tasks.

## Format

### Story Statement

* As a {persona or role}
* I want to {action or capability}
* So that {benefit or outcome}

### Context

* **Parent Feature:** {feature-id} — {feature title}
* **Background:** {any additional context that helps a developer understand the need}
* **Assumptions:** {things assumed to be true that the story depends on}

### Scope / Tasks

* {task 1 — implementation step}
* {task 2 — implementation step}
* {task 3 — test or validation step}

### Out of Scope

* {explicit exclusion 1}

### Estimation

* {story points or T-shirt size}

## Examples

### Example 1 — Tenant Creation

**Story Statement**
* As a Platform Operator
* I want to create a tenant via a REST API call
* So that I can provision new customers without requiring DBA access or a support ticket

**Context**
* **Parent Feature:** F-22 — Tenant Provisioning API
* **Background:** Currently provisioning requires a manual DB script run by the DBA team with a 2-3 day turnaround
* **Assumptions:** Auth middleware (S-88) is already in place and JWT validation is working

**Scope / Tasks**
* Implement `POST /v1/tenants` endpoint with request validation
* Persist tenant entity with namespace assignment via Namespace Service
* Return 201 with `tenant_id`, `namespace`, and `api_key`
* Write unit tests covering happy path and key error conditions
* Write integration test validating DB persistence and namespace assignment

**Out of Scope**
* Tenant deletion or deactivation (separate story S-106)
* Admin Portal UI (separate story S-107)

**Estimation:** 3 points

### Example 2 — Export Report

**Story Statement**
* As a Data Analyst
* I want to trigger a CSV export of any report view
* So that I can complete my quarterly analysis without waiting for engineering support

**Context**
* **Parent Feature:** F-31 — Self-Serve Data Export
* **Background:** 12 support tickets/month are raised for data exports; median turnaround is 2.5 days
* **Assumptions:** Report engine supports async job dispatch; email service is available

**Scope / Tasks**
* Add "Export CSV" button to report view toolbar
* Trigger async export job with user ID and report parameters
* Send email with download link when job completes (90-day expiry)
* Handle job failure with error email and retry option

**Out of Scope**
* JSON export format (follow-on story)
* Scheduled recurring exports

**Estimation:** 5 points

## Leading Questions

* Is the persona specific enough — would different personas need different stories here?
* Is the "so that" a genuine user benefit, or is it restating the action?
* Is this story small enough to be completed within one sprint by one developer?
* Are the tasks clear enough that a developer can start without further clarification?
* What assumptions are we making — and are they validated or at risk?
