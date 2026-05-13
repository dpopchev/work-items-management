# Checklist Story Acceptance

A concise pass/fail checklist format for stories where scenario-based acceptance would be over-specified — ideal for refactoring, infrastructure, and enablement stories.

## Format

### Functional Checks

* [ ] {observable behaviour 1 is working as expected}
* [ ] {observable behaviour 2 is working as expected}
* [ ] {edge case or error condition is handled correctly}

### Code Quality Checks

* [ ] Code reviewed and approved by {number} reviewer(s)
* [ ] Test coverage ≥ {threshold}% for new/changed code
* [ ] No new linting, type, or static analysis errors
* [ ] No unresolved TODOs or FIXMEs

### Integration Checks

* [ ] Passes all existing tests in CI without regression
* [ ] Deployed to staging and manually smoke tested
* [ ] Dependent services or consumers verified unaffected

### Documentation Checks

* [ ] Inline comments updated where logic is non-obvious
* [ ] CHANGELOG or release notes entry added
* [ ] {runbook / API doc / wiki} updated if applicable

### Performance / Operational Checks

* [ ] {metric or benchmark} meets {threshold} as verified by {method}
* [ ] No new N+1 queries or unnecessary allocations introduced

## Examples

### Example — Add `tenant_id` DB Migration

**Functional Checks**
* [x] `tenant_id` column exists on `users`, `resources`, and `events` tables
* [x] All existing rows backfilled with `DEFAULT_TENANT_ID`
* [x] Composite index `(tenant_id, created_at)` created on each table
* [x] ORM query layer always scopes by `tenant_id`

**Code Quality**
* [x] Reviewed by 2 engineers
* [x] 100% of migration script paths covered by test rollback scenario
* [x] No linting errors

**Integration**
* [x] All 148 existing API tests pass post-migration in CI
* [x] Staged on a production-size snapshot; migration completed in 3 min 42 sec
* [x] Rollback script verified — data integrity confirmed

**Documentation**
* [x] DB schema doc updated
* [x] CHANGELOG entry: "Add tenant_id partitioning to core tables"

**Performance / Operational**
* [x] Query latency for tenant-scoped reads improved by 40% on staging benchmark
* [x] No full-table scans detected in EXPLAIN ANALYZE output

## Leading Questions

* Is every check independently verifiable by someone other than the author?
* Are there functional checks missing that a reviewer would expect to see?
* Has the change been tested on data that resembles production volume?
* Are there downstream consumers or dependent tests that need to be re-verified?
* Is the documentation complete enough that a new team member could understand the change?
