# Capability Definition Feature

Defines a feature in terms of the new system capability it introduces, its interfaces, and the constraints it must satisfy — useful for platform or API-facing features.

## Format

### Capability Summary

* **Parent Epic:** {epic-id} — {epic title}
* **Capability Name:** {short name, e.g. "Tenant Provisioning API"}
* **Capability Type:** {API / UI / Background Process / Integration / Configuration}
* **Consumers:** {who or what uses this capability — persona, service, or system}

### Interface Definition

* **Inputs:** {parameters, events, or user actions that trigger the capability}
* **Outputs:** {data returned, side effects, or state changes produced}
* **Contract:** {API schema reference, event schema, or UI wireframe link}
* **SLO / SLA:** {availability, latency, or throughput target}

### Constraints

* **Security:** {authentication, authorisation, or data sensitivity requirements}
* **Performance:** {latency, throughput, or resource limits}
* **Compliance:** {regulatory or policy constraints, e.g. GDPR, SOC 2}
* **Backwards Compatibility:** {must not break {consumers} using {version or contract}}

### Dependencies

* {feature-id or service} — {reason it is required}

## Examples

### Example — Tenant Provisioning API

**Capability Summary**
* **Parent Epic:** E-15 — Multi-Tenant Support
* **Capability Name:** Tenant Provisioning API
* **Capability Type:** API
* **Consumers:** Platform Operators via Admin Portal; internal Namespace Service

**Interface Definition**
* **Inputs:** `POST /tenants` with `{name, region, plan_tier}`; operator JWT in Authorization header
* **Outputs:** 201 with `{tenant_id, namespace, api_key}`; async provisioning status via `GET /tenants/{id}/status`
* **Contract:** OpenAPI spec v2.3 — `/docs/api/tenants.yaml`
* **SLO / SLA:** P95 latency ≤ 200 ms; 99.9% availability

**Constraints**
* **Security:** JWT must carry `platform:admin` scope; tenant data scoped to namespace
* **Performance:** Must handle 50 concurrent provisioning requests without degradation
* **Compliance:** Tenant metadata stored in EU region only; GDPR Article 25 by design
* **Backwards Compatibility:** Must not change response schema for existing `GET /tenants` consumers

**Dependencies**
* F-10 — Auth middleware (JWT validation must be in place)
* Namespace Service v2.1 (supports scoped namespace creation)

## Leading Questions

* Who are the consumers of this capability — internal services, external APIs, or end users?
* What is the contract: is there an existing schema or do we need to design one?
* What are the non-negotiable performance or availability targets?
* What backwards compatibility guarantees must be maintained?
* What security and compliance constraints apply to the data this capability handles?
