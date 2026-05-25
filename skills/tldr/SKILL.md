---
name: tldr
description: |
  Quick plain-English brief — skip the explanation, get the point.

  Use when the user says "tldr", "quick version", "what is X", "should I use X", "just tell me", "give me the short version", or is clearly in a hurry.

  Output adapts to the question:
  - Pure definition ("what is X") → 1 sentence + 1-2 key facts
  - Decision / comparison ("should I use X", "X vs Y") → 1 sentence + use when / skip when / bottom line

  Max 5 lines. No diagrams. No analogies. No history. Direct verdict.
disable-model-invocation: true
---

# TL;DR

Goal: user reads this in 10 seconds and knows what to do.

## Rules

- Respond in the same language the user wrote in. If they write in Chinese, reply in Chinese. Technical terms (JWT, Redis, API…) stay in English.
- Max 5 lines. Hard limit.
- No diagrams, no analogies, no history.
- Every word earns its place.

## Detect the intent, pick the format

**If the question is a definition** ("what is X", "explain X briefly"):

```
**$ARGUMENTS**
[One sentence. What it does in plain English.]

- [Key fact #1]
- [Key fact #2]
```

**If the question involves a decision** ("should I use X", "X vs Y", "is X worth it"):

```
**$ARGUMENTS**
[One sentence. What it does in plain English.]

- Use it when: [one condition, ≤8 words]
- Skip it when: [one condition, ≤8 words]
- Bottom line: [direct recommendation or verdict]
```

If `$ARGUMENTS` is empty, ask: "Quick brief on what?"
