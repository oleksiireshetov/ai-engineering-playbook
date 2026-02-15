# AI Engineering Playbook — Lifecycle

## What Is This

A discipline layer for building software with AI. Not a new SDLC — add it on top of whatever process you already use.

AI changes the speed of code generation, but not the need for discipline. Without structure, AI-driven development produces **context rot** — where the codebase becomes a mess of hallucinations and technical debt.

This playbook keeps the roles clear: AI writes code, you make decisions.

> *A simple bug is one Heartbeat. A complex feature is a series of Heartbeats. The rhythm remains the same: Think, Build, Review, Ship, Learn.*

---

## The Heartbeat

A Heartbeat is one pass through all 5 stages. The depth changes by context, but no stage is ever skipped.

| Spec | Rule |
|---|---|
| **Size** | Target < 300 lines of code change per task. If it looks bigger during THINK, break it down further. |
| **Time** | 1-4 hours from start to finish |
| **Session** | One fresh AI session per Heartbeat — prevents context drift |
| **Golden Rule** | Every Heartbeat completes all 5 stages. Always. |

```
THINK → BUILD → REVIEW → SHIP → LEARN
```

---

## The Backbone: project-context.md

`project-context.md` is the living document that describes your project as it is today: architecture, tech stack, DB schema, API contracts, conventions, known gotchas.

- **THINK** consumes it — AI needs context to give good options
- **BUILD** consumes it — AI needs context to write correct code
- **LEARN** updates it — when the project changed (new tables, endpoints, patterns, gotchas)

Update project-context.md when the project changed — not when a Heartbeat finished. Most Heartbeats won't change it. That's fine.

→ [project-context.md template](templates/project-context.md)

### Context Rot Signals (Early Warning)

Context rot happens silently. If 2 or more of these are true, **stop BUILD and refresh project-context.md** before continuing.

- AI proposes APIs you "almost have" but not quite
- You keep correcting naming conventions mid-session
- Tests pass but behavior feels "off"
- You explain the same thing twice in one Heartbeat
- You're unsure whether the code still matches the brief

These are signals, not failures. Stopping to refresh context is faster than debugging rotten output.

---

## Rules That Don't Bend

| Rule | Why |
|---|---|
| **Brief is no-AI** | If you can't explain it without AI, you don't understand it enough to guide AI |
| **Tasks target < 300 lines** | Focused AI sessions produce better output. 300 is a guideline, not a hard ceiling — if a task needs 350 lines to be done right, that's fine. Don't sacrifice quality or split coherent logic just to hit a number. For full-stack features: split by layer (API = one Heartbeat, UI = another) — mixing BE and FE in one AI session produces worse output. |
| **Describe before rewrite** | AI will silently drop edge cases it thinks are bugs. Describe what code does today in plain language, then rewrite from the description |
| **Automated guardrails always run** | Linting + SAST on every PR. Automated = zero cost to enforce, no excuse to skip |
| **Hotfix THINK is never zero** | 2 minutes to validate root cause. Otherwise you're patching symptoms |
| **Rollback check before deploy** | Know if you can undo it. If you can't — extra review, not less |
| **Heartbeat Kill Switch** | If BUILD exceeds 3× expected time — abort the Heartbeat. Record why in LEARN. Restart as a smaller task or manual implementation. No sunk-cost spirals. |

---

## Do Not Use AI For

AI is strong at many things. These are not negotiable exclusions:

- **One-off emergency SQL fixes in production** — too high risk, too little context
- **Security-sensitive crypto/auth code without prior patterns** — AI guesses at security, it doesn't understand it
- **Performance hot paths without benchmarks** — AI optimizes for readability, not for your SLAs
- **Code you cannot explain line-by-line after review** — if you can't explain it, you can't maintain it

This list protects the team — especially juniors — from blind trust in AI output.

---

## Two Modes of Operation

The 5 stages are always the same. What changes is whether you run them once or in a series.

### Mode A: Single Heartbeat

For bug fixes, hotfixes, small tasks, tech debt items — anything that fits in one Heartbeat.

```
THINK → BUILD → REVIEW → SHIP → LEARN
```

One pass through all 5 stages. SHIP means deploy to production (or main branch). Done.

### Mode B: Multi-Heartbeat Feature

For features that need multiple tasks. A planning layer wraps a series of Heartbeats.

```
┌─────────────────────────────────────────────┐
│ Feature THINK (once)                        │
│  Brief → Stress-Test → Decisions →          │
│  NFR Check → Task Breakdown                 │
│  Output: [Task 1, Task 2, ... Task N]       │
└──────────────┬──────────────────────────────┘
               │
               ▼
┌─────────────────────────────────────────────┐
│ Heartbeat 1 (Task 1)                        │
│  THINK → BUILD → REVIEW → SHIP → LEARN     │
├─────────────────────────────────────────────┤
│ Heartbeat 2 (Task 2)                        │
│  THINK → BUILD → REVIEW → SHIP → LEARN     │
├─────────────────────────────────────────────┤
│ ...                                         │
├─────────────────────────────────────────────┤
│ Heartbeat N (final task)                    │
│  THINK → BUILD → REVIEW → SHIP → LEARN     │
└──────────────┬──────────────────────────────┘
               │
               ▼
┌─────────────────────────────────────────────┐
│ Feature LEARN (once)                        │
│  Retro + heartbeat log + real numbers       │
└─────────────────────────────────────────────┘
```

**Key difference in Mode B:**
- **THINK** inside each Heartbeat is light — re-read context, review how this task fits the plan
- **SHIP** inside each Heartbeat means **merge to feature branch** (integration), not deploy to production
- **SHIP** in the final Heartbeat means **deploy to production**
- **LEARN** inside each Heartbeat — log what happened. Update project-context.md only if the project changed.
- **Feature LEARN** at the end is the full retrospective — where did decisions hold up, where did they break, real numbers

---

## The 5 Stages — Defined by Intent

Each stage has a universal intent. The action scales to the context.

| Stage | Intent | Mode A (single task) | Mode B (task within feature) |
|---|---|---|---|
| **THINK** | Context prep | Why is it broken? What's the fix? | How does this task fit the plan? |
| **BUILD** | Execution | Code the fix | Code the sub-feature |
| **REVIEW** | Verification | Did it fix the bug? | Does it pass the hallucination check? |
| **SHIP** | Integration | Deploy to production | Merge to feature branch |
| **LEARN** | Retention | Why did this bug exist? | Log what happened, update context if project changed |

---

## Stage 1: THINK

You define the problem. AI helps you stress-test it. You make the decisions.

**Stage overview:**

| Input | Output | Key |
|---|---|---|
| Your head → then stress-tested brief + project-context.md + DB schema | idea-brief.md → decisions.md → task-breakdown.md + backlog.md | Brief is no-AI. Stress-test is one round. Everything after is with AI but NO CODE. |

**Steps (full, for Mode A or Feature THINK in Mode B):**

| Step | Input | Output | Key | Time |
|---|---|---|---|---|
| **Write Brief** | Your head | idea-brief.md | No AI, no code. Answer: what, why, who, where, constraints, out of scope. | 10 min |
| **AI Stress-Test** | idea-brief.md + project-context.md | Updated idea-brief.md (gaps fixed) | One round: AI asks numbered questions, you answer by number, AI produces updated brief. Deferred items go to backlog.md. | 10 min |
| **Architecture Decisions** | Stress-tested brief + project-context.md + DB schema | decisions.md | Same AI session. Ask for 2-3 options with pros/cons. NO CODE. You decide. | 20 min |
| **NFR Check** *(gate)* | decisions.md | NFR notes added to decisions.md | Same session. Pressure-test: security, performance, observability, compliance, error handling, rollback. | 5 min |
| **Mode Selection** | decisions.md | Mode A or B selected | Based on scope and architecture, pick mode. If Mode B → continue to breakdown. If Mode A → go to BUILD. | 2 min |
| **Task Breakdown** *(Mode B only)* | brief + decisions | task-breakdown.md | Each task targets < 300 lines. List input/output files. Map dependencies. One task = one Heartbeat. | 15 min |

**The flow:**

```
idea-brief.md (you write, no AI)
  → stress-test (AI challenges, you answer by number, AI updates brief)
  → decisions.md (architecture options + NFR check + mode selection)
  → task-breakdown.md (Mode B only)
```

**THINK inside a Mode B Heartbeat (light):**

> **Mode B Heartbeats do NOT need a separate idea-brief or stress-test. Feature THINK already did that. Heartbeat THINK is just: re-read context + review your task from the breakdown.**

| Step | Input | Output | Key | Time |
|---|---|---|---|---|
| **Review Context** | project-context.md + this task from breakdown | Mental readiness | Re-read context. Check if anything changed since the plan. Adjust approach if needed. | 5 min |

### What THINK looks like at each level

| Level | What you do | What you DON'T do | Time |
|---|---|---|---|
| **Feature THINK** (once per feature) | Brief, stress-test, decisions, NFR check, mode selection, breakdown | Write code | 60 min |
| **Heartbeat THINK** (per task) | Re-read project-context.md, review task from breakdown | New brief, new stress-test, new decisions | 5 min |

→ [idea-brief.md template](templates/idea-brief.md) · [decisions.md template](templates/decisions.md) · [task-breakdown.md template](templates/task-breakdown.md) · [backlog.md template](templates/backlog.md)

---

## Stage 2: BUILD (with guardrails)

AI writes code within your guardrails. One task per session.

**Stage overview:**

| Input | Output | Key |
|---|---|---|
| project-context.md + decisions.md + existing code + one task | Working code | One task per session. Fresh session. Paste real code, not descriptions. |

**Steps:**

| Step | Input | Output | Key | Time |
|---|---|---|---|---|
| **Build** | project-context.md + decisions.md + existing code + one task | Working code | Fresh AI session. Paste real code, real schemas, real error messages. For refactors: describe what code does today before AI rewrites. | 1-3 hrs |

**Guardrails (always active):**

- One task per session — fresh context, no drift
- Paste real code, real schemas, real error messages — not descriptions of them
- `.cursorrules` or system prompts enforce team conventions
- Automated linting + SAST runs on every PR regardless of work type
- For refactors: describe what the code does today in plain language before AI rewrites it
- **Kill Switch:** if BUILD exceeds 3× expected time — abort, record why in LEARN, restart smaller or write it manually

**Where AI is strong:** boilerplate, CRUD, data mapping, test scaffolding, format conversions

**Where AI is weak:** business logic, error handling, cross-service interactions, performance-sensitive code

---

## Stage 3: REVIEW (with quality gates)

AI catches mechanical issues. You catch logic and hallucination issues.

**Stage overview:**

| Input | Output | Key |
|---|---|---|
| Code from BUILD + requirements + decisions | Approved code → PR | AI reviews first, then human. Hallucination check is non-negotiable. |

**Steps:**

| Step | Input | Output | Key | Time |
|---|---|---|---|---|
| **AI Review** | Code from BUILD + decisions.md | Issues list | Ask AI about edge cases, performance at scale, security, missing validation. | 5 min |
| **Human Review** *(gate)* | Code + AI review output + decisions.md | Approved code → PR | Domain logic, business rules, test quality + hallucination check. | 10 min |

**Hallucination check (part of Human Review):**

- [ ] Every import/dependency exists and is the correct version
- [ ] Every internal method/API call actually exists in your codebase
- [ ] No invented config keys, env vars, or endpoints
- [ ] No made-up library methods that look plausible but don't exist
- [ ] Tests assert behavior, not implementation
- [ ] Implicit behavior is documented — defaults, retries, timeouts are explicit
- [ ] Failure modes are explicit — what happens when a dependency is down?

---

## Stage 4: SHIP (integration)

SHIP means integration — the scope of integration depends on context.

**Stage overview:**

| Input | Output | Key |
|---|---|---|
| Approved PR | Integrated + monitored | Point-of-no-return check before any integration. |

| Context | SHIP means |
|---|---|
| Mode A (single task) | Deploy to production |
| Mode B Heartbeat 1..N-1 | Merge to feature branch |
| Mode B final Heartbeat | Deploy to production |

**Steps (for production deploy):**

| Step | Input | Output | Key | Time |
|---|---|---|---|---|
| **Point-of-No-Return Check** *(gate)* | Migration/deploy plan | Go / extra review needed | Are migrations reversible? Data changes recoverable? If no — extra review. | 2 min |
| **Deploy** | Approved PR + rollback plan | Running in production | Env vars, flags, migrations applied, rollback plan documented. | varies |
| **Monitor** | Deployed service | Confidence or rollback | 24hr monitoring window. Extend for AI-generated code in critical paths. | 24 hrs |

**Steps (for feature branch merge):**

| Step | Input | Output | Key | Time |
|---|---|---|---|---|
| **Point-of-No-Return Check** | PR diff | Go / needs rework | Does this break other in-flight Heartbeats? Schema conflicts? | 2 min |
| **Merge** | Approved PR | Merged to feature branch | Verify CI passes on feature branch after merge. | 5 min |

**Production deploy checklist:**

- [ ] Migrations applied / backward compatible
- [ ] Environment variables set
- [ ] Feature flags configured (if applicable)
- [ ] Rollback plan documented and tested
- [ ] Monitoring and alerts configured
- [ ] Team knows what was deployed and what to watch

---

## Stage 5: LEARN (retention)

The stage that makes the cycle compound. Without LEARN, every Heartbeat starts from scratch.

**Stage overview:**

| Input | Output | Key |
|---|---|---|
| What you learned during this Heartbeat | heartbeat-log.md entry + project-context.md (if project changed) | Do it now. Not later. Later means never. |

**Steps:**

| Step | Input | Output | Key | Time |
|---|---|---|---|---|
| **Log** | What happened during this Heartbeat | Entry in heartbeat-log.md | What worked, what didn't, hallucinations caught, numbers. | 5 min |
| **Update Context** | What changed in the project | Updated project-context.md | Only if the project itself changed — new tables, endpoints, patterns, gotchas. Most Heartbeats won't need this. | 3 min |

**The required question before you close LEARN:**

> *What will AI get wrong next time if I don't update context now?*

If you have an answer — put it in project-context.md. If you don't — you're done.

**Feature LEARN (after all Heartbeats, Mode B only):**

| Step | Input | Output | Key | Time |
|---|---|---|---|---|
| **Update Context** | Full feature changes | Updated project-context.md | Broader patterns, architectural changes, new conventions that emerged. | 5 min |
| **Feature Retro** | What happened across all Heartbeats | Entry in heartbeat-log.md | Real numbers. Where did architecture decisions hold up? Where did they break? Would you use AI for this again? | 10 min |

**Do it now. Not "later." Later means never.**

→ [heartbeat-log.md template](templates/heartbeat-log.md)

---

## Scaling by Work Type

Every type uses the same 5 stages. The depth changes, the rhythm doesn't.

| Type | Mode | THINK | BUILD | REVIEW | SHIP | LEARN |
|---|---|---|---|---|---|---|
| **Feature** | B | Feature THINK (full) | Full guardrails | Full gates | Feature branch → prod on final | Heartbeat log + Feature retro |
| **Bug fix** | A | Brief + root cause | Guardrails | Full gates | Deploy to prod | Root cause log |
| **Refactor** | A or B | Decisions + scope boundaries | Guardrails + describe before rewrite | Full gates + before/after metrics | Incremental, flag if risky | Patterns changed |
| **Hotfix** | A | Root cause validation (2 min) | Guardrails (automated checks still run) | Expedited, no test shortcuts | Emergency deploy + extended monitoring | Post-mortem |
| **Tech debt** | A or B | Brief + clear "done" boundary | Guardrails | Full gates | Standard + point-of-no-return check | What was cleaned |
| **Spike/POC** | A | What are we learning? | Relaxed guardrails | Light review | **Don't ship spikes** | Findings only, kill the code |

---
