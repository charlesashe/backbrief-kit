# Shiproom Kit — Changelog

## 1.3.0 (2026-08-05)
- New: reference library — a context/reference/ scaffold folder for source material you own or may freely use; the researcher checks it first and reports conflicts instead of guessing (owner docs beat general knowledge).
- /setup now asks about reference material and offers to place it for you.
- /verify-install checks the reference folder, with a soft pass for installs made before 1.3.0.

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

## Updating an existing install (plugin route)
Run `/plugin update`, then `/shiproom-kit:setup` again — setup only adds what's new and never touches your context/, outputs/, or memory files. (Zip installs update differently; see the README inside the zip download.)
