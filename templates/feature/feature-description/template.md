# FEATURE NAME

A deliverable capability that provides user or system value and maps to a parent epic.

## Format

* **Title:** {short, capability-oriented phrase, e.g. "Tenant Provisioning API"}
* **Parent Epic:** {epic-id — epic title}
* **Problem Statement:** {what user or system pain does this solve}
* **Proposed Solution:** {high-level description of the capability}
* **User Personas:** {who benefits — role or persona name}
* **Key Scenarios:** {2-4 bullet scenarios the feature enables}
* **Dependencies:** {other features, services, or stories that must precede this}
* **Estimation:** {T-shirt size or story points range, e.g. L / 13-21 pts}

### Example

* **Title:** Tenant Provisioning API
* **Parent Epic:** E-15 — Enable Multi-Tenant Support
* **Problem Statement:** Operators cannot create or configure tenants without direct database access
* **Proposed Solution:** REST API for CRUD operations on tenant entities with role-based access control
* **User Personas:** Platform Operator, Enterprise Admin
* **Key Scenarios:**
  * Operator creates a tenant and receives an isolated namespace
  * Admin updates tenant configuration via API without downtime
  * Operator deactivates a tenant and all associated resources are archived
* **Dependencies:** Auth service (F-10), Database partitioning (F-11)
* **Estimation:** L / 13-21 pts

## Leading Questions

* Which user personas are primarily affected and what is their pain today?
* What are the 2-3 most critical scenarios this feature must enable?
* What existing features or services must be in place before work can begin?
* How does this feature move the needle on the parent epic's success metrics?
* What is the rough size and do we need a spike to de-risk the estimate?
