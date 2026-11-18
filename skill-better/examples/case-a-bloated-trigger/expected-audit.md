# Expected audit — case A (csv-report)

Mode: audit (read-only). Target: `before/csv-report`.

## Findings (expected)

- [MAJOR] B2/B4 — description vague ("data and files") + body claims PDF/migrations/flights → over-trigger risk
- [MAJOR] C1 — model-obvious CSV tutorial wastes body tokens
- [MAJOR] A4 — description lacks clear when-to-use keywords for CSV reporting
- [MINOR] C3 — steps lack checkable done-criteria
- [MINOR] E1 — no fixtures shipped with before/ (skill-better should draft them)

## Patch plan (expected)

1. Rewrite description: what + when + explicit negatives
2. Delete tutorial prose; add When to Use / Procedure / Pitfalls
3. Remove cross-domain "also use for" scope creep
4. Add evals (pos/neg/exec)

## After status

`after/csv-report` should pass walkthrough triggers in `evals/evals.json`. Model runs: not_run in this draft pack.
