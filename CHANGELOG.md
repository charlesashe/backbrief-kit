# Backbrief Kit — Changelog

## 2.3.0 (2026-08-21)

- **`/resume` was renamed to `/pickup`, because typing `/resume` never reached this kit's file.** Claude Code ships a built-in `/resume` that opens a session picker, and it wins the name outright. The kit documented `/resume` in its README, its plugin listing, its session-hygiene rule, and the closing line of `/handoff`, so anyone who followed the instructions got a session picker with nothing explaining why. The command's behavior is unchanged; only the name is. `resume.md` stays in the payload as a signpost that names the replacement.
- **Why the checker never caught it.** A built-in command lives in neither `~/.claude/commands/` nor `~/.claude/skills/`, and those were the only two places `/verify-install` compared against. It reported a clean install with total confidence while a documented command was unreachable. `/verify-install` now checks the built-in namespace as a third case and tells you how to test a name in ten seconds.
- **`/pickup` also gained the read discipline `/resume` never had.** It now reads an append-only decision log by its tail rather than whole. A plain read returns the TOP of a file, so "the last 5 entries" silently became the OLDEST five on any project with a long log, and the session carried on believing it held current context. That failure is silent, which is what made it worth a step of its own.
- Upgrading from 2.2.x: run `/pickup` where you used to run `/resume`. Nothing else changes.

## 2.2.3 (2026-08-19)

- The license said "DRAFT, have an attorney review before first distribution" and was titled "Shiproom Kit License", a product name retired two releases ago. The draft marker was an internal note that shipped by mistake. It now carries the same honest line the paid bundle has carried since 3.2.2: this license has not yet had attorney review, and it will be updated through the free updates channel when it has. No right, restriction, or permission changed.
- The MIT attribution clause pointed at `kit/.claude/skills/`, a path that does not exist in this repository. It now points at `kit-payload/team/skills/`, where the third-party notices actually live. That clause is how anyone finds the MIT notices, so a dead pointer there mattered more than a broken link usually does.
- No change to any agent, command, rule, or skill.

## 2.2.2 (2026-08-18)

- The plugin description no longer counts its own parts. It used to say "12 agents, 8 commands, 10 rules, 4 skills", which is true today and has been wrong before: a stale count string sat live in public for six days earlier this month, and counts move on almost every release. The description now says what the kit does (an orchestrator that plans and routes, a fresh-context verifier that checks work before it ships, project memory that survives across sessions) and leaves the arithmetic to the repo.
- The marketplace entry gained a category (productivity) and a homepage, and the plugin manifest gained a license line pointing at LICENSE.md. These are the fields a directory listing reads.
- No change to any agent, command, rule, or skill. Installing this over 2.2.1 changes metadata only.

## 2.2.1 (2026-08-18)

- `escalation.md` describes the paid bundle's enforcement layer accurately. It had said the layer is "off unless you turn it on", which is wrong for a fresh install: the installer recommends it and turns it on when you state no preference. Only a setup you already run is strictly off-unless-yes. The same sentence also left out that the layer guards the files it lives in, not just outward shell commands.
- The payload version stamp said 2.1.1 while the plugin said 2.2.0. Both now read 2.2.1.

## 2.2.0 (2026-08-18)

- `escalation.md` now says plainly what the rule is and is not: the team is instructed to stop before anything outward, a model follows that instruction, and nothing in the kit technically blocks the action. Same policy as before, described accurately.
- The council advisors and the verifier can no longer write files, and the runner can no longer reach the network. A review agent that could quietly edit the thing it was reviewing was never an independent review.

## 2.1.1 (2026-08-15)
- Improved the **handoff-checklist** rule: it now says when it applies (any "continue where we left off" session, before you make claims about state or edit files), adds a step for auto-memory notes while marking them secondary to the files, tells you to correct the memory when it disagrees with a file, and states plainly that the checklist is not optional for multi-step tasks or agent handoffs.
- Why it changed: the shipped rule had lost its trigger condition and its guardrail. A checklist nobody knows when to run is not a checklist.
- Rule text only. Item counts are unchanged at 12 agents, 8 commands, 10 rules, 4 skills.

## 2.1.0 (2026-08-14)
- New command **/grade-idea**. Give it a sentence or two (what it is, who pays, any numbers you already have) and it runs the same five advisors from /council against the public six-dimension rubric, no plan document required. It returns a scorecard: a score per dimension, the average, the 8.5 pass line, a letter grade, and the lowest-scoring dimension, or the tied set, named plainly.
- This is a stress-test, not a certification. The command says so every run: a pass means no confident weakness was left un-named, not that the idea will work. A thin description caps what can be scored, and the scorecard names the gaps instead of manufacturing six confident numbers to fill the space.
- Item counts are now 12 agents, 8 commands, 10 rules, 4 skills.

## 2.0.1 (2026-08-13)
- `/backbrief-kit:setup` (and the installed `/setup`) now close with one optional line: a plugin install never asks for an email, so the kit has no way to tell you when a new version ships. If you want update notices, the form at backbrief.ai/get-the-kit is the update list. Said once, and a no is a no.
- Fixed a stale product-name reference in this plugin's setup instructions: an upgrade-detection line said "Backbrief Kit" where it meant the older "Shiproom Kit" heading.
- Item counts unchanged: 12 agents, 7 commands, 10 rules, 4 skills.

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
