# Shiproom Kit — Changelog

## 1.2.0 (2026-08-02)
- New: /setup command — first-time setup interview writes the context files for you; no manual file editing.
- New: /verify-install command — plain pass/fail install check, including the common copied-too-deep mistake.
- New: first-run greeting — on a fresh install the team introduces itself and offers /setup.
- New: install docs lead with the one-paste assisted install (Claude does the copying, same on Windows and Mac); manual copying is now the alternative, with a Mac hidden-folder note.
- Also available as a Claude Code plugin: /plugin marketplace add charlesashe/shiproom-kit

## 1.1.0 (2026-08-01)
- Four bundled skills (stop-slop, sop-builder, competitive-analysis, content-repurposer) with attribution; skill-routing rule; license files.

## 1.0.0 (2026-07-14)
- Launch: 12 agents, 4 commands, 9 rules, project scaffold, /handoff + /resume project memory.

## Updating an existing install
Unzip the new download, open Claude Code in the unzipped folder, and paste: "Update my Shiproom Kit from this folder: compare kit/.claude/ against my installed copy, show me what changed, and apply the update without touching my context/, outputs/, or memory files."
