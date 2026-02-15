# Changelog

## 0.4.0 — 2026-02-15

- replace Macro-THINK/LEARN with Feature THINK/LEARN
- simplify Heartbeat diagram (remove circular project-context arrow)
- fix project-context update rule: update when project changed, not every Heartbeat
- split LEARN into Log (always) + Update Context (only if project changed)
- delete lifecycle-overview.md (README covers intro, lifecycle.md covers the rest)
- remove context rot checkboxes (plain bullets)
- remove Hidden Dangers table
- rewrite README intro (drop vendor comparisons, sharpen failure modes list)
- fix README principles (remove project-context feedback loop claim)
- delete Coming Soon section from README

## 0.3.0 — 2026-02-14

- restructure THINK flow: stress-test in brief, mode selection in decisions
- merge session-log and decision-log into heartbeat-log.md
- add backlog.md template for deferred items with triggers
- add one-round rule for stress-test (no infinite Q&A loops)
- add predefined deferral answer pattern
- add pruning protocol to project-context.md
- add when not to use this
- change NFR status from emojis to PASS / WARN / N/A
- standardize template headers (Stage, Version, Input, Output, Protocol)
- add code blocks for all AI prompts (copy-paste safe)
- use relative links (./file.md) across all templates
- simplify Contributing section
- bump all template versions to 0.3

## 0.2.0 — 2026-02-14

- add prompt examples to all templates (stress-test, decisions, NFR check, task breakdown)
- add version, input/output metadata to all templates
- add Scale section to project-context.md (users, DAU, requests/day, forecast)
- add session-log.md template for logging AI sessions
- clarify Macro-THINK vs Heartbeat THINK distinction in lifecycle
- improve field descriptions in idea-brief (Who, Constraints, Out of Scope, Success Criteria)
- update 300-line rule: guideline not ceiling, quality over line counting
- add full-stack split guidance (API and UI = separate Heartbeats)
- add "same session" note for NFR check in decisions template

## 0.1.0 — 2026-02-12

- initial playbook structure: lifecycle, templates, and overview
