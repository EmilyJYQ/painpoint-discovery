# Release regression — 2026-09-28

A bounded synthetic comparison of the previous skill and the revised skill, using the same five facts in [scenario E](release-scenario.json). Two independent agent contexts received the facts and their respective skill instructions. Neither received the scoring rubric or the other response. The author graded the saved outputs; this was not an independent blinded assessment or a repeated benchmark.

| Criterion | Previous skill | Revised skill |
|---|---|---|
| Unknown population/region not treated as Chinese student evidence | Pass | Pass |
| Quote retrieval and matrix assembly kept separate | Pass | Pass |
| Reposted F1/F5 grouped as one source event | Pass | Pass |
| Vendor and official features labeled documented, not tested | Pass | Pass |
| Relative/snippet dates and unknown edits remain uncertain | Pass | Pass |
| Existing-solution trial with observable results and reuse outcome | Pass | Pass |

Raw outputs: [previous skill](runs/release-baseline.md), [revised skill](runs/release-with-skill.md). Historical workspace-relative references in these unedited responses describe the run environment; scenario E is the public fixture linked above.

Both versions passed all six checks. These runs do not demonstrate a behavioral improvement. The revision makes source fit, date provenance and alternative-verification states explicit in reusable instructions and tables. Its practical value still requires repeated use and observation.

The [research-student desk pilot](../examples/research-students-desk-pilot.md) informed these changes. It predates this regression and was not a fresh validation of the revised skill. No students were interviewed, recruited or tested in this regression. No vendor software was installed or benchmarked. Host discovery, cross-model reliability and market demand remain untested.
