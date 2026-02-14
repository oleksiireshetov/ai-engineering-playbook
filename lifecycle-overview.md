# AI Engineering Playbook — Overview

> A simple bug is one Heartbeat. A complex feature is a series of Heartbeats.
> The rhythm remains the same: Think, Build, Review, Ship, Learn.

---

## What's a Heartbeat?

The smallest unit of delivery. One task, < 300 lines, 1-4 hours, all 5 stages. Always.

```
context → THINK → BUILD → REVIEW → SHIP → LEARN
   ↑                                         │
   └──────────── project-context.md ─────────┘
```

Context flows in, code flows out, learnings flow back. Every Heartbeat makes the next one smarter.

---

## The 5 Stages

| Stage | Intent | What Happens | Time |
|---|---|---|---|
| **THINK** | Context prep | Write a brief (no AI). Then AI stress-tests it. Pick an approach. Break into tasks. | 10-60 min |
| **BUILD** | Execution | One task, one fresh AI session. Paste real code, not descriptions. Guardrails enforce quality. | 1-3 hrs |
| **REVIEW** | Verification | AI reviews for mechanical issues. Human reviews for logic, business rules, and hallucinations. | 15 min |
| **SHIP** | Integration | Merge to feature branch or deploy to prod. Check if you can roll back first. | varies |
| **LEARN** | Retention | Update project-context.md with what changed. Log what worked, what didn't. | 5-10 min |

---

## Two Modes

**Mode A: Single Heartbeat** — bug fixes, hotfixes, small tasks.
One pass: THINK → BUILD → REVIEW → SHIP → LEARN. Done.

**Mode B: Multi-Heartbeat** — features that need multiple tasks.

```
Macro-THINK (plan the feature, break into tasks)
  → Heartbeat 1: BUILD → REVIEW → SHIP (to branch) → LEARN
  → Heartbeat 2: BUILD → REVIEW → SHIP (to branch) → LEARN
  → ...
  → Heartbeat N: BUILD → REVIEW → SHIP (to prod) → LEARN
Macro-LEARN (feature retro with real numbers)
```

Each Heartbeat's LEARN keeps context fresh for the next task.

---

## 7 Rules That Don't Bend

1. **Brief is no-AI.** If you can't explain it without AI, you can't guide AI.
2. **Tasks < 300 lines.** Bigger = hallucinations and context drift.
3. **Describe before rewrite.** AI drops edge cases it thinks are bugs. Describe first, then rewrite.
4. **Automated guardrails always run.** Linting + SAST on every PR. No exceptions.
5. **Hotfix THINK is never zero.** 2 minutes to validate root cause. Always.
6. **Rollback check before deploy.** If you can't undo it — extra review, not less.
7. **Kill Switch.** BUILD exceeds 3× expected time → abort, log why, restart smaller.

---

## Do Not Use AI For

- Emergency SQL fixes in production
- Security-sensitive crypto/auth code without prior patterns
- Performance hot paths without benchmarks
- Code you cannot explain line-by-line after review

---

## Scales to Everything

| Type | Mode | Key Focus |
|---|---|---|
| Feature | B | Full process, feature flags |
| Bug fix | A | Root cause in THINK |
| Hotfix | A | 2-min THINK, extended monitoring |
| Refactor | A or B | Describe before rewrite |
| Tech debt | A or B | Clear "done" boundary |
| Spike | A | Don't ship it. Findings only. |

---

## Why It Works

This isn't really about AI. It's about:

- **Decision ownership** — you decide, AI executes
- **Scope control** — small tasks, clear boundaries, kill switch
- **Knowledge compounding** — every Heartbeat feeds the next through project-context.md

AI just forces these truths to the surface faster.

---

**Does this match how your team works? What would break? What's missing?**
