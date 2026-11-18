# Expected audit — case B (overlapping pair)

Mode: audit. Target: `before/` directory (2 skills).

## Findings (expected)

- [MAJOR] B4 — `pr-review` and `code-review-lite` compete on the same primary trigger
- [MAJOR] A4/B2 — `code-review-lite` description is overly pushy ("whenever someone mentions PRs... merging") → over-trigger
- [MAJOR] C5 — router note ("load pr-review instead — or both") is hub-like indirection
- [BLOCKER-risk] D1 — "Approve or reject (always)" pushes irreversible/merge-gate behavior without user ask
- [MAJOR] merge hygiene — `references/style-notes.md` must move with the surviving package

## Patch plan (expected)

1. Merge into single `pr-review` umbrella
2. Carry `references/style-notes.md` into survivor; rewrite links
3. Archive/remove `code-review-lite` after confirming no inbound refs
4. Soften description; remove forced approve/reject
5. Add trigger +/− evals distinguishing feature-design asks

## After status

Only `after/pr-review` remains. `code-review-lite` gone. Model runs: not_run.
