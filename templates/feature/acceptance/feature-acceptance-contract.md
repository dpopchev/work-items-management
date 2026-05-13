# Contract-Based Feature Acceptance

Verifies a feature by asserting the interface contract it must uphold — inputs, outputs, error codes, schemas, and SLOs — making it ideal for API or platform features.

## Format

### Interface Contract

* **Endpoint / Interface:** {method and path, event name, or UI component}
* **Request Schema:** {required and optional fields with types and constraints}
* **Response Schema:** {fields returned on success with types}
* **Status Codes:**
  * `{code}` — {condition that produces it}
* **Headers / Auth:** {required headers and token scopes}

### SLO Acceptance

* **Latency:** P{percentile} ≤ {threshold} ms under {load condition}
* **Availability:** ≥ {percentage}% measured over {window}
* **Error Rate:** ≤ {percentage}% of requests return 5xx under normal load

### Backwards Compatibility

* {existing consumer} must continue to function without changes after this feature ships
* No fields removed or types changed in {existing schema or version}

### Security Contract

* {role or scope} can {action} — expect {status code}
* {role or scope} cannot {action} — expect {status code}
* {sensitive data field} is {encrypted / masked / excluded} in all responses

## Examples

### Example — Tenant Provisioning API Contract

**Interface Contract**
* **Endpoint:** `POST /v1/tenants`
* **Request Schema:** `name` (string, required, 3–64 chars, `[a-z0-9-]`), `region` (enum: `eu-west | us-east`, required), `plan_tier` (enum: `starter | enterprise`, optional, default `starter`)
* **Response Schema (201):** `tenant_id` (uuid), `namespace` (string), `api_key` (string), `created_at` (ISO 8601)
* **Status Codes:**
  * `201` — tenant created successfully
  * `400` — missing required field
  * `409` — tenant name already exists
  * `422` — field validation failure (invalid chars, length)
  * `403` — insufficient scope
  * `503` — namespace service unavailable (with retry-after header)
* **Headers:** `Authorization: Bearer <JWT>` with scope `platform:admin`

**SLO Acceptance**
* P95 ≤ 200 ms under 50 concurrent requests
* ≥ 99.9% availability over 30-day rolling window
* ≤ 0.1% 5xx rate under normal load

**Backwards Compatibility**
* `GET /v1/tenants` response schema must remain unchanged

**Security Contract**
* `platform:admin` scope: full CRUD — expect 2xx
* `platform:viewer` scope: write operations — expect 403
* `api_key` field is masked after initial creation (shown once only)

## Leading Questions

* Is the request schema fully specified including all constraints and defaults?
* Are all meaningful status codes defined including 4xx and 5xx variants?
* Are the SLO targets realistic and have they been validated against load test results?
* Does this feature change any existing interface — and are backwards compatibility guarantees explicit?
* Are all security assertions covering both positive (allowed) and negative (denied) cases?
