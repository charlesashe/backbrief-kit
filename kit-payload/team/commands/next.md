---
description: Show where this project stands and what to do next, then offer to run it. Safe to run any time.
---

Run NEXT whenever the owner types `/next`, asks what to do now, or sounds unsure of where they are. This is the command someone runs when they are lost, so answer plainly and never make them feel behind.

## 1. Read, do not remember

Work out the stage from what is actually on disk, never from this chat's history. The owner may be in a brand new session (session-hygiene rule), so the files are the only reliable source.

Read `.claude/memory/preferences.md` for `guidance`. If the file is missing, treat guidance as `guided` and offer to create it at the end.

## 2. Work out the stage

First match wins:

| What you find | Where they are | Next step |
|---|---|---|
| `context/strategy/` missing, or both files still template placeholders | not set up | `/setup` |
| set up, nothing in `workflows/active/` and nothing in `outputs/` | ready to work | state a goal in plain words; the orchestrator plans it, routes it, and gates the result through the verifier |
| a plan in `workflows/active/` with units not yet done | mid-run | the next unfinished unit in that plan |
| work in `outputs/` and the plan's units are done | finished a piece | `/handoff` to close the session cleanly, then `/pickup` next time |

If `/critique` or `/council` would genuinely help right here, mention it as optional and say why in one line. Never insert them as a required step and never run them without being asked.

An artifact only counts as done if it has the owner's real content in it. A template that was created and saved but never filled in does not advance the stage: treat it as still missing, say so plainly, and offer to finish it. This applies to the brief, the plan, and the scorecard, not just the strategy files.

While you are reading, glance at the knowledgebase. If the project is set up but `context/reference/` holds nothing beyond the shipped templates (no files added, no real rows in `SOURCES.md`, the example rows do not count), add one line to your answer: "No knowledgebase registered yet: if you have guides, docs, or links the team should work from, name them and I will file them." Say it once, as an aside, never as a required step, and drop it entirely once the owner has sources registered or has declined in this session.

## 3. Say where they are

Two short lines, plain language, no jargon: where they are, and what comes next and why it matters. Name the file that told you, so the owner can check you. If a previous step produced something they have not looked at, offer to show it before moving on.

## 4. Then act on the guidance preference

- **`manual`**: name the next step and stop. Run nothing.
- **`guided`** (the default): offer to run the next step now and wait for a yes. One word is enough.
- **`auto-prep`**: run the next step without asking, but ONLY when it is `/setup`. Announce what you are running. Stop at everything else, including starting work on a goal.

Run at most ONE step per invocation, whatever the mode. When it finishes, stop, re-read the files, and report the new stage. Never chain steps together in a single run.

## 5. Never automatic, whatever the preference says

`auto-prep` does not relax any of these. If the next step is on this list, stop and hand the decision to the owner, and say plainly that you are stopping because the decision is theirs.

1. **Every outward action stops for the owner**: sending, publishing, spending, granting access (escalation rule). Silence is never approval.
2. **Anything that results in a `/council` run is never started unprompted**, however it is phrased. It dispatches five advisors and costs real tokens.
3. **Nothing the owner wrote is deleted or overwritten** without an explicit yes.
4. **Jurisdiction-specific legal, tax, or licensing claims** go through the researcher before they appear in output (agent-routing rule).

## 6. Close

End with the one thing to do next, and remind them once that `/next` works any time they are unsure. If they want a different pace, tell them they can say so and you will update `.claude/memory/preferences.md`.
