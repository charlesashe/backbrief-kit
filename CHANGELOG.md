# Backbrief Kit — Changelog

## 2.0.0 (2026-08-10) — the rename release

- The kit is renamed: the Shiproom Kit is now the **Backbrief Kit**, this plugin is now **backbrief-kit** in the **backbrief** marketplace, and the site moved to backbrief.ai (shiproom.ai redirects there). Same files, same system, new name; item counts unchanged (12 agents, 7 commands, 10 rules, 4 skills).
- New installs: `/plugin marketplace add charlesashe/backbrief-kit`, then `/plugin install backbrief-kit@backbrief`, then `/backbrief-kit:setup`. The old `charlesashe/shiproom-kit` marketplace address still resolves (GitHub redirects it here).
- **Already installed as shiproom-kit@shiproom?** Your installed kit keeps working. To move to the new plugin name: `/plugin uninstall shiproom-kit` (this does not touch the kit files it installed into your projects), then add and install as above. Running `/backbrief-kit:setup` afterwards upgrades your installed kit files in place — it recognizes the old Shiproom Kit stamp and never touches anything you wrote.

## 1.5.0 (2026-08-09)
- Your knowledgebase is now a first-class part of the kit. `/setup` asks for the documents AND the links the team should work from — digital books, guides, product docs, a docs site, a Notion page — copies the files into `context/reference/`, and records every source in a new index, `context/reference/SOURCES.md`, with a note on when to use it. Links finally have a home: they live as rows in that index.
- The researcher reads the index first and cites your sources, by filename or URL, ahead of general knowledge.
- `/next` now notices an empty knowledgebase and offers once, in one line, to file whatever you have. It never nags and never blocks anything.
- You do not have to wait for `/setup`: naming a document or link in chat is enough to have it filed and indexed.
- Existing projects get the index automatically on update: the scaffold copy adds `SOURCES.md` without touching anything you wrote.
- Installer clarity fixes found in rehearsal: version comparison across the two differently-formatted VERSION files is now spelled out, the scaffold's hidden memory folder is named so no copy method drops it, memory backups are named for the version being replaced with the time included, skill folders are replaced wholesale on upgrade so dropped files do not linger, and you are no longer offered the same pointer block twice.

## 1.4.4 (2026-08-07)
- If a newer download is sitting in the same folder as the one you opened, the installer now tells you before it copies anything and asks whether you meant to use that one. Previously you would only have found out at the very end.

## 1.4.3 (2026-08-07)
- The install now cleans up after itself, with your permission. It finds older unzipped downloads sitting beside it, old memory backups in your project, and the installer folder you are currently in, shows you the list, and deletes only what you say yes to. Nothing in a project folder is ever a cleanup candidate, and if nothing has piled up it says nothing at all.

## 1.4.2 (2026-08-07)
- The installer now opens by telling you which version it is, so opening an older unzipped folder by mistake is obvious immediately.
- It also refuses to install an older download over a newer install, unless you say outright that you want to roll back.
- "Updating an existing install" now says what actually works: unzip, open Claude Code in the new folder, type `install this`.

## 1.4.1 (2026-08-07)
- Fixed, and it matters if you installed before version stamping existed: updating an install that has no `.claude/VERSION` file no longer mistakes the kit's files for your own work and skip the entire update. The installer now recognises its own earlier payload by what is actually in the folder, tells you what it is about to replace, and asks first. Anything you wrote is still never touched.
- The stale-duplicate warning no longer fires on every other project sitting beside yours in the same parent folder, only on a probable copy of the same one.
- The install never copies `.git/` or the installer's own documentation into your project.

## 1.4.0 (2026-08-07)
- New command **/next**. It reads your project files, tells you where you stand and what to do next, and offers to run it. Because it works from what is on disk rather than from the conversation, it is correct in a brand new chat. If you are ever unsure what to do, that is the one to type.
- /setup asks how much you want the team to drive and records it in `.claude/memory/preferences.md`: `guided` (offers each step, the default), `manual` (names the step, runs nothing), or `auto-prep` (runs setup without asking). That file lives in memory/, which the payload never overwrites, so the setting survives every future update.
- No setting ever skips an outward action or a /council run. Those always stop for you.
- Command count is now 7 (was 6).

## 1.3.1 (2026-08-07)
- Install is now one instruction. Open Claude Code in the unzipped folder and type "install this". A new root CLAUDE.md carries the install procedure, so Claude reads it and runs the install: it asks which project folder you want the team in, asks global or one project, copies both pieces, runs /verify-install, and offers /setup. Nothing to copy out of the README, no PATH placeholder to edit.
- The explicit paste message is kept as a fallback for anyone who prefers to be literal.
- Fixed: every remaining copy command in INTEGRATION.md is now non-destructive. Two PowerShell examples used Copy-Item, which silently overwrites, and one macOS example used mv, which removed the file from your download.
- Fixed: the install no longer assumes the /verify-install and /setup commands are available in the installer folder. They live in your project, so the installer runs the checks directly and hands you off to your project for setup.
- Naming: the payload now calls itself the Shiproom Kit throughout. Files that landed in your project still said Agent OS Kit, the name it shipped under before the rename.
- New: the install stamps `.claude/VERSION`, so a later install can tell it is updating its own files rather than looking at yours. Reinstalling over an older kit now actually updates it instead of skipping every file and reporting success. Installing over Business OS is refused, since that is the complete system and this would be a downgrade.
- `/verify-install` now opens by reporting the installed version, and it recognizes the case where `.claude/` was left behind when a project was moved, copied, or synced. That folder is hidden, so it goes missing quietly and the only symptom is the team appearing to forget how to work.
- Jurisdiction routing: any claim about what is legal, licensed, required, disclosed, or taxed in a named place now goes through the researcher before it can reach an advisor score or guidance you might act on. /council runs that check before the advisors, and anything unchecked gets labelled an unverified local-law assumption instead of being reasoned past.
- Blended rules of thumb across mixed segments are now called out rather than applied silently.
- Install: warns you when a stale duplicate of your project sits one level up or down; recommends per-project when the folder already has its own .claude/; backs up .claude/memory/ before an update replaces anything; and states plainly that memory, context, outputs, workflows, and your own CLAUDE.md are never touched.

## 1.3.0 (2026-08-05)
- New: reference library. The scaffold now includes `context/reference/` for the documents you trust (product docs, standards, style guides, books you own). The researcher checks it first and cites from it; owner documents outrank general knowledge. Less generic filler, more answers grounded in your sources.
- /setup now asks whether you have reference material and offers to place it (or fetch freely available documents you point at) during the interview.
- /verify-install checks for the reference folder and offers to create it on older installs.

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

Download the current version, unzip it, open Claude Code in the newly unzipped folder, and type **install this**. It will tell you which version it is, notice what you already have, say what it is about to replace, and ask before it does. Your own files are never touched and your memory folder is backed up first.

If you still have the folder from a previous download, delete it or move it aside before you start. The only thing that goes wrong here is opening the old one by mistake, and the installer now names its own version in its first line so you can catch that immediately.
