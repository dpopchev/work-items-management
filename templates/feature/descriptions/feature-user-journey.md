# User Journey Feature

Describes a feature by mapping the end-to-end experience a user goes through, ensuring the team understands the full context before designing individual stories.

## Format

### Context

* **Parent Epic:** {epic-id} — {epic title}
* **Primary Persona:** {role or persona name}
* **Entry Point:** {where / how the user arrives at this feature}
* **Exit Point:** {what the user has achieved when the journey is complete}

### Journey Steps

* **Step {n} — {step name}:** {user action or system response}
  * Happy path: {expected outcome}
  * Failure / edge case: {what can go wrong and how it is handled}

### Jobs To Be Done

* When {situation}, I want to {motivation}, so I can {expected outcome}.

### Acceptance Summary

* {one-line statement of what done looks like for the full journey}

## Examples

### Example — Tenant Provisioning Journey

**Context**
* **Parent Epic:** E-15 — Multi-Tenant Support
* **Primary Persona:** Platform Operator
* **Entry Point:** Operator lands on Admin Portal → Tenants page
* **Exit Point:** New tenant is active and operator has received credentials

**Journey Steps**
* **Step 1 — Initiate:** Operator clicks "New Tenant" and fills in name and region
  * Happy path: Form validates and pre-flight checks pass
  * Failure: Name already exists → inline error "Tenant name must be unique"
* **Step 2 — Confirm:** Operator reviews summary and submits
  * Happy path: System creates tenant, assigns namespace, returns tenant ID
  * Failure: Downstream namespace service timeout → async retry with status page
* **Step 3 — Activate:** Operator copies API key and shares with customer admin
  * Happy path: Key is scoped to tenant namespace and rotatable
  * Failure: Key generation fails → error banner with retry CTA

**Jobs To Be Done**
* When I need to onboard a new enterprise customer, I want to provision a tenant in under 2 minutes, so I can start the customer's trial without waiting for DBA intervention.

**Acceptance Summary**
* An operator can create, review, and activate a tenant end-to-end without leaving the Admin Portal or raising a support ticket.

## Leading Questions

* Where exactly does the user start this journey — what triggers their need?
* What are the 2-3 most likely failure modes and how should the system respond?
* Is the journey completable end-to-end by one persona, or does it hand off to another?
* What would make this journey feel slow, confusing, or broken to the user?
* Are all journey steps covered by at least one story in the backlog?
