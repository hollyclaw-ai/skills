# Sources

Access date: **2026-11-18** (Asia/Taipei). Links were opened during drafting. Summaries below are attributions, not license grants.

## Primary sources

| Source | URL | What we used | License / notes |
| --- | --- | --- | --- |
| Agent Skills Specification | https://agentskills.io/specification | Directory layout, frontmatter constraints, progressive disclosure, validation pointer | Spec site; confirm license terms before redistributing verbatim text. This pack paraphrases rules only. |
| agentskills GitHub | https://github.com/agentskills/agentskills/ | Format overview, progressive disclosure stages | See repo LICENSE before reuse of code/text |
| Anthropic Skill authoring best practices | https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices | Concision, degrees of freedom, description writing, evals-first, &lt;500 line body guidance | Anthropic docs — paraphrase only; do not paste long excerpts |
| Anthropic skill-creator SKILL.md | https://github.com/anthropics/skills/blob/main/skills/skill-creator/SKILL.md | Create → eval → iterate loop; pushy-but-precise descriptions; comparator/grader pattern | See anthropics/skills LICENSE (repo) |
| Improving skill-creator article | https://claude.com/resources/articles/improving-skill-creator-test-measure-and-refine-agent-skills | Trigger tuning, regression evals, capability-uplift vs preference skills | Anthropic site terms |
| Hermes Curator | https://hermes-agent.nousresearch.com/docs/user-guide/features/curator | pin/lock/dry-run/consolidate, stale 14 / archive 30, no auto-delete | Hermes docs — platform adapter only |
| Hermes Skills System | https://hermes-agent.nousresearch.com/docs/user-guide/features/skills | write_approval gate, progressive disclosure, agentskills compatibility claim | Hermes docs |
| Hermes skill authoring | https://hermes-agent.nousresearch.com/docs/user-guide/skills/optional/software-development/software-development-hermes-agent-skill-authoring | 60-char description hardline, ~100/200 line targets, no hub skills, body structure | MIT-licensed skill page metadata on Hermes site; still paraphrase |
| SkillOpt research blog | https://www.microsoft.com/en-us/research/blog/skillopt-agent-skills-as-trainable-parameters/ | Bounded edits, held-out gating, rejected-edit memory | © Microsoft — cite, don't copy paper text |
| SkillOpt project | https://microsoft.github.io/SkillOpt/ | Pipeline framing | See GitHub license: https://github.com/microsoft/SkillOpt |
| Microsoft Learn Agent Skills | https://learn.microsoft.com/en-us/agent-framework/agents/skills | Progressive resource/script load in Agent Framework | Microsoft docs terms |

## Design vs upstream fact

| Claim | Status |
| --- | --- |
| agentskills `description` max 1024 | Upstream fact |
| Hermes description max 60 | Upstream fact (Hermes hardline), **not** universal |
| Hermes body target ~100–200 lines | Upstream fact (house style) |
| Anthropic ~500 line body guidance | Upstream guidance |
| Default audit-only + apply gate | **skill-better design** |
| SkillOpt-style held-out accept rule | **design adapted** from SkillOpt ideas |
| Fictional examples in `examples/` | Original for this pack |

## License and redistribution notes

- This repository uses the root MIT `LICENSE` (Copyright (c) 2026 hollyclaw-ai). Do not invent a different copyright holder for this pack.
- Re-check upstream licenses for any file you might later vendor
- Keep examples synthetic / strip private customer skills from examples
- Re-verify Hermes/Anthropic URLs and limits (they can change)
- Draft status remains: static validation and fictional walkthroughs only; no claimed live-model uplift yet
