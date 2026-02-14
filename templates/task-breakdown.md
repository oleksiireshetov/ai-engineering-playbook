# Task Breakdown

**Stage:** THINK • **Version:** 0.3

**Input:** idea-brief.md + decisions.md

**Output:** Ordered list of Heartbeats with dependencies

**Protocol:** Step 4 • 15 min • With AI • Mode B only

> **CORE PRINCIPLE**
>
> Each task = one Heartbeat. Target < 300 lines. Don't sacrifice quality to hit the number.

---

### Prompt

Feed this to the AI to generate the initial list:

```text
Based on this brief and architecture decisions, break this into ordered tasks. Each task: what it does, input files, output files, dependencies on other tasks, estimated lines. Target each task under 300 lines but don't sacrifice quality or split coherent logic just to hit the number. One task = one AI session.
```

> **Full-stack features:** split by layer. API = one Heartbeat, UI = another. Mixing backend and frontend in one AI session produces worse output — the context is too broad.

> **300 lines is a guideline, not a hard ceiling.** If a task naturally needs 350 lines to be done right — that's fine. Don't split a coherent piece of logic into two awkward tasks just to hit a number. The goal is focused AI sessions, not line counting.

## Tasks

### Task 1: [Name]

**What:** [What this task delivers]
**Input files:** [Which files the AI session needs]
**Output files:** [Which files will be created or changed]
**Depends on:** None
**Estimated lines:** [target < 300]
**Done when:** [How you know it's complete]

### Task 2: [Name]

**What:**
**Input files:**
**Output files:**
**Depends on:** Task 1
**Estimated lines:**
**Done when:**

### Task 3: [Name]

**What:**
**Input files:**
**Output files:**
**Depends on:** Task 1, Task 2
**Estimated lines:**
**Done when:**

*(add more tasks as needed — each task becomes one Heartbeat)*

## Dependency Map

```
Task 1 ──→ Task 2 ──→ Task 4
              │
              └──→ Task 3 ──→ Task 5
```

## Notes

[Risky tasks, tasks needing specific reviewer, shared context across tasks]

---

**Author:** [name] · **Date:** [YYYY-MM-DD]
