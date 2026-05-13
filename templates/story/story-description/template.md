# STORY NAME

A small, independently deliverable unit of work expressed from the perspective of a user or system actor.

## Format

* **Title:** {imperative phrase, e.g. "Create tenant via API"}
* **Parent Feature:** {feature-id — feature title}
* **User Story:** As a {persona}, I want to {action}, so that {benefit}
* **Context / Background:** {any additional context needed to understand the story}
* **Scope / Tasks:**
  * {task or sub-task 1}
  * {task or sub-task 2}
* **Dependencies:** {story-ids or external blockers}
* **Estimation:** {story points, e.g. 3}

### Example

* **Title:** Create tenant via API
* **Parent Feature:** F-22 — Tenant Provisioning API
* **User Story:** As a Platform Operator, I want to create a tenant via a REST API call, so that I can provision new customers without direct database access
* **Context / Background:** Currently provisioning requires a manual DB script run by the DBA team, causing delays
* **Scope / Tasks:**
  * Implement `POST /tenants` endpoint with request validation
  * Persist tenant entity with isolated namespace assignment
  * Return 201 with tenant ID and default configuration
  * Write unit and integration tests
* **Dependencies:** Auth middleware story (S-88)
* **Estimation:** 3

## Leading Questions

* Who is the primary actor and what outcome do they need?
* Is this story small enough to be completed within one sprint?
* What tasks are needed and are any of them spike-worthy?
* Which other stories or services does this depend on?
* How will a developer know when this story is done?
