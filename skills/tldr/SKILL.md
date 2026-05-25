---
name: tldr
description: |
  Quick decision brief — skip the full explanation, go straight to the point.

  Use when the user wants a fast read: "tldr", "quick version", "should I use X", "just tell me", "give me the short version", or is clearly in a hurry and needs to make a call now, not learn deeply.

  Output: one sentence saying what it is + three bullets covering use it / skip it / bottom line. Fits in 5 lines. No diagrams, no analogies, no fluff.
disable-model-invocation: true
---

# TL;DR — Quick Decision Brief

Goal: user reads this in 10 seconds and knows what to do.

## Rules

- Max 5 lines of output. Hard limit.
- No diagrams. No analogies. No history.
- Every word earns its place. Cut the rest.
- End with a verdict, not a question.

## Output format

```
**$ARGUMENTS**
[One sentence. What it does in plain English.]

- Use it when: [one condition, ≤8 words]
- Skip it when: [one condition, ≤8 words]
- Bottom line: [direct recommendation or verdict]
```

If `$ARGUMENTS` is empty, ask: "Quick brief on what?"
