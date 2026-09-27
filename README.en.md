# painpoint-discovery

Discover user friction, test product assumptions, and hand an evidence-linked prototype brief to a development agent.

[中文](README.md) · [Skill](skills/painpoint-discovery/SKILL.md) · [Synthetic example](examples/synthetic-research.md) · [Evaluation](evals/results.md)

This is an on-demand instruction skill, not a crawler or a background service. It uses the host's available search, browser, API and file tools. No specific model, paid search provider or deployment platform is required.

[Real desk-research pilot](examples/research-students-desk-pilot.md): student literature-note questions led to an existing matrix template, so the outcome was to test reuse before building. The release distinguishes population fit, adjacent pains, date provenance and documented versus observed alternative capabilities.

## Three entry points

- **Discover:** Start with a population or domain and compare concrete task problems.
- **Validate:** Check an idea, demo or product against current evidence and alternatives.
- **Handoff:** Turn supplied research into a bounded MVP brief, preserving evidence gaps.

Outputs connect **evidence E → pain P → requirement R → acceptance A**. Analyst-proposed designs are labeled separately from observations. Personal utility and open-source value do not require evidence of willingness to pay.

## Install and use

Copy the complete `skills/painpoint-discovery/` folder into your host's skill directory, including its references and assets. For local Codex discovery, use project `.agents/skills/` or user `~/.agents/skills/`. From this package's root, the following avoids replacing an existing installation:

```sh
mkdir -p "$HOME/.agents/skills"
if [ -e "$HOME/.agents/skills/painpoint-discovery" ] || [ -L "$HOME/.agents/skills/painpoint-discovery" ]; then
  echo "Existing installation found; compare versions before replacing."
else
  cp -R skills/painpoint-discovery "$HOME/.agents/skills/painpoint-discovery"
fi
```

See the [official skill documentation](https://learn.chatgpt.com/docs/build-skills), checked on 2026-09-27. Restart Codex if the skill does not appear. This package has not automatically installed itself, and host installation has not been tested across products.

```text
Use $painpoint-discovery to find up to three workflow problems affecting
freelance designers in the UK. I can spend two weeks on a prototype.
Compare current alternatives, preserve counterevidence and cite sources.
```

```text
Use $painpoint-discovery to validate my meeting-notes-to-quote idea for small
design studios. Determine what they currently do before suggesting a build.
```

```text
Use $painpoint-discovery to prepare a prototype brief from these interview
notes. Label assumptions and give testable acceptance criteria. Do not code
or deploy yet.
```

The agent responds in your language and adapts search languages to the population. The default effort cap is up to three candidate problems and two passes: discovery, then alternatives/counterevidence. It may recommend no opportunity.

## Outputs and limits

A verdict, evidence ledger, problem comparison and validation experiment; a development handoff only when appropriate. The handoff includes scope, contracts, failure cases, acceptance and unresolved assumptions. Using AI to write software does not imply that the product itself needs AI.

Live discovery requires host-provided search or browsing. Without it, the skill performs an explicitly materials-only review. Login barriers and unavailable pages remain coverage gaps. It does not infer page contents from snippets or treat social engagement as purchase evidence.

No guarantee of profitable demand is made. Draft outreach and developer prompts are deliverables, not authorization to contact people, build, deploy or schedule monitoring.

## Evaluation and release

See [fixtures](evals/scenarios.json), [rubric](evals/rubric.md) and [results](evals/results.md) for bounded synthetic smoke tests and their limitations. The synthetic example is not market validation; the separate desk pilot is also limited to public sources. The [release regression](evals/release-results.md) passed all six checks with both versions, providing no evidence of behavioral improvement. No statistical improvement over baseline is claimed.

Repository: [EmilyJYQ/painpoint-discovery](https://github.com/EmilyJYQ/painpoint-discovery). The owner has not selected a license; no open-source license is granted. Public visibility does not grant permission to modify, redistribute or use commercially. See the [release checklist](RELEASE-CHECKLIST.md). Third-party reference screenshots and private research are excluded. Instructions and templates were independently written from workflow ideas shown in a user-supplied demonstration, without access to its original skill source.
