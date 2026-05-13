# Bug Report Story

Captures a defect in a structured, reproducible format so that developers have everything needed to diagnose, fix, and verify the resolution.

## Format

### Summary

* **Observed Behaviour:** {what actually happens}
* **Expected Behaviour:** {what should happen}
* **Severity:** {Critical / High / Medium / Low} — {brief justification}
* **Affected Version / Environment:** {version, environment, e.g. v2.4.1 / staging}

### Reproduction Steps

1. {precondition — starting state}
2. {action 1}
3. {action 2}
4. {observed result}

### Evidence

* **Logs / Error Message:** {paste or link to relevant log output or error}
* **Screenshot / Recording:** {link if applicable}
* **Trace ID / Request ID:** {identifier for distributed trace lookup}

### Impact

* **Users Affected:** {number, segment, or "all users"}
* **Frequency:** {always / intermittent — {approximate rate}}
* **Business Impact:** {consequence — e.g. blocks billing, data loss risk, SLA breach}

### Root Cause Hypothesis

* {initial hypothesis about the cause — "unknown" if not yet investigated}

### Fix Scope

* {what change is expected to resolve the issue}
* Out of scope: {related issues not included in this fix}

## Examples

### Example — Tenant API Returns 500 on Duplicate Name

**Summary**
* **Observed Behaviour:** `POST /v1/tenants` with a duplicate name returns HTTP 500 with an unhandled exception stack trace
* **Expected Behaviour:** Should return HTTP 409 Conflict with `{"error": "Tenant name must be unique"}`
* **Severity:** High — exposes internal stack trace to API consumers; violates contract
* **Affected Version / Environment:** v1.3.2 / production and staging

**Reproduction Steps**
1. Authenticate as a user with `platform:admin` scope
2. Call `POST /v1/tenants` with `{"name": "acme", "region": "eu-west"}` — returns 201
3. Call `POST /v1/tenants` again with the same payload
4. Observe 500 response with `UniqueConstraintViolation` stack trace

**Evidence**
* **Error Message:** `psycopg2.errors.UniqueViolation: duplicate key value violates unique constraint "tenants_name_key"`
* **Trace ID:** `4bf92f3577b34da6a3ce929d0e0e4736`

**Impact**
* **Users Affected:** All operators using the provisioning API
* **Frequency:** Always (100% reproducible)
* **Business Impact:** Exposes internal DB error details; violates published API contract

**Root Cause Hypothesis**
* Unique constraint violation from the DB is not caught and mapped to a 409 response in the error handler

**Fix Scope**
* Add `UniqueConstraintViolation` handling in tenant service error middleware to return 409
* Out of scope: Other duplicate-key scenarios in unrelated endpoints

## Leading Questions

* Can the bug be reproduced consistently — if intermittent, what triggers it?
* What is the actual user or business impact — is this a data loss, security, or SLA risk?
* Do we have a trace ID or log evidence that points to the failing code path?
* Is the root cause understood well enough to estimate a fix, or is a spike needed?
* Are there related endpoints or code paths that might have the same defect?
