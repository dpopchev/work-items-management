# Problem Statement Epic

Anchors an initiative in a clearly articulated problem experienced by users or the business, ensuring alignment on why before discussing what.

## Format

### Problem Definition

* **Affected Users:** {who experiences the problem — persona or segment}
* **Context:** {when or where does the problem occur}
* **Problem:** {what goes wrong or is missing}
* **Impact:** {quantified or qualified consequence for user and business}
* **Root Cause (if known):** {underlying reason the problem exists}

### Vision Statement

* In {time horizon}, {affected users} will be able to {desired capability or experience} without {current friction or obstacle}.

### Constraints

* **Budget / Capacity:** {team or resource constraint}
* **Regulatory / Compliance:** {any legal or policy constraint}
* **Technical Constraints:** {platform, legacy, or architecture limits}

### Out of Scope

* {explicit non-goal 1}
* {explicit non-goal 2}

## Examples

### Example 1 — Data Export

**Problem Definition**
* **Affected Users:** Data analysts at enterprise accounts
* **Context:** End of reporting cycle, monthly and quarterly
* **Problem:** Cannot export aggregated reports in machine-readable formats without engineering help
* **Impact:** 4-6 hours of analyst time lost per report cycle; 12 support tickets/month; analyst NPS −18
* **Root Cause:** Export functionality was scoped out of the MVP and never revisited

**Vision Statement**
* By Q4 2026, data analysts will be able to self-serve CSV and JSON exports of any report view without raising a support ticket.

**Constraints**
* **Budget / Capacity:** 1 team, 2 sprints max for initial delivery
* **Regulatory / Compliance:** GDPR — exported data must be scoped to the user's own tenant
* **Technical Constraints:** Report engine does not support streaming; must use async job pattern

**Out of Scope**
* Real-time streaming export
* Export of raw event logs

## Leading Questions

* Can we quantify the impact — what does this problem cost users or the business today?
* Do we understand the root cause well enough, or do we need discovery first?
* Who are the specific users affected — have we talked to them recently?
* What constraints (technical, regulatory, capacity) will shape the solution?
* How will we know the problem is solved — what does the user experience look like after?
