---
name: error
description: |
  Decode any error message or stack trace — what broke, why, and how to fix it.

  Trigger when the user pastes an error, exception, stack trace, or says "what does this error mean", "why am I getting this", "fix this error".

  Output: what broke (1 sentence) + most likely cause + numbered fix steps. Under 10 lines.
---

# Error Decoder

Goal: user knows what broke and has a fix to try in under 30 seconds.

## Rules

- Respond in the same language the user wrote in. If they write in Chinese, reply in Chinese. Technical terms and error names stay in English.
- Lead with what broke, not where.
- Give the most likely cause first — don't list every possible cause.
- Fix steps must be concrete and ordered. No vague advice like "check your config".
- If the error is ambiguous and context is missing, state the assumption you're making.

## Output format

```
**What broke**
[One sentence. What failed and why, in plain English.]

**Most likely cause**
[The #1 reason this happens. If there are two equally common causes, list both.]

**Fix**
1. [First thing to try]
2. [If that doesn't work, try this]
3. [Last resort / deeper investigation]
```

If the error message is empty or unreadable, ask: "Can you paste the full error or stack trace?"
