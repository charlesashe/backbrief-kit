---
description: Start a new chat with full project memory. Read the files, say where things stand, name the next action, then wait.
---

Run RESUME as the first command in a new chat on an existing project.

1. Read, in order: the root CLAUDE.md; context/strategy/current-state.md and current-priorities.md; the last 5 entries of .claude/memory/decisions.md; the most recent file in .claude/memory/handoffs/ (if the folder exists); any plan in workflows/active/ (if it exists).
2. Summarize in under 200 words: where the project stands, what changed most recently, and the single next action (taken from the latest handoff brief when one exists).
3. Files win over recollection (handoff-checklist rule). If two files disagree, say so plainly and ask one question instead of guessing.
4. Do not start work until the owner confirms the next action or redirects.
