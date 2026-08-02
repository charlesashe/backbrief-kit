---
description: First-time setup interview. Fills in the two context files by asking questions, so nobody has to edit files by hand.
---

Run SETUP once per project, right after installing the kit. It replaces "go edit these files" with a short conversation.

1. Check the install first. Confirm these exist and say so in one line each (a green check or a plain statement of what is missing):
   - `.claude/agents/` with the orchestrator and verifier present
   - `.claude/commands/` with critique, council, handoff, resume
   - `.claude/rules/` with at least the escalation rule
   - `.claude/skills/` (four bundled skills)
   - `context/strategy/`, `inputs/`, `outputs/`, `workflows/` folders
   If the scaffold folders are missing, offer to create them now (copy the layout from the kit's scaffold, or create empty folders with the standard names) before continuing.
2. Interview the owner, one question at a time, in plain language. Do not ask everything at once:
   - "What is this project, in a sentence or two?"
   - "What are you trying to get done in the next few weeks?"
   - "Anything I should never do without asking you first, beyond the standard stops (spending, sending, publishing, deleting)?"
   - "Anything already done or decided that I should know about?"
3. Write the answers into the files, in the owner's own words where possible:
   - `context/strategy/current-state.md` — one paragraph: what the project is and where it stands.
   - `context/strategy/current-priorities.md` — a ranked list of 3-5 priorities from their answer.
   - Extra constraints go in `current-priorities.md` as a "House rules" line, and anything already-decided becomes the first entry in `.claude/memory/decisions.md` (create the file if needed).
4. Read the two files back to the owner in under 100 words and ask if anything is wrong. Fix what they correct.
5. Close with exactly this orientation: "Setup is done. State a goal in plain words and the team will plan it, build it, and verify it. Useful commands: /critique to stress-test an idea, /council for a five-advisor debate, /handoff to end a session, /resume to start the next one."

Keep the whole thing under ten minutes. No jargon. If the owner says "skip" to any question, write a sensible placeholder and mark it with "(fill in later)".
