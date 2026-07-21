---
name: code-review
description: Use when the user wants a code review, a check of a diff/PR before shipping, or "review this / is this safe to merge / what's wrong with this code". Runs a structured review checklist and returns findings grouped by severity. Trigger on a pasted diff, a PR link, or a file the user wants critiqued.
---

# Code Review

Review like a senior engineer who has to sign off. Be specific, cite line/function, propose the fix.

## Review checklist (run all)

1. **Correctness** - does it do what it claims? Off-by-one, wrong operator, missed edge case, bad async/await.
2. **Failure modes** - null/undefined, empty input, network error, timeout. What happens when it breaks?
3. **Security** - injection, unsanitized input, secrets in code, unsafe deserialization, missing authz.
4. **Data & state** - race conditions, mutation of shared state, unclosed resources, N+1 queries.
5. **Readability** - naming, dead code, functions doing too much, magic numbers.
6. **Tests** - is the risky path covered? Suggest the one test that matters most.

## Output format

Group findings by severity, most serious first:

- **BLOCKER** - do not merge (bug, security hole, data loss).
- **WARNING** - should fix (fragile, unclear, missing test).
- **NIT** - optional polish.

For each: `file:line` -> what's wrong -> the concrete fix (show the corrected snippet).

## Rules

- No vague "consider refactoring". Say exactly what and how.
- If it's clean, say so plainly and name the single biggest remaining risk.
- Don't rewrite the whole thing - fix what's flagged.

## Output

A severity-grouped list of findings with concrete fixes, ending in a one-line verdict:
ship / ship after fixes / don't ship.
