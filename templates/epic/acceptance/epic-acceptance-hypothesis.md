# Hypothesis Validation Epic Acceptance

Verifies that the epic has produced enough evidence to confirm, refute, or refine the original hypothesis before further investment.

## Format

### Hypothesis Verdict

* **Original Hypothesis:** {restate the We Believe / If-Then statement from the description}
* **Verdict:** {Confirmed / Refuted / Inconclusive — needs extension}
* **Evidence:** {data points, metric readings, qualitative signals that support the verdict}
* **Confidence Level:** {High / Medium / Low} — {brief rationale}

### Metric Results

* **Primary Signal:** {metric} result was {value} vs target {value} → {Pass / Fail / Partial}
* **Falsification Condition:** {was the stop condition triggered? Yes / No}
* **Unexpected Findings:** {any signal not anticipated that changes understanding}

### Next Step Recommendation

* [ ] Confirmed → proceed to full build / next epic {epic-id}
* [ ] Refuted → stop investment, document learnings in {location}
* [ ] Inconclusive → extend experiment by {time box} with {adjustment}

### Stakeholder Sign-Off

* [ ] Product Owner accepts verdict and approves next step
* [ ] Engineering Lead confirms technical findings are accurate
* [ ] Data/Analytics confirms measurement methodology was sound

## Examples

### Example — Onboarding Simplification Hypothesis

**Hypothesis Verdict**
* **Original Hypothesis:** Reducing onboarding steps from 8 to 4 will increase activation by 15%
* **Verdict:** Confirmed
* **Evidence:** Activation rate increased from 34% to 51% over 6-week measurement window (n = 4,200 users)
* **Confidence Level:** High — sample size sufficient, no confounding campaigns ran during period

**Metric Results**
* **Primary Signal:** Activation rate 51% vs target 49% (baseline + 15%) → Pass
* **Falsification Condition:** Not triggered (threshold was < 10% improvement) ✓
* **Unexpected Findings:** Step 2 drop-off eliminated entirely — email verification was the main friction point

**Next Step Recommendation**
* [x] Confirmed → proceed to full rollout epic E-22 (remove feature flag)

## Leading Questions

* Is the evidence sufficient to make a confident decision, or do we need more data?
* Were there confounding factors (campaigns, seasonality, bugs) that could invalidate the signal?
* What did we learn that we did not expect — and does it change the next step?
* Who needs to see this verdict before we commit to the next investment decision?
* If inconclusive, what specific adjustment would make the next experiment more decisive?
