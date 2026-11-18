# Eval protocol

Distinguish **static checks**, **fixture walkthroughs**, and **real model runs**. Never call a simulated judgment a model pass.

## Fixture schema (suggested)

Store as `evals/evals.json` next to the skill or in the audit workspace:

```json
{
  "skill": "example-name",
  "budget": { "max_model_runs": 0, "notes": "0 means pack-only" },
  "cases": [
    {
      "id": "pos-1",
      "split": "tune",
      "type": "trigger_positive",
      "prompt": "User utterance",
      "expect": { "trigger": true }
    },
    {
      "id": "neg-1",
      "split": "held_out",
      "type": "trigger_negative",
      "prompt": "Near-miss utterance",
      "expect": { "trigger": false }
    },
    {
      "id": "exec-1",
      "split": "held_out",
      "type": "execution",
      "prompt": "Task that needs the skill",
      "expect": {
        "must_include_behaviors": ["..."],
        "must_preserve_constraints": ["..."],
        "must_not": ["..."],
        "resource_refs_ok": true,
        "failure_exit": "safe stop without destructive side effects"
      }
    }
  ]
}
```

## Case types

| type | Measures |
| --- | --- |
| `trigger_positive` | Description should fire |
| `trigger_negative` | Description should not fire |
| `trigger_boundary` | Document expected fire/skip |
| `execution` | With skill loaded, behavior quality |
| `constraint` | Safety/approval rules still held |
| `resource` | Agent finds and uses referenced files correctly (without running untrusted scripts during audit) |
| `failure_exit` | Bad inputs → clean refusal/stop |

## Running modes

1. **Static:** rubric A/D + link integrity (always)
2. **Walkthrough:** reviewer marks expected trigger given description only (cheap; label `walkthrough`)
3. **Model trigger probe:** show catalog metadata only; ask whether skill would load (label `model_trigger`)
4. **Model execution:** full skill in context on execution cases (label `model_exec`)
5. **Blind compare (optional):** skill A vs B vs no-skill without revealing which (inspired by skill-creator comparators / SkillOpt gating)

## Independence and comparability

Keep held-out answers out of the rewrite context where possible. If exposed, disclose contamination and reserve fresh cases for independent acceptance. Compare baseline and candidate under the same model, runtime, settings, and comparable budgets. Metadata-only probes do not prove actual runtime routing. Never let aggregate gains conceal a critical constraint failure. A provider-free pack contains fixtures and a manual protocol, not an automated runner.

## Budgets

- Respect `budget.max_model_runs` and user-provided provider limits
- If no provider: produce the eval pack + grading checklist; set `model_runs: not_run`
- Prefer fewer high-signal held-out cases over many noisy ones

## Gating rule (SkillOpt-inspired, adapted)

Treat the skill text like a trainable artifact:

- Propose **bounded** edits
- Keep rejected ideas in a short negative list for the next proposal
- **Accept only** if held-out aggregate does not regress (strict improve when scores exist)
- If only walkthrough evidence exists, status must remain `proposed-unverified`

## Reporting

```text
eval_id / split / type / method / result / notes
pos-1 / tune / trigger_positive / walkthrough / pass / ...
```

Aggregate as counts, not a fake 0–100 quality index.
