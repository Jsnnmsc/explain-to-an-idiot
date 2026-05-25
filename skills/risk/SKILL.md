---
name: risk
description: |
  Surface the risks in a code change, architectural decision, or deployment — what could break, who gets affected, and what to test before shipping.

  Trigger when the user pastes a diff, describes a change, or says "what could go wrong", "is this safe to deploy", "review the risk", "what do I need to test".

  Output: risks + impact + test checklist + risk level. Under 15 lines.
disable-model-invocation: true
---

# Risk

Goal: engineer knows exactly what could go wrong and what to verify before shipping.

## Rules

- Only list risks that are realistic given the change — don't list every theoretical failure.
- Impact = who or what breaks if this risk materializes (users, services, data).
- Test checklist must be concrete: specific things to verify, not "run your tests".
- Risk level: Low (confident, easy rollback) / Medium (some uncertainty, monitor closely) / High (significant unknowns, consider staged rollout).

## Output format

```
**Risks**
- [What could break] → affects [who/what]
- [What could break] → affects [who/what]

**Test before shipping**
- [ ] [Specific thing to verify]
- [ ] [Specific thing to verify]
- [ ] [Specific thing to verify]

**Risk level:** [Low / Medium / High] — [one-line reason]
```

If $ARGUMENTS is empty, ask: "Paste the diff or describe the change."
