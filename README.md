# explain-to-an-idiot

A [Claude Code](https://claude.ai/code) plugin that gives software engineers a set of focused, no-fluff tools for understanding technical concepts, decoding errors, scoping work, and surfacing risk — in your language.

## Skills

| Skill | Invoke | Use when |
|---|---|---|
| **tldr** | `/explain-to-an-idiot:tldr JWT` | You need the point in 10 seconds |
| **error** | `/explain-to-an-idiot:error` + paste trace | You hit an error and need to fix it fast |
| **scope** | `/explain-to-an-idiot:scope` + paste requirement | You need to define what's in/out before starting |
| **risk** | `/explain-to-an-idiot:risk` + paste diff | You want to know what could break before shipping |
| **why** | `/explain-to-an-idiot:why HTTP is stateless` | You want the reasoning behind a design decision |

## Examples

**`tldr`** — adapts to whether you need a definition or a decision:
```
/explain-to-an-idiot:tldr JWT

**JWT**
A tamper-proof token that proves who you are — server signs it, client carries it.

- Use it when: stateless auth across services
- Skip it when: you need server-side session revocation
- Bottom line: use it, keep expiry short (15min)
```

**`error`** — what broke, why, how to fix:
```
**What broke**
Postgres rejected the connection because the pool was exhausted.

**Most likely cause**
Too many concurrent queries without releasing connections — common in async code that doesn't await properly.

**Fix**
1. Check for missing `await` on DB calls in async functions
2. Lower `pool.max` or add a connection timeout
3. Add connection pool monitoring to catch this earlier
```

**`scope`** — clear boundaries before work starts:
```
**In scope**
- User can reset password via email link
- Link expires after 1 hour

**Out of scope**
- SMS reset, OAuth re-auth
- Admin-triggered resets

**Unknowns**
- Does the link invalidate after first use?
- Which email service?

**Complexity:** S — straightforward auth flow, no novel logic
```

**`risk`** — what to verify before shipping:
```
**Risks**
- DB migration changes column type → affects all existing rows
- New index on high-write table → brief lock during deploy

**Test before shipping**
- [ ] Run migration on staging with production data volume
- [ ] Verify reads/writes on affected table after migration
- [ ] Check deploy window — avoid peak traffic hours

**Risk level:** Medium — migration is safe but needs timing care
```

**`why`** — the reasoning behind a design:
```
**Short answer**
HTTP is stateless so servers don't have to remember anything between requests.

**The real reason**
In the early web, servers couldn't reliably store per-client memory across millions of simultaneous users. Statelessness let any server handle any request, making horizontal scaling trivial.

**Trade-off accepted**
The client has to send identity proof (cookie, token) with every request — more data per request, but no server-side session management.
```

## Installation

Run these three commands inside Claude Code:

```
/plugin marketplace add Jsnnmsc/explain-to-an-idiot
/plugin install explain-to-an-idiot@explain-to-an-idiot
/reload-plugins
```

## License

[MIT](./LICENSE)
