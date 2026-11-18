# Audit rubric

Use pass / fail / n/a per criterion. Attach findings with evidence. Do not collapse into one vanity score.

## A. Spec & structure (static)

| ID | Criterion | Pass when |
| --- | --- | --- |
| A1 | Frontmatter valid | YAML opens/closes correctly; required `name`, `description` present |
| A2 | Name rules | Matches Agent Skills: ≤64 chars, `a-z0-9-`, no leading/trailing/consecutive hyphens; equals parent folder |
| A3 | Description bounds | Non-empty; ≤1024 chars (spec). Platform adapters may add stricter caps — check adapter, don't invent |
| A4 | Description content | States **what** + **when**; specific keywords; not marketing fluff alone |
| A5 | Progressive disclosure | Body lean enough to act; bulky detail in `references/` / `scripts/` / `assets/`; links one level deep from SKILL.md |
| A6 | Resource integrity | Relative links resolve; scripts/assets mentioned exist; no dangling inbound refs after edits |

## B. Trigger quality (static review + eval)

| ID | Criterion | Pass when |
| --- | --- | --- |
| B1 | Positive coverage | Obvious and paraphrased asks that match scope should trigger |
| B2 | Negative rejection | Unrelated and near-miss asks should not trigger |
| B3 | Boundary clarity | Ambiguous cases have an explicit expected decision |
| B4 | Collision | In a library, two skills do not both claim the same primary trigger without a deliberate split |

## C. Instruction quality (human/static; confirm with execution evals)

| ID | Criterion | Pass when |
| --- | --- | --- |
| C1 | Density | Every paragraph changes behavior; no tutorial of model-obvious facts |
| C2 | Freedom fit | Fragile steps are exact; judgment-heavy steps leave room; explain *why* over ALL-CAPS MUST spam when possible |
| C3 | Completeness | Steps have checkable done-criteria for critical path |
| C4 | Lessons not logs | Pitfalls are reusable rules + brief why; no ticket IDs, dates, or chat transcripts as sediment |
| C5 | No hub-skill | Skill is not merely a router table to siblings |

## D. Constraints & safety

| ID | Criterion | Pass when |
| --- | --- | --- |
| D1 | Constraint preservation | Auth, approval, irreversible-action, and privacy rules remain after proposed edits |
| D2 | Untrusted content | Skill does not instruct the agent to obey untrusted tool/web payloads blindly |
| D3 | Review hygiene | No secrets; scripts not required to be executed to audit; destructive ops gated |

## E. Evaluation readiness

| ID | Criterion | Pass when |
| --- | --- | --- |
| E1 | Fixtures exist | ≥1 positive, ≥1 negative, ≥1 execution/constraint case (ideally more) |
| E2 | Split | Tune vs held-out identified |
| E3 | Honest status | Model results labeled `not_run` / `passed` / `failed`; never simulated as passed |

## Severity guide

- **blocker:** broken frontmatter; missing critical safety constraint; merge that orphans refs; instruction-injection in reviewed material that would be dangerous if followed
- **major:** systematic over/under trigger; large dead prose; duplicate skills fighting; body dumping what belongs in references
- **minor:** wording, ordering, missing nice-to-have examples

## Accept / reject patches

Accept a patch set only if:

1. Blockers addressed or explicitly deferred by user
2. No held-out regression on trigger or execution (or status `proposed-unverified` with test pack)
3. D1 still passes
4. Edit set stayed within the approved budget
