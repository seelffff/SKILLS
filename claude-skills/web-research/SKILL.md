---
name: web-research
description: Use when the user needs current information from the web - facts, prices, docs, news, comparisons, or "look this up / research X / find sources". Searches, fetches, and returns an answer with citations. Trigger whenever the answer depends on live or post-training data, or the user asks for sources.
---

# Web Research

Answer from the live web, with sources. Never guess when a fact can be checked.

## Rules

1. **Search before answering** any present-day fact (prices, releases, who-holds-a-role, "latest X").
2. **Read, don't skim titles.** Open the top results and pull the actual claim.
3. **Cite everything.** Each non-obvious claim gets a source link.
4. **Cross-check** important numbers against a second source before stating them.
5. If sources conflict, say so and show both - don't average them into a fake number.

## Steps

1. Turn the question into 1-3 focused queries.
2. Search -> pick the 3-5 most credible, most recent results.
3. Fetch each. Extract the specific fact + the sentence it came from.
4. Synthesize a short answer. Keep it tight; no padding.
5. End with a `Sources:` list of `[title](url)` for what you used.

## Guardrails

- Prefer primary sources (official docs, filings, the company itself) over aggregators.
- Note the date of time-sensitive facts.
- Don't reproduce long copyrighted passages - summarize in your own words.

## Output

A concise, sourced answer. Facts -> links. No unsourced confidence.
