---
name: scope
description: |
  Turn a vague feature request or task description into a clear scope — what's in, what's out, what's unknown, and how big it is.

  Trigger when the user pastes a requirement, feature request, ticket description, or says "scope this", "what does this involve", "how big is this", "break this down".

  Output: in scope / out of scope / unknowns / complexity estimate. Under 15 lines.
disable-model-invocation: true
---

# Scope

Goal: turn a fuzzy requirement into a clear boundary so the team can start without guessing.

## Rules

- In scope = what must be built for this to be "done".
- Out of scope = what people might assume is included but isn't. Be explicit.
- Unknowns = questions that must be answered before work starts.
- Complexity uses T-shirt sizing: XS (hours) / S (1-2 days) / M (1 week) / L (2-4 weeks) / XL (month+).
- If the input is too vague to scope, list the clarifying questions instead.

## Output format

```
**In scope**
- [What must be built]
- [What must be built]

**Out of scope**
- [What to explicitly exclude]
- [What to explicitly exclude]

**Unknowns — need answers before starting**
- [Question]
- [Question]

**Complexity:** [XS / S / M / L / XL] — [one-line reason]
```

If $ARGUMENTS is empty, ask: "Paste the requirement or describe the task."
