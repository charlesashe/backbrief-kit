---
description: Check that the kit is installed correctly and report a plain pass/fail list. Safe to run any time.
---

Run VERIFY-INSTALL when the owner wants to confirm the kit is wired up (or when anything feels off after an install or update).

1. Check each item and print a one-line result per row, pass or fail, no jargon:
   - `.claude/agents/` — expect 12 agent files (7 core + 5 advisors); name any that are missing.
   - `.claude/commands/` — expect critique, council, handoff, resume, setup, verify-install.
   - `.claude/rules/` — expect 10 rule files; name any missing.
   - `.claude/skills/` — expect stop-slop, sop-builder, competitive-analysis, content-repurposer, each with a SKILL.md, plus THIRD-PARTY-LICENSES.md.
   - Root `CLAUDE.md` present (global `~/.claude/` install or this project).
   - Project folders: `context/strategy/` (with the two strategy files), `inputs/`, `outputs/`, `workflows/`.
   - Common mistake check: look for a nested `.claude/.claude/` folder — if found, say plainly that the copy went one level too deep and offer to fix it by moving the contents up.
2. If the Business OS pack is also installed, additionally check: cmo, cfo, web, ops agents; intake, plan, grade, approve commands; ceo-gate, grading, skill-routing-business rules; 17 skills in `.claude/skills/` beyond the base four; `templates/` and `workflows/` pack files.
3. End with one of exactly two verdicts:
   - "Everything checks out. If you have not run /setup yet, that is the next step."
   - "N items need attention" — followed by the shortest fix for each (offer to do the fixes yourself; get a yes before moving or copying anything).

Never modify anything without the owner's yes. This command only reads, reports, and offers.
