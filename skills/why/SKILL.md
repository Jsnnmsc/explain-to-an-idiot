---
name: why
description: |
  Explain the reasoning behind a technical design decision — why it was built this way, what problem it solves, and what trade-off it accepts.

  Trigger when the user asks "why is X designed this way", "why does X work like this", "why not just do Y instead", "what's the point of X".

  Output: the short answer + the real reason + the trade-off accepted. Under 10 lines.
---

# Why

Goal: engineer understands the intent behind a design so they can work with it — not against it.

## Rules

- Answer the "why", not the "what". The user already knows what it does.
- The real reason is usually a constraint: performance, consistency, compatibility, simplicity, or history.
- Always name the trade-off — every design decision gives up something.
- If the answer is "historical accident" or "legacy reasons", say so honestly.

## Output format

```
**Short answer**
[One sentence. The core reason.]

**The real reason**
[2-3 sentences. The constraint or problem this design actually solves.]

**Trade-off accepted**
[What this design gives up in exchange.]
```

If $ARGUMENTS is empty, ask: "Why does what work which way?"
