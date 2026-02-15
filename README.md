# AI Engineering Playbook 💓

> v0.3.0 — Early draft. Feedback welcome.

A discipline layer for building software with AI. Not a new SDLC — add it on top of whatever process you already use.

## Why This Exists

AI coding tools are everywhere. Engineering discipline for using them isn't.

Most teams are figuring it out as they go — prompting, generating, reviewing, shipping — without a shared process for how AI-assisted work should flow. The result: fast output, slow cleanup, growing tech debt that nobody fully understands.

This playbook addresses the actual failure modes of AI-assisted development:

- **Context rot** — AI losing track of your codebase as sessions grow
- **Hallucinations** — code that looks right but calls things that don't exist
- **Scope creep** — AI happily generating beyond what was asked
- **Sunk-cost spirals** — fighting the AI instead of writing it yourself

Built from real production experience — not from theory.

## How It Works: The Heartbeat

Every piece of work — feature, bug fix, hotfix, refactor — follows the same rhythm:
```
THINK → BUILD → REVIEW → SHIP → LEARN
```

`project-context.md` feeds every THINK and BUILD session. It gets updated only when the project itself changes — new tables, endpoints, patterns, or gotchas.

> Try it on one task. If the output is cleaner and the process is clearer — keep going.

## Quick Start

1. Create `project-context.md` in your project root and fill it in:

```bash
curl -sO https://raw.githubusercontent.com/oleksiireshetov/ai-engineering-playbook/main/templates/project-context.md
```

2. Create a Heartbeat folder and pull templates:

```bash
# Create feature folder
mkdir -p docs/features/your-feature-name && cd docs/features/your-feature-name

# Pull templates
curl -sO https://raw.githubusercontent.com/oleksiireshetov/ai-engineering-playbook/main/templates/idea-brief.md
curl -sO https://raw.githubusercontent.com/oleksiireshetov/ai-engineering-playbook/main/templates/decisions.md
curl -sO https://raw.githubusercontent.com/oleksiireshetov/ai-engineering-playbook/main/templates/task-breakdown.md
```

3. Follow the [lifecycle](lifecycle.md) and log what happened:

```bash
curl -sO https://raw.githubusercontent.com/oleksiireshetov/ai-engineering-playbook/main/templates/heartbeat-log.md
```

## What's Inside

### Lifecycle: The Heartbeat

The core of the playbook. A repeating delivery cycle with stages, steps, gates, and rules.

| File | What | When to Read |
|---|---|---|
| [lifecycle.md](lifecycle.md) | Full lifecycle reference | During work |
| [lifecycle-overview.md](lifecycle-overview.md) | Simplified one-pager | Share for review / onboarding |

### Templates

Copy these into your project. Fill them in as you go through the lifecycle.

| File | Stage | Purpose |
|---|---|---|
| [project-context.md](templates/project-context.md) | All stages | Living project context — start here |
| [idea-brief.md](templates/idea-brief.md) | THINK | Write your brief |
| [decisions.md](templates/decisions.md) | THINK | Architecture decisions + NFR check + mode selection |
| [task-breakdown.md](templates/task-breakdown.md) | THINK | Break feature into Heartbeats |
| [backlog.md](templates/backlog.md) | THINK | Deferred items from stress-test and decisions |
| [heartbeat-log.md](templates/heartbeat-log.md) | BUILD + REVIEW + LEARN | Log each Heartbeat |

## Principles

This isn't really about AI. It's about:

- **Decision ownership** — you decide, AI executes
- **Scope control** — small tasks, clear boundaries, kill switch when it's not working
- **Knowledge compounding** — what you learn today makes tomorrow's AI sessions better

AI just forces these truths to the surface faster.

## When Not to Use This

- **Throwaway prototypes and hackathons** — speed matters more than structure
- **Spikes and exploration** — you don't know what you're building yet
- **Solo projects under 3 days** — the overhead isn't worth it
- **Teams under deadline pressure who haven't felt AI quality pain yet** — they'll reject it. Wait until they feel it.

This playbook solves a specific problem: AI-generated code degrading your codebase over time. If that's not your problem yet, you don't need this yet.

## Contributing

This playbook grows from real experience. Theory is cheap — show your data.

Since I am keeping the core templates restricted to stress-tested patterns to avoid "Context Rot," the best way to contribute is via discussion.

- **Discussions:** Open an Issue if you have a question or a different perspective.
- **Data:** If you've used the Decision Log and have metrics, share them in the Issues.

## License

MIT — use it, fork it, make it yours.


