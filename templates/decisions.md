# Architecture Decisions

> Version: 0.2
> Input: idea-brief.md + project-context.md + DB schema
> Output: Architecture decisions + NFR notes ready for task breakdown

> **THINK · Steps 2-4 · 30 min · With AI · NO CODE**
>
> Feed AI your brief, project context, and schema. Ask for options. Challenge them. You decide.

## Context Given to AI

[What did you feed in? Brief, project-context.md, schema files, existing code — list it so the conversation is reproducible.]

## AI Stress-Test

> Prompt: "Review this brief. Give me numbered questions about edge cases, missing requirements, and risks. One question per line. I'll reply by number."

[Paste the numbered questions AI asked and your answers here.]

## Options Explored

> Prompt: "Given this brief and project context, suggest 2-3 architecture approaches. For each: approach summary, pros, cons, estimated complexity. No code."

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

> Continue in the same AI session — context is already loaded.
> Prompt: "Review these architecture decisions against these NFRs: security, performance, observability, error handling, rollback. Flag any concerns."

Pressure-test the chosen approach before BUILD starts. Mark each: ✅ covered · ⚠️ needs attention · ➖ not applicable.

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

**Author:** [name] · **Date:** [YYYY-MM-DD]
