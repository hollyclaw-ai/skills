---
name: pr-review
description: Review pull request diffs for correctness, risk, and actionable nits. Use when the user asks to review a PR, diff, or merge request — not for designing new features from scratch or acting as a merge gate without being asked.
---

# PR Review

Review a PR/diff and return prioritized findings. Do not approve or reject unless the user asks for a verdict.

## When to Use

- User asks to review a PR, patch, or diff
- Don't use for: greenfield feature design, writing the implementation, or silent merge authorization

## Procedure

1. Identify the change surface (files, intent). Done when intent is one sentence.
2. List blockers (correctness, security, data loss) before nits. Done when each blocker cites a file/hunk.
3. List secondary risks and style nits separately. Done when nits are clearly labeled non-blocking.
4. End with questions/gaps — not a fake approve. Done when verdict is absent unless requested.

## Pitfalls

- Over-broad descriptions steal triggers from sibling skills — keep one review skill.
- "Always approve or request changes" forces merge-gate behavior the user may not want.

## References

- Style heuristics: `references/style-notes.md`
