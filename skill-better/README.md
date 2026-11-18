# skill-better (draft)

Portable Agent Skill that **audits and improves other skills** for trigger quality, redundancy, safety, and task performance. Designed to be runtime-agnostic; Hermes and other platform rules are optional adapters.

**Status:** draft. Static checks and fictional walkthroughs only. **Not tested against real private skills** and **not measured with live model runs**. Licensed under the repository [MIT LICENSE](../LICENSE) (Copyright (c) 2026 hollyclaw-ai).

## Install

Copy the `skill-better` folder into your agent's standard skills directory so that:

```text
<skills-root>/skill-better/SKILL.md
```

Examples of skills roots (depends on product): project `.agents/skills/`, Claude skills folders, or Hermes `~/.hermes/skills/...`. Keep the folder name `skill-better` matching frontmatter `name`.

Then reload/restart the agent session if your runtime only indexes skills at startup.

## Usage

- **Audit (default):** ask the agent to run skill-better on a path — read-only findings + patch plan
- **Apply:** explicitly authorize the listed ops from an audit
- **Evaluate:** run or emit fixtures per `references/eval-protocol.md` (mark `not_run` without a provider)

## Layout

- `SKILL.md` — executable workflow
- `references/` — rubric, eval protocol, platform adapters, sources
- `examples/` — fictional before/after cases with expected audits and evals

## Open-source notes

- This pack ships under the repo MIT license; do not invent a different copyright holder
- Re-verify upstream licenses in `references/sources.md` before vendoring third-party text
- Examples are synthetic; replace or keep them clearly labeled if you fork
- Run skill-better on real libraries only with owner permission
