# Project Context

**Stage:** All stages • **Version:** 0.3

**Input:** Your project's current state

**Output:** Living context that makes every AI session smarter than the last

**Protocol:** Feed to AI every session • Update every Heartbeat • One per repo

> **CORE PRINCIPLE**
>
> Without this, every AI session starts from zero. With it, Heartbeat #10 is smarter than Heartbeat #1.

--- 

## Project

**Name:** [Project name]
**Description:** [One sentence — what does this system do?]
**Repo:** [Link]

## Scale

[This shapes every AI decision. 3 users ≠ 30,000 users. AI will suggest Kafka and RBAC for a 3-user app if you don't tell it the scale.]

| Metric | Current | Expected (6 months) |
|---|---|---|
| Users | | |
| Daily active users | | |
| Requests per day | | |
| Data volume | | |

## Tech Stack

| Layer | Technology |
|---|---|
| Language | |
| Framework | |
| Database | |
| Cache | |
| Message broker | |
| CI/CD | |
| Hosting | |

## Architecture Overview

[2-3 sentences or a simple diagram. How do the main components talk to each other?]

## Database Schema (key tables)

[Core tables with purpose and key relationships. What AI needs to write correct code.]

```sql
users          — id, email, role, created_at
orders         — id, user_id, status, amount, currency
transactions   — id, order_id, psp_id, status, response_code
```

## API Contracts (key endpoints)

[Main endpoints AI will interact with. Method, path, purpose.]

```http
POST   /api/v1/orders          — Create order
GET    /api/v1/orders/:id      — Get order by ID
POST   /api/v1/payments/init   — Initialize payment with PSP
POST   /api/v1/webhooks/:psp   — Receive PSP callback
```

## Conventions

- **Naming:** [e.g., camelCase for variables, PascalCase for classes, snake_case for DB columns]
- **Error handling:** [e.g., custom AppError class, always wrap external calls in try/catch]
- **Logging:** [e.g., structured JSON, include correlationId in every log]
- **Testing:** [e.g., Jest, test files next to source, naming: *.test.ts]
- **Branching:** [e.g., feature/XX-description, hotfix/XX-description]

## Key Patterns

[Patterns the AI should follow when generating code in this project.]

-

## Known Gotchas

[Things that will trip up AI and new developers. Edge cases, legacy quirks, "don't touch this" areas.]

-

## Recent Changes

[Updated during LEARN. What changed recently that AI needs to know.]

| Date | What Changed | Heartbeat |
|---|---|---|
| | | |

---

*Last updated: YYYY-MM-DD*
