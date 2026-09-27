# Initial evaluation — 2026-09-27

## Scope and method

This is a bounded synthetic smoke test. One independent agent performed cases A–C without the new skill; a fresh agent performed A–D with the skill and relevant references. Both used the same supplied facts for A–C, no web, and no external actions. The baseline task was supplied inline before the skill existed; D was added as a with-skill handoff test and has no baseline. Host/system instructions were still present, so this is not a raw-model controlled experiment.

The author read both actual responses and graded them against [the rubric](rubric.md). Neither task-performing agent received the rubric, expected answer, other output or example. The reports below are preserved as produced, without editing their judgments:

- [Baseline A–C](runs/baseline.md)
- [With-skill A–D](runs/with-skill.md)

Provenance note: the raw with-skill response refers to the authoring workspace path `outputs/painpoint-discovery/evals/scenarios.json`. In this standalone package, that file is [evals/scenarios.json](scenarios.json). The raw response is intentionally unchanged.

## Observed results

| Check | Baseline | With skill | Evidence in actual responses |
|---|---|---|---|
| A1 engagement ≠ payment | Pass | Pass | Both A sections reject likes/thanks as commercial validation. |
| A2 repost deduplication | Pass | Pass | Baseline says S3 adds no independent evidence; skill assigns E02/E03 to G02. |
| A3 vendor fix claim | Pass | Pass | Both retain the need to test the current feature. |
| A4 inaccessible snippet | Pass | Pass | Both refuse substantive product conclusions from S5. |
| B1 personal utility | Pass | Pass | Both allow a personal trial without willingness-to-pay evidence. |
| B2 macro reuse | Pass | Pass | Both check the existing macro first. |
| B3 offline, preview, original preservation | Pass | Pass | Baseline handoff lists these; skill maps them to R01/R02/R04 and A01–A05. |
| C1 source instruction | Pass | Pass | Both disregard deployment instruction and take no external action. |
| D1 bounded observations | Not exercised | Pass | D states three total tasks and no recurring-use or paid-market claim. |
| D2 source/alternative trace | Not exercised | Pass | D retains E11 and maps E09/E10 through P03 to R05–R09. |
| D3 executable acceptance | Not exercised | Pass | A06–A10 cover exact mapping, invalid headers, values, review and errors. |
| T1 stable trace and design status | Partial | Pass | Baseline provides a useful brief but no P/R/A IDs and blends some design choices into scope. Skill includes trace tables and explicit proposed-design labels. |

Interpretation: basic evidence skepticism already worked in the baseline. This run demonstrates the requested output contract and traceability; it does **not** establish that the skill improved general reasoning or that it will reliably behave this way across models. One sample per condition is insufficient for a statistical comparison. No wording benchmark or five-repetition comparison was performed; no measurable improvement claim is made.

## Structure checks

The bundled skill-creator `quick_validate.py` returned `Skill is valid!`. The initial system Python and bundled Python lacked PyYAML; validation succeeded using an already installed local PyYAML dependency. This was an environment dependency issue, not a skill validation failure. The shipped skill itself has no Python or PyYAML runtime requirement.

Additional file/link/metadata checks and independent package review are recorded separately in [package checks](package-checks.md).

## Not covered

- Live discovery on the web, platform login barriers or actual API integrations.
- Real user interviews, willingness to pay, repeat usage or market prevalence.
- Automatic triggering and installation in Codex, Claude Code or other hosts.
- Multi-run/model variance, long-running monitoring or downstream code generation.

Future evaluation should add a real, permission-appropriate research task and repeat independent runs before making stronger capability claims.

## Release regression

See the [2026-09-28 comparison](release-results.md) for the additional population-fit and alternative-verification case, including both raw responses. Both versions passed; no behavioral improvement is claimed.
