# explain-to-an-idiot

A [Claude Code](https://claude.ai/code) skill that translates any complex software concept into plain English — so engineers and non-technical stakeholders (PMs, managers, clients) can understand quickly and make decisions faster.

## What it does

Give it any technical topic — a chunk of code, an architecture diagram description, a confusing API doc, or just a vague question like *"what even is JWT"* — and it returns:

- A one-sentence summary (the point, upfront)
- A real-world analogy that creates an instant mental image
- An ASCII diagram or comparison table when the concept has structure
- Scannable bullet takeaways
- A direct recommendation when a decision is involved

Three output modes:

| Mode | Use when |
|---|---|
| **A — Explain a concept** | You want to understand something yourself |
| **B — Compare options** | You're choosing between two approaches |
| **C — Explain to someone else** | You need to brief a manager, PM, or client |

## Installation

**Option 1 — one-liner (recommended)**

```bash
npx skills add YOUR_GITHUB_USERNAME/explain-to-an-idiot
```

Requires [Node.js](https://nodejs.org). Restart Claude Code after installing.

**Option 2 — manual**

1. Download [`explain-to-an-idiot.skill`](./explain-to-an-idiot.skill)
2. Drag the `.skill` file into a Claude Code chat window

---

Then invoke it with `/explain-to-an-idiot` or just ask naturally — the skill auto-triggers on phrases like:

- "explain this code"
- "how does this architecture work"
- "how do I explain this to my manager"
- "what's the difference between X and Y"
- "what even is [concept]"

## Example

**Input:** "explain JWT to me"

**Output:**
```
In one sentence
A JWT is a tamper-proof digital badge that proves who you are without the server
needing to look you up every time.

The analogy
Like a stamped visitor badge at an office. Security checks it at the door, stamps it,
and now you can walk around freely — no one needs to call reception every time you
enter a room.

Visual
  User logs in
       │
       ▼
  Server creates JWT
  ┌─────────────────────────────┐
  │ Header (algorithm)          │
  │ Payload (user ID, role, exp)│  ← your info
  │ Signature (server's stamp)  │  ← can't be faked
  └─────────────────────────────┘
       │
       ▼
  Client stores JWT, sends it with every request
       │
       ▼
  Server verifies signature — no DB lookup needed

Key takeaways
- The signature makes it tamper-proof — change anything, signature breaks
- Stateless: server doesn't store sessions, scales easily
- Has an expiry — short-lived tokens (15min) are safer than long ones

So what does this mean for you?
If you're building auth: use short expiry + refresh tokens. If you're debugging:
decode the JWT at jwt.io to see exactly what's inside.
```

## Analogy library

The skill ships with a built-in reference table of 20+ concepts mapped to plain-English analogies — API, cache, event loop, RAG, WebSocket, rate limiting, and more.

## License

[MIT](./LICENSE)
