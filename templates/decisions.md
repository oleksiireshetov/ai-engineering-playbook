# Architecture Decisions

**Stage:** THINK • **Version:** 0.3

**Input:** Stress-tested idea-brief.md + project-context.md + DB schema

**Output:** Architecture decisions + NFR notes + mode selection

**Protocol:** Step 2-3 • 30 min • With AI • No Code

> **CORE PRINCIPLE**
>
> Continue in the same AI session as the stress-test — context is already loaded.

---

## Context Given to AI

[What did you feed in? Brief, project-context.md, schema files, existing code — list it so the conversation is reproducible.]

## Options Explored

Feed this prompt to the AI:

```text
Given this stress-tested brief and project context, suggest 2-3 architecture approaches. For each: approach summary, pros, cons, estimated complexity. No code.
```

### Option A: [Name]

**Approach:**

**Pros:**

**Cons:**

### Option B: [Name]

**Approach:**

**Pros:**

**Cons:**

### Option C: [Name] *(if needed)*

**Approach:**

**Pros:**

**Cons:**

## Decision

**Chosen option:** [A / B / C]

**Why:** [1-2 sentences. What tipped the scale?]

**Accepted trade-offs:** [What you're knowingly accepting]

---

## NFR Check (gate)

Feed this prompt to the AI:

```text
Review these architecture decisions against these NFRs: security, performance, observability, error handling, rollback. Flag any concerns.
```

Pressure-test the chosen approach before BUILD starts. 

Mark each: PASS · WARN · N/A

| NFR | Status | Notes |
|---|---|---|
| **Security** — auth, input validation, secrets, data exposure | | |
| **Performance** — latency, throughput, resource usage | | |
| **Observability** — logging, metrics, alerting, tracing | | |
| **Scalability** — will this hold at 2x, 10x current load? | | |
| **Compliance** — PCI, GDPR, audit trail, data retention | | |
| **Error handling** — failure modes, retries, circuit breakers | | |
| **Testing** — how will you verify this works? | | |
| **Rollback** — can you undo this safely? | | |

**Concerns to address during BUILD:**

-

---

## Complexity & Mode

Based on the architecture decisions and scope above:

- [ ] **Hotfix** — broken in prod, fix now → Mode A
- [ ] **Small** (< 1 day) → Mode A
- [ ] **Medium** (1-5 days) → Mode A or B
- [ ] **Feature** (5+ days) → Mode B

**Selected mode:** [A / B]

If Mode B → proceed to [task-breakdown.md](./task-breakdown.md)
If Mode A → skip task breakdown, go straight to BUILD.

---

**Author:** [name] · **Date:** [YYYY-MM-DD]
