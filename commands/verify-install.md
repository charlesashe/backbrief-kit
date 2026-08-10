---
description: Check a Backbrief Kit install and report a plain pass/fail list. Reads only; never changes anything without a yes.
---

Check the user's Backbrief Kit installation (global `~/.claude/` and/or this project's `.claude/`) and report one line per item, pass or fail, no jargon:

- 12 agent files (7 core including orchestrator and verifier, 5 advisors); name any missing.
- Commands: critique, council, handoff, next, resume, setup, verify-install.
- 10 rule files; name any missing.
- 4 skills (stop-slop, sop-builder, competitive-analysis, content-repurposer), each with SKILL.md, plus THIRD-PARTY-LICENSES.md.
- Project scaffold: context/strategy/ with the two strategy files, inputs/, outputs/, workflows/.
- Common mistake: a nested `.claude/.claude/` or a `.claude/team/` folder — if found, explain plainly and offer to fix by moving contents up.

If the kit is not installed at all, say so and point to `/backbrief-kit:setup`. If the Backbrief Business OS pack is present, also check its 4 agents, 4 commands, 3 rules, and 17 skills. End with either "Everything checks out" (plus a /setup pointer if the strategy files are still templates) or "N items need attention" with the shortest fix for each. Never modify anything without the user's yes.
