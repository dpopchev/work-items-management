# Problem to Solution Feature

Bridges a specific user or system problem to a concrete feature design, making the rationale for scope and solution choices explicit and traceable.

## Format

### Problem

* **Affected Users:** {persona or segment}
* **Observed Behaviour / Pain:** {what users do today and why it is painful}
* **Frequency / Severity:** {how often it occurs and its impact — e.g. daily, blocks core workflow}
* **Supporting Evidence:** {user research, support tickets, analytics — {reference or link}}

### Proposed Solution

* **Solution Summary:** {1-2 sentence description of what we will build}
* **Key Design Decisions:** {why this approach over alternatives}
* **Scope:**
  * In: {what is included}
  * Out: {what is explicitly excluded}

### Value Statement

* This feature reduces {pain or cost} for {users} by {mechanism}, resulting in {expected outcome}.

### Dependencies

* {feature-id or service} — {dependency reason}

## Examples

### Example — Self-Serve Export

**Problem**
* **Affected Users:** Data analysts at enterprise accounts
* **Observed Behaviour / Pain:** Analysts email engineering to request data exports; turnaround is 2-3 days
* **Frequency / Severity:** 12 tickets/month; blocks end-of-quarter reporting for 80% of enterprise accounts
* **Supporting Evidence:** Support ticket analysis Q1 2026; analyst NPS survey (score −18 on this topic)

**Proposed Solution**
* **Solution Summary:** Add an "Export" button to all report views that triggers an async CSV/JSON generation job and emails the analyst a download link when ready
* **Key Design Decisions:** Async job chosen over sync response to handle large datasets without timeout; email delivery preferred over in-app notification based on user research
* **Scope:**
  * In: CSV and JSON export, async job with email notification, 90-day download link
  * Out: Real-time streaming, scheduled recurring exports, raw event log export

**Value Statement**
* This feature eliminates the 2-3 day wait for enterprise analysts by enabling self-serve export, expected to close 12 support tickets/month and improve analyst NPS by ≥ 20 points.

## Leading Questions

* Do we have evidence (not just assumptions) that this is a real, frequent pain for users?
* Why this solution and not an alternative — have we documented the trade-off?
* What is the minimum scope that solves the core problem without over-engineering?
* Does the value statement hold up — can we trace a clear line from feature to outcome?
* What dependencies could block delivery and how are we mitigating them?
