# Project Context

> The living document that makes every AI session smarter than the last.
> Feed it to AI at the start of every THINK and BUILD session.
> Update it at the end of every Heartbeat (LEARN stage).
>
> Required question before updating: *What will AI get wrong next time if I don't update this now?*

## Project

**Name:** [Project name]
**Description:** [One sentence — what does this system do?]
**Repo:** [Link]

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

```
users          — id, email, role, created_at
orders         — id, user_id, status, amount, currency
transactions   — id, order_id, psp_id, status, response_code
```

## API Contracts (key endpoints)

[Main endpoints AI will interact with. Method, path, purpose.]

```
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
