# Platform adapters

Universal rules follow the [Agent Skills specification](https://agentskills.io/specification). Below are **optional** overlays. Apply only when the target library declares that platform.

## agentskills.io (baseline)

- Directory + `SKILL.md` with YAML `name` + `description`
- `name`: ≤64, lowercase alphanumeric + hyphens, no leading/trailing/consecutive hyphens; matches folder
- `description`: ≤1024; what + when
- Progressive disclosure: metadata → body → resources; keep body focused; recommended body &lt; 500 lines in Anthropic guidance; spec discusses &lt; 5000 tokens guidance for instructions
- Optional: `license`, `compatibility`, `metadata`, experimental `allowed-tools`
- Validate with `skills-ref validate` when available

## Anthropic / Claude skills (authoring habits)

- Description is the primary trigger surface; be specific; third person
- Prefer concise body; challenge model-obvious prose
- Match degrees of freedom to fragility
- Build evals early; test trigger +, −, and paraphrases; retest after each significant edit
- skill-creator loop: draft → test prompts → qualitative + quantitative review → minimal rewrite → description tuning
- Do not copy Anthropic-only tooling paths into generic skills unless the target runtime has them

## Hermes Agent (overlay — not universal)

Verified from Hermes docs (accessed 2026-11-18):

| Topic | Hermes rule | Universal? |
| --- | --- | --- |
| Description length | Hardline **≤ 60 characters**, one sentence, ends with period; capability not implementation; no marketing words; don't repeat skill/category name | **No** — agentskills allows 1024 |
| Body size | Target ~100 lines simple / ~200 complex; hard cap 100k chars | Target is Hermes house style; 100k is Hermes validator |
| Structure | When to Use (+ Don't use for), Procedure with checkable criteria, pitfalls as reusable rules | Good practice, Hermes-shaped |
| Hub skills | No router/index skills that only point at siblings | Strongly recommended generally |
| Curator | `hermes curator status`; `pin` / `unpin`; `lock` / unlock per docs; `run --dry-run`; consolidation off by default, `run --consolidate` or `curator.consolidate: true`; stale after 14 days, archive after 30 to `~/.hermes/skills/.archive/`; restore supported; never auto-delete | Hermes-only machinery |
| Write gate | `skills.write_approval: true` stages skill_manage writes for approve/reject | Hermes-only |
| Pin vs lock | Pin: skip archive/delete, edits still allowed. Lock: block agent writes entirely | Hermes-only |

When auditing Hermes libraries: enforce 60-char descriptions and curator workflows via this adapter. When auditing generic or multi-runtime packs: keep descriptions informative within the 1024-char spec and put Hermes compression in a Hermes export step.

## Microsoft SkillOpt (method adapter)

SkillOpt treats a skill file as a trainable parameter outside a frozen model: rollout → reflect → bounded add/delete/replace → **validation gate on held-out** → keep rejected edits as negative feedback. Use the *ideas* (edit budget, held-out gate, no uncontrolled growth). Do not require SkillOpt's trainers or claim its benchmark numbers on unrelated skills.

## Microsoft Agent Framework skills

Supports progressive load of metadata, body, resources, and scripts via framework tools. Prefer the same disclosure discipline; follow framework docs for runtime APIs rather than inlining them into every skill.
