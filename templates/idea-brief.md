# Idea Brief

**Stage:** THINK • **Version:** 0.3

**Input:** Raw idea

**Output:** Scoped brief for AI stress-test

**Protocol:** Step 1 • 10 min • Human Only • No AI / No Code

> **CORE PRINCIPLE**
>
> If you can't explain it without AI, you don't understand it enough to guide AI.

---
## Concept (what)

[One sentence. What are you building or changing?]

## Why

[Why does this matter? What problem does it solve? Who asked for it?]

## Who Will Use This

[Who are the users of this feature? If no users yet — who will be first? If solo project with no users — write "Internal/solo, no external users yet."]

## Where

[Which services, repos, or components are involved?]

## Constraints

[What limits your options? Tech debt, third-party API limits, infra limitations, compliance, budget. Write "None" if truly unconstrained.]

## Out of Scope

[What will people assume is included but isn't? Be explicit to prevent scope creep. If unsure — write "None — to be challenged during AI stress-test."]

## Success Criteria

[How will you test that this works? Be specific and testable. E.g., "When test fails, configured webhook receives POST within 30 seconds with correct payload." Not "webhooks work."]

---

## Next Step: AI Stress-Test

Feed this brief + `project-context.md` to AI with this prompt:

```text
Stress-test this idea brief. Challenge it, assess edge cases, what am I missing, trade-offs. Use numbered questions so I can reply by number. After I answer, provide an updated version of the brief.
```

**One round.** AI asks questions, you answer by number, AI produces updated brief. If new questions emerge from answers — don't loop. Capture them in [backlog.md](./backlog.md) with a trigger for when to revisit.

**To defer items during stress-test, answer:**

```text
Not in scope. Add to backlog.
```

AI will capture it. Full deferral format is in [backlog.md](./backlog.md).

AI will incorporate your answers and produce an updated, stress-tested version of this brief. That updated version becomes the input for [decisions.md](./decisions.md).

The updated brief replaces this file's content — one file, updated in place.

---

**Author:** [name] · **Date:** [YYYY-MM-DD]
