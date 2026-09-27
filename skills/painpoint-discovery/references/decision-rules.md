# Decision rules

Read before comparing opportunities or generating a development handoff.

## Keep three judgments separate

1. **Evidence confidence:** How directly, recently and independently is this exact problem supported? Record unresolved conflicts and sample limits.
2. **Opportunity value:** Would solving it improve the target person's task enough to matter under the user's goal?
3. **Implementation fit:** Can accessible data, tools and resources solve it at an acceptable cost and error rate?

Use high / medium / low / unknown with reasons and E IDs. Unknown is not zero. Avoid arbitrary weighted totals; if the user requests scoring, document weights, uncertain inputs and whether changing weights changes the ranking. Never present a score as measured market probability.

Compare severity, recurrence, alternatives, reachability, software fit, data availability, effort and operating cost. For commercial goals add buyer/user separation, spending evidence and distribution. For personal/open-source goals use task benefit and maintenance cost; absent willingness to pay is not a veto.

Do not equate:

- many likes with adoption or purchasing;
- no public price question with no willingness to pay;
- a free competitor with no opportunity;
- an old complaint with an unresolved current defect;
- a vendor fix announcement with verified user success;
- a simulated interview with a real person;
- “can be coded quickly” with “should be built.”

## Choose the next action

| Decision | Appropriate when | Deliverable |
|---|---|---|
| Prototype validation | A bounded task and testable benefit exist; key inputs and a way to test are available or explicitly planned | Small prototype brief with open assumptions and stop conditions |
| Gather evidence | Key facts could reverse the decision: current failure, user access, data, alternative fit or buyer unknown | Cheapest experiment to resolve the uncertainty |
| Do not build now | An adequate existing solution fits, the task is better solved without software, cost outweighs benefit, or a blocking constraint exists | Evidence-backed reason and conditions for reconsideration |

No universal minimum number of users is required for a personal tool. A few reports may justify an experiment but cannot establish a commercial market. If the user explicitly requests a prototype despite weak evidence, support that as speculative validation without relabeling the evidence or expanding to production deployment.

Check existing solutions before new build work. Compare the actual workflow, price if relevant, offline/data constraints, setup burden and remaining gap. If access prevents checking a competitor, keep its suitability unknown. A build recommendation can be conditional on that check.

For each shortlisted alternative, record one observed verification state:

- **Documented only:** source describes the capability; installation and task fit untested.
- **Attempted:** record version, input/task, steps and actual result, including setup failures.
- **Task success observed:** record what completed, with whose material and under which constraints; this is not proof for other users or versions.

Ask whether the remaining obstacle is missing functionality, setup, migration, training or an organizational constraint. Preserve uncertainty when several explanations fit. If a task-level trial shows existing tools plus modest guidance satisfy the goal, recommend reuse or a guide and stop new-build work. That is a successful discovery outcome, not a reason to search until a build justification appears.

When comparing alternatives, include setup, review and correction in total task cost. An installation failure is a setup observation, not proof that the advertised core feature fails. Use comparable tasks and note learning/order effects when timing repeated trials.

## Design the cheapest informative experiment

For each important assumption, specify:

- Hypothesis and evidence gap.
- Participants/tasks/materials; who will recruit or supply them.
- Method: workflow interview, reproduce current failure, adapt an existing tool, manual service, bounded prototype trial.
- Metric with baseline and units; how it will be observed.
- Proposed pass, revise and stop thresholds; label thresholds as project choices, not established benchmarks.
- Time/cost cap and next decision for each outcome.

Do not invent participant availability, commitments, costs or measured outcomes. Draft outreach only when useful; sending it needs user authorization. Simulated personas can critique questions but cannot fill the evidence gap. A seven-day plan is optional, not a forced schedule.

## Handoff gate and traceability

Use stable E → P → R → A links. Classify each R as **evidence-derived**, **user constraint**, or **proposed design**. Evidence can justify a problem without proving a particular interface or architecture. For proposed requirements record the rationale and validation needed rather than fabricating a supporting user quote. Preserve IDs when revising; mark superseded items instead of renumbering them silently.

A handoff must tell the developer what to build and what remains undecided: one core task, smallest useful loop, non-goals, input/output contracts, normal/error flows, dependencies, data handling, acceptance and outcome metrics. “Fast,” “accurate,” and “easy to use” alone are not acceptance criteria.

For each acceptance item provide setup/input → action → observable expected result, and the linked R ID. Include at least the material failure path and preservation/recovery behavior. Distinguish functional acceptance from the experiment measuring whether the user benefits.

Prefer a deterministic solution when sufficient. If the product itself needs AI, state why simpler alternatives fail, the evaluation set, tolerated errors, cost/latency constraints and fallback or human review. Unknowns stay open; don't invent model performance.

The output is a development brief or validation plan. Actual coding, deployment, outreach and ongoing monitoring require the user's corresponding request; a handoff prompt alone is not authorization.
