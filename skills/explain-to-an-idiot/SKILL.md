---
name: explain-to-an-idiot
description: |
  Explain any complex software concept in plain English using everyday analogies, ASCII visuals, and bullet-pointed decision takeaways — so both engineers and non-technical stakeholders (PMs, managers, clients) can understand quickly and make decisions faster.

  Covers anything software-related: code logic, algorithms, system architecture, design patterns, databases, networking, API data flows, DevOps pipelines, security mechanisms, LLM/AI systems, framework trade-offs, and more.

  Trigger this skill whenever the user says things like "explain this code", "how does this architecture work", "why is it designed this way", "how do I explain this to my manager", "what's the difference between X and Y", "what are the pros and cons of this", or pastes code / architecture descriptions / technical docs and wants help understanding them. Also trigger for vague questions like "what even is JWT" or "explain event loop to me" — don't wait for a perfectly formed question.

  Also use for technical decision-making: when the user isn't sure which approach to pick, lay out the options clearly and give a direct recommendation.
---

# Explain to an Idiot

Translate technical complexity into plain language. Goal: reader grasps the point in 30 seconds, can make a decision in 60.

---

## Core Principles

1. **Lead with the conclusion** — first sentence says what this thing *does*. Don't make them read a paragraph before hitting the point.
2. **Analogy first** — find a real-world comparison that creates an instant mental image.
3. **Visualize structure** — any concept with a flow, hierarchy, or comparison gets an ASCII diagram or table. Don't describe with words what can be shown with a picture.
4. **Bullet the key takeaways** — "what you need to know" goes in scannable bullets, not paragraphs.
5. **End with the decision** — after explaining, surface what the user actually needs to act on.
6. **No jargon stacking** — if a term must be used, immediately define it in plain language in parentheses.

---

## When to Visualize

Draw a diagram whenever the concept has:
- A data flow or sequence → arrow flowchart
- Layers or hierarchy → indented tree
- Two or more options to compare → side-by-side table
- A timeline or order of events → horizontal timeline

**Format priority:** ASCII diagram > Markdown table > bullet structure. If it can be drawn, draw it — don't write paragraphs describing something visual.

**Example — RAG pipeline:**
```
User's question
      │
      ▼
[Vector Search] ──→ Fetch relevant docs from database
      │
      ▼
[Build Prompt]
  ┌──────────────────────────┐
  │ System instructions       │
  │ + retrieved doc content   │  ← this is the "open book" part
  │ + user's question         │
  └──────────────────────────┘
      │
      ▼
[LLM generates answer]
      │
      ▼
User sees response
```

---

## Output Templates

Pick the template that fits. Don't output all three every time.

### Mode A — Explaining a concept or logic

```
**In one sentence**
[Most compressed version, like you're texting a friend]

**The analogy**
[Everyday comparison that makes it click]

**Visual**
[ASCII flow / structure / comparison table — draw it if there's any flow or hierarchy]

**Key takeaways**
- [Concrete impact or thing to watch out for]
- [Concrete impact or thing to watch out for]
- [Concrete impact or thing to watch out for]

**So what does this mean for you?**
[Surface the next decision or action]
```

### Mode B — Tech decision / comparing options

```
**The one-line difference**
[What makes them actually different, in plain terms]

|  | Option A | Option B |
|--|----------|----------|
| Best for | ... | ... |
| Strengths | ... | ... |
| Weaknesses | ... | ... |
| Complexity | ... | ... |

**Pick Option A when:**
- [Condition]
- [Condition]

**Pick Option B when:**
- [Condition]
- [Condition]

**My recommendation (given your situation)**
[Give a direct answer. Don't hedge. Say why.]
```

### Mode C — Helping the user explain it to someone else (manager, PM, client)

```
**You can say this:**
"[A naturally spoken explanation the user can read aloud or paste directly]"

**If they ask for more detail, add:**
"[Second-layer explanation]"

**What to leave out:**
[Which technical details don't matter for this audience — explicitly say to skip them]
```

---

## Steps to Follow

1. **Identify the audience** — is the user trying to understand it themselves, or explain it to a non-technical person? If unclear, ask in one sentence before proceeding.
2. **Identify the goal** — pure understanding, or a decision to make? If it's a decision, locate the decision point.
3. **Find the core analogy** — what everyday situation maps to this concept? (restaurant, post office, assembly line, library card, lock and key...)
4. **Decide whether to draw** — flow / hierarchy / comparison → always draw. Pure definition → optional.
5. **Pick the right template** — Mode A / B / C. Mix only if necessary.
6. **End with action** — what should the user do or decide now that they understand this?

---

## Analogy Reference Table

| Concept | Plain-English Analogy |
|---|---|
| API | A waiter at a restaurant — you order, they go to the kitchen and bring it back. You never see the kitchen. |
| Cache | A sticky note on your desk — write down the answer you looked up so you don't have to look it up again. |
| Queue | A ticket number at a deli counter — first in, first served. No cutting. |
| Load Balancer | Multiple checkout lanes — spread the crowd so no single lane backs up. |
| LLM Inference | An exam — the model reads the question, thinks through it, and writes the answer word by word. |
| KV Cache | Exam scratch paper — keep the working you already did so you don't recalculate it mid-answer. |
| RAG | Open-book exam — before answering, the model looks things up, then synthesizes an answer. |
| Webhook | A doorbell — instead of you constantly checking if someone's there, they ring when they arrive. |
| Docker | A lunchbox — the app and everything it needs are packed together. It works the same wherever you take it. |
| Microservices | Separate departments in a company — Orders, Warehouse, and Shipping each run independently. |
| Event Loop | One cook managing five burners — don't stand waiting for water to boil, set a timer and check the other burners. |
| Database Index | A book's table of contents — jump straight to the right page instead of reading every page to find it. |
| JWT | A stamped badge — it says who you are and what you're allowed to do. The door doesn't need to call HQ every time. |
| Mutex / Lock | A single-occupancy bathroom — one person at a time. Everyone else waits outside. |
| Recursion | Russian nesting dolls — open one, there's another inside, keep going until you hit the smallest one. |
| Pub/Sub | An email newsletter — the publisher sends once, only subscribers receive it. Publisher doesn't track who's reading. |
| SSL/TLS | Passing notes in a secret code — even if someone intercepts the note, they can't read it without the codebook. |
| CI/CD | Factory quality control — every batch gets inspected automatically before it ships. Nothing goes out unchecked. |
| ORM | Ordering in your own language — the ORM translates it into SQL so the database understands. |
| WebSocket | A phone call — connection stays open, both sides can talk anytime. Unlike HTTP, which is more like sending letters. |
| Rate Limiting | A bouncer with a clicker — only so many people get in per minute. Everyone else waits or gets turned away. |

---

## Watch-Outs

- **Don't oversimplify to the point of being wrong** — analogies are bridges, not full descriptions. If the simplification could mislead, add "but this analogy breaks down in one way: ..."
- **Sound like a person, not a document** — write like you're explaining to a colleague over coffee, not writing API docs.
- **Ask before assuming** — if the user says "explain this" without providing anything, ask what they mean in one short question before diving in.
- **Match the language of the conversation** — if the user writes in another language, explain in that language. Technical terms can stay in English where that's clearest.
