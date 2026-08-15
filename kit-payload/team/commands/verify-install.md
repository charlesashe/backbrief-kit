---
description: Check that the kit is installed correctly and report a plain pass/fail list. Safe to run any time.
---

Run VERIFY-INSTALL when the owner wants to confirm the kit is wired up (or when anything feels off after an install or update).

Check the payload where it was actually installed: the global `~/.claude/` for a global install, or this project's `.claude/` for a per-project install. If both hold agents, the project copy is the one in force here, so check that one, but report both and their `.claude/VERSION` values. Two different versions in the two locations is worth saying out loud: this project is running the project copy, and the global one is what every other project gets. Say which you checked either way. The project-folder rows below always refer to the current project.

Start by reporting the installed version from `.claude/VERSION` (for example "Backbrief Kit 2.0.0", or an older stamp like "Shiproom Kit 1.5.0"). If that file is missing but agents are present, the install predates version stamping: say so and offer to add it. If `.claude/` is missing entirely in a project that has `context/` and `outputs/` folders, that is the classic moved-or-copied-project failure: `.claude` is hidden, so it is easy to leave behind when a project is moved, copied, zipped, or synced. Say that plainly, because the symptom otherwise looks like the team silently forgetting how to work, and offer to reinstall from the download.

1. Check each item and print a one-line result per row, pass or fail, no jargon:
   - `.claude/agents/` — expect 12 agent files (7 core + 5 advisors); name any that are missing.
   - `.claude/commands/` — expect next, critique, council, grade-idea, handoff, resume, setup, verify-install (8 total).
   - `.claude/rules/` — expect 10 rule files; name any missing.
   - `.claude/skills/` — expect stop-slop, sop-builder, competitive-analysis, content-repurposer, each with a SKILL.md, plus THIRD-PARTY-LICENSES.md.
   - Root `CLAUDE.md` present (global `~/.claude/` install or this project).
   - Project folders: `context/strategy/` (with the two strategy files), `context/reference/`, `inputs/`, `outputs/`, `workflows/`. A missing `context/reference/` is a soft fail on installs from before 1.3.0: offer to create it.
   - `.claude/memory/decisions.md` present in the project (the decision log the decision-log rule writes to). If missing, offer to create it from the scaffold.
   - `.claude/memory/preferences.md` present. Missing is a soft fail on installs from before 1.4.0: say /setup will write it, or offer to create it from the scaffold now.
   - Project root `CLAUDE.md`: if it exists but never mentions the kit or the orchestrator, the project predates this install. Say so in one line and offer to add a short pointer section; never rewrite their file. Separately, if it still holds scaffold placeholders such as `<PROJECT NAME>`, it has never been filled in: that is not a broken install, but say so and point at /setup, because mentioning the product is not the same as being set up.
   - Common mistake check: look for a nested `.claude/.claude/` folder — if found, say plainly that the copy went one level too deep and offer to fix it by moving the contents up.
2. If Backbrief Business OS is installed instead of this kit, you will also see the cmo, cfo, web, and ops agents, the /intake, /plan, /grade, and /approve commands, the ceo-gate and grading rules, and 21 skills rather than four. That is expected: Backbrief Business OS is the complete bundle and includes everything here.
3. End with one of exactly two verdicts:
   - "Everything checks out. If you have not run /setup yet, that is the next step."
   - "N items need attention" — followed by the shortest fix for each (offer to do the fixes yourself; get a yes before moving or copying anything).

Never modify anything without the owner's yes. This command only reads, reports, and offers.
