# AI Engineering Playbook 💓

> v0.1.0 — Early draft. Feedback welcome.

A step-by-step playbook for building software with AI. Not a new SDLC — a discipline layer you add on top of whatever process you already use.

## Why This Exists

AI coding tools are everywhere. Engineering discipline for using them isn't.

Most teams are figuring it out as they go — prompting, generating, reviewing, shipping — without a shared process for how AI-assisted work should flow. The result is predictable: fast output, slow cleanup, growing tech debt that nobody fully understands.

The options that exist today don't quite fit:

- **Vendor guides** tell you how to set up Copilot or Cursor — tooling setup, not engineering process
- **Enterprise frameworks** like Amazon's AI-DLC replace your entire SDLC — too heavy to adopt incrementally
- **Best practice blogs** say "review AI code carefully" — true, but not actionable

What's missing is a lightweight lifecycle that plugs into your existing workflow and addresses the actual failure modes of AI-assisted development: **context rot** (AI losing track of your codebase), **hallucinations** (code that looks right but calls things that don't exist), **scope creep** (AI happily generating beyond what was asked), and **sunk-cost spirals** (fighting the AI instead of writing it yourself).

This playbook fills that gap. Built from real production experience with AI-assisted development in a regulated, high-volume environment — not from theory.

## The Problem

AI changes the speed of code generation, but not the need for discipline. Without structure, you get **context rot** — a codebase full of hallucinations and tech debt that no one fully understands.

## The Solution: The Heartbeat

Every piece of work — feature, bug fix, hotfix, refactor — follows the same rhythm:

```
context → THINK → BUILD → REVIEW → SHIP → LEARN
   ↑                                         │
   └──────────── project-context.md ─────────┘
```

A Heartbeat is one task: < 300 lines, 1-4 hours, all 5 stages. A bug fix is one Heartbeat. A feature is a series of Heartbeats. The rhythm stays the same.

## Quick Start

1. Copy `templates/project-context.md` into your project root and fill it in
2. On your next task, follow the [lifecycle](lifecycle.md)
3. Use the [templates](templates/) for each stage
4. Log what happened in [decision-log.md](templates/decision-log.md)

## What's Inside

| File | What | When to Read |
|---|---|---|
| [lifecycle.md](lifecycle.md) | Full lifecycle — stages, steps, gates, rules | Reference during work |
| [lifecycle-overview.md](lifecycle-overview.md) | Simplified one-pager | Share for review / onboarding |
| [templates/project-context.md](templates/project-context.md) | Living project context | Start here, update every Heartbeat |
| [templates/idea-brief.md](templates/idea-brief.md) | THINK: write your brief | Step 1 of every task |
| [templates/decisions.md](templates/decisions.md) | THINK: architecture decisions + NFR check | Before BUILD |
| [templates/task-breakdown.md](templates/task-breakdown.md) | THINK: break feature into Heartbeats | Mode B features |
| [templates/decision-log.md](templates/decision-log.md) | LEARN: log what happened | After every Heartbeat |

## Principles

This isn't really about AI. It's about:

- **Decision ownership** — you decide, AI executes
- **Scope control** — small tasks, clear boundaries, kill switch when it's not working
- **Knowledge compounding** — every Heartbeat feeds the next through project-context.md

AI just forces these truths to the surface faster.

## Contributing

This playbook is in early development. Feedback, ideas, and real-world experience welcome — open an issue.

## License

MIT — use it, fork it, make it yours.
