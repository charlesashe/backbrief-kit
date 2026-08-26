# Skill Routing (Backbrief kit)

The kit's bundled skills live in `.claude/skills/`. Claude Code discovers them automatically: no install step. Agents load the matching skill before producing work in its domain.

| Skill | Primary agent | When |
|---|---|---|
| stop-slop | reviewer, verifier | Every prose artifact (posts, emails, docs) gets a stop-slop pass before it is called done. This is a standing quality gate, not an on-request tool. |
| sop-builder | builder | Turning repeatable work into SOPs, checklists, or handoff documents. |
| competitive-analysis | researcher | Competitor mapping, offer comparison, positioning-gap research. |
| content-repurposer | builder | Converting one finished piece into multiple platform formats. |

Rules of use:

- Skills are procedures, agents are roles. The agent stays accountable for the output; the skill shapes how it is produced.
- stop-slop's rules are intentionally strict. When the owner's real voice uses a pattern it bans, the owner's voice wins: note the exception in `context/` rather than fighting the gate every run.
- Competitor facts age fast. competitive-analysis output must date-stamp claims and mark anything unverified.
- These skills are third-party MIT work, bundled with attribution (see `.claude/skills/THIRD-PARTY-LICENSES.md`). Keep each skill folder's LICENSE file when copying the kit into projects.
