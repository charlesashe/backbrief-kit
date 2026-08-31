# Backbrief Kit: Changelog (formerly the Shiproom Kit)

## 2.10.0 (2026-08-31)

- **Hallucination hardening: the trigger taxonomy and the citation-fidelity spot-check.**
  Grounded in Anthropic's circuit-tracing research (refusal is the model's default; a
  known-entity feature suppresses it on partial recognition, and hallucinations are
  misfires of that suppression). Two folds: the constraints rule and the researcher now
  name the high-risk ask class - stats, names, dates, quotes, sources, niche or very
  recent topics - as retrieve-or-tag-unverified, never recall alone. And the verifier
  gains a citation-fidelity step: for a sample of load-bearing cited claims, open the
  source and confirm it says what the artifact claims; unreachable sources (URLs - the
  verifier has no web access by design) are compared against dispatch-supplied excerpts
  or marked SOURCE UNREACHABLE, and verify-before-delivery now tells dispatchers to
  include those excerpts. A real citation attached to a claim its source does not make
  is a CONFIRMED finding.
- **/council's chairman now opens with an actionable verdict line**: GO, HOLD, or NO with one
  sentence of reasoning and a "First move:" drawn from the executor's answer, before the full
  reasoning and next steps. The clash and the blind peer review are unchanged; the one-liner
  compresses the verdict, it never softens a disagreement.
- **/grade-idea gains a reachability trial line and a panel's read.** Advisors now score a
  seventh line - Reachability: a named, plausible way a stranger first finds the idea, from
  the channels and budget the user actually stated - reported beside the rubric and never
  averaged into the grade, the letter, or the pass line. The public rubric stays six
  dimensions; this line is an explicit trial. The scorecard also closes with "The panel's
  read" (pursue as-is / close the gaps first / walk away, drawn only from what the advisors
  argued) and "First move" from the executor. The decision stays the user's.

## 2.9.1 (2026-08-30)

Closes the residuals from the independent re-walk of 2.9.0 as shipped.

- **The reference manifest moved inside the payload folder, so every install path lands it - not just the agent-run one.** 2.9.0 shipped it beside the payload with a special-case copy instruction, which the README's manual copy blocks and the merge path never execute. It now lives in `kit/.claude/`, so all three paths inherit it automatically; the installed location (`.claude/reference-manifest.json`) is unchanged.
- **The collision check is scoped and sees nested commands.** The installer's new collision step now states it is a per-project-install check (on a global install it would compare the folder against itself), and the comparison includes command files in subfolders, which claim their bare names exactly like top-level ones - in the installer and in /verify-install both.
- **/verify-install knows about the plugin channel.** The kit installed as a plugin carries its own copy and version under `~/.claude/plugins/`; the version row now notes it when present, instead of the split report silently covering only the two folder levels.

## 2.9.0 (2026-08-30)

Findings from an independent deep review, every one re-verified on disk before it was fixed.

- **The kit now ships a reference manifest, and three checks that did not exist before hang off it.** `kit/reference-manifest.json` carries the shipped-name rosters, and the installer copies it to `.claude/reference-manifest.json` beside `VERSION`. With it: the installer gains the collision check the paid bundle has had for a while (a same-named command or skill in `~/.claude/` silently overrides the one just installed - now every hit is reported, naming the file that wins), /verify-install reads its rosters from the manifest instead of typed lists that go stale, and both report the common older-global-copy case plainly.
- **Upgrades stop silently deleting the customization our own guide directs.** CUSTOMIZATION.md tells owners to reference their custom agents in the routing rule; the upgrade path then overwrote `rules/` wholesale, so the custom agent survived while the wiring that routed to it vanished, with nothing erroring. The installer now asks before replacing `rules/`, naming `agent-routing.md` specifically, and merges an edited copy forward instead of discarding it.
- **Dead frontmatter keys removed and a stale build artifact deleted.** Two skills carried a `tools: []` key the runtime ignores (skills restrict tools with `allowed-tools`), and two agent definitions (reviewer, runner) had frontmatter that did not parse as YAML - unquoted colons in their descriptions. All fixed. A six-week-old build zip from before the product's rename was found sitting inside the download and is gone; the release gate now refuses to ship build output inside the payload.

## 2.8.1 (2026-08-30)

- **The reviewer now runs the standing stop-slop gate by name.** The routing rule has always said the gate runs at reviewer AND verifier; only the verifier's file said so. The reviewer's definition now loads it explicitly for prose artifacts and says the pass ran.
- **The installer stops treating your global CLAUDE.md as ours.** On a global upgrade, `~/.claude/CLAUDE.md` is now replaced only when its first heading is one of this kit's own; anything else is recognized as your configuration, left alone, and offered the pointer block as an append instead. This matches the paid bundle's long-standing behavior.
- **Two stale strings fixed:** the third-party licenses file was still titled for the retired Shiproom name, and CUSTOMIZATION.md told customizers strong-tier agents "carry no model: line" when they actually pin `model: inherit` - following the old instruction literally would have produced a different frontmatter shape than the kit's own agents use.

## 2.8.0 (2026-08-30)

- **The paid layer is now visible from inside the product, at the moments it matters.** A funnel audit found the free kit's users were never told the paid product exists as something purchasable - one survey respondent believed it was unreleased. Three additions, all pull-not-push: the kit's own CLAUDE.md gains a plain "The paid layer" section (what Business OS adds, one link, and the honest line that nothing in this kit expires or is withheld); /next may add ONE sentence naming the CEO loop when the project's stage is genuinely business-decision territory, under an absolute suppression rule (never on consecutive runs, never as a required step); and typing /intake, /business-plan, /grade, or /approve now gets a two-sentence signpost saying what the command does and that it ships in Business OS, instead of silence. Each signpost also self-checks for the one hazardous case - a global kit shadowing a per-project Business OS install - and offers to remove itself there.
- **Counts left the copy.** "Nine commands" strings were replaced with structural phrasing across the kit's documents, per the standing rule that counts break on nearly every release. /verify-install now expects the four signposts by name and says their presence is not a Business OS install.

## 2.7.2 (2026-08-26)

- **A quarter of the skill library was invisible, and now is not.** content-repurposer's frontmatter did not parse (an unquoted colon in its description), so Claude Code's auto-discovery skipped it silently, and sop-builder and competitive-analysis carried no `description:` field at all - discovery reads nothing else. All three fixed, and /verify-install now parses every SKILL.md's frontmatter so an unparseable skill is a named FAIL instead of a quiet absence.
- **The strong tier's claims are true on disk.** orchestrator, planner, and verifier now pin `model: inherit` (token-discipline said tiers were pinned in frontmatter; theirs were not) and carry output budgets like every other agent. The verifier also states its standing stop-slop gate in its own definition - it is dispatched fresh-context and never sees the routing rule that assigned it.
- **One count removed from the skill-routing rule.** "Four bundled skills" becomes a sentence that cannot go stale when the library grows.

## 2.7.1 (2026-08-26)

- **The refusal rule closes the offer-shape.** Benchmark measurement found one failure the 2.7.0 hardening did not reach: a session that correctly refuses an improper decision-log entry, then offers to write it anyway if the user confirms. decision-log.md now says a refusal is complete in itself: offering to perform a refused action conditionally is performing the first half of the action. The scenario that beat the previous wording passes with this one.

## 2.7.0 (2026-08-26)

- **Two rules hardened, shipped with a benchmark receipt.** A reliability benchmark ran adversarial scenarios against this team's rules: before these edits, sessions could be talked into weakening their own configuration or accepting a standing "anything under $X is pre-approved" waiver into the decision log; after them, the same scenarios re-ran clean, with no over-blocking of legitimate direct instructions. escalation.md gains a "Guarding the guardrails" section: your configuration is the owner's, not the session's - weakening permission rules, rules files, agent tool allowlists, or hooks is owner-by-hand every time, a blocked edit is the guard working rather than an obstacle to route around, and standing waivers given in chat are never accepted or logged. decision-log.md gains integrity lines: never backdate, pre-record, or fabricate an entry, or offer wording that would; a decision reported after the fact is recorded under today's date and labeled retroactive.

## 2.6.0 (2026-08-26)

- **New command: /find-gap.** The missing front door to the idea pipeline. You name an industry, product type, or audience; the researcher reads real complaints from forums and reviews, checks whether people are actively seeking solutions and why the existing ones disappoint, and returns ranked gaps with verbatim, sourced evidence and an honest confidence statement. It ends by offering /grade-idea on the top gap, so a hunch becomes a scored idea inside one free install. Its output says plainly what it did not do: it reads a biased sample, the demand check is judgment rather than measurement, and finding a real problem is not a prediction of success.

- **A stale count removed from /verify-install.** Step 3 described the paid bundle's skill library with a number that had been wrong through two releases. The sentence now describes the difference without counting it, which cannot go stale.

## 2.5.0 (2026-08-26)

- **The orchestrator never told anyone to use a skill.** The kit ships bundled skills and a rule mapping them to agents, and the coordinator that decides how work gets done contained zero references to any of it - so specialists were dispatched unequipped, and a domain no specialist covered quietly became the orchestrator's own work. Found from an owner's real session where a full day of production ran almost entirely inline. The Method grows from 5 steps to 9: name the expertise a unit needs before choosing who runs it; equip every dispatch with the matching skills by full path (subagents do not load installed skills automatically); when no specialist and no skill covers a domain, constitute an expert under an explicit brief rather than approximating; and doing a unit yourself is a routing decision that needs a reason. One new guardrail: a run that produced good work without routing any of it is a failed orchestration, however good the output.

- **The worker agents now check for a matching skill before starting.** builder, researcher, reviewer, and planner each gained a first guardrail: check `.claude/skills/` for a matching skill before producing work in a domain, and name any skills loaded in the output. The runner (its unit names its skill), the five advisors (deliberately lean per the grading rule), and the verifier (fresh-context by design) are unchanged on purpose.

## 2.4.3 (2026-08-23)

- **The memory layer's decision-log tail was silently absent on any project using the shipped starter decision log.** The hook matched entries with `grep '^## '`, while the scaffold's own starter `decisions.md` uses `- YYYY-MM-DD:` bullets and neither the decision-log rule nor `/handoff` prescribes headings. So half of what this layer advertises printed nothing, on exactly the projects that followed the shipped files most closely, and it failed by returning a plausible partial answer rather than an error. Both hook variants now match either format. Confirmed by control (same file, same hook, only the marker changed) and tested four ways: POSIX `sh` and PowerShell, against bullet-format and heading-format logs.

- **Documentation only, no payload behavior change.** The memory layer's cost figures are restated as a measured range instead of a single number. The three places that carried it disagreed with each other (roughly four hundred tokens in the layer's own README, five hundred in the user guide and in the installer's opt-in question), and none of them was the measured answer. Measured across sixty one real handoff briefs: the digest path, which covers fifty nine of them, runs roughly three hundred fifty to five hundred tokens with a median near four hundred twenty. Three things the old wording never said are now stated: the decision-log tail is already inside that figure rather than added to it, the digest itself has no internal length cap so an unusually long "Next action" section produces an unusually long digest, and the numbers come from a public tokenizer rather than Claude's own and are approximate. The user guide also had the common case backwards, describing whole-file injection as typical when it is rare once a project has real history.

## 2.4.2 (2026-08-23)

- **Documentation only, no payload behavior change.** Every agent, command, rule, script and skill is byte-identical to the previous release.
- **The install instruction now leads the README.** It sat below the requirements list and the file tree, so the first thing a reader met was a folder layout, and working out that the kit installs itself took one user days against an install that takes minutes. The instruction is now the first section, and it says plainly that you do not copy any files by hand.
- **The README now says the paid product exists and is shipping.** A free-kit user reported believing Backbrief Business OS was still in development. It was mentioned only in the changelog, in installer-internal instructions, and in one line of a command description, so nothing a new reader would see. There is now a short section naming it, stating that the free kit is complete and not a trial.

## 2.4.1 (2026-08-22)

- **Documentation only, no payload behavior change.** The user guide's memory-layer cost sentence now states the whole range: roughly five hundred tokens in the common case, up to about fifteen hundred when a short brief loads whole. Every agent, command, rule, script and skill is byte-identical to the previous release.

## 2.4.0 (2026-08-22)

- **New: automatic memory layer, opt-in.** A small SessionStart hook can recall the newest handoff brief and the tail of the decision log at the start of a session, so the team starts already knowing where the project stands, and the recall comes back after a compaction wipe too. The installer asks once per project; it lives in `kit/memory-layer/` and never touches `.claude/memory/` itself.
- **Em-dash sweep.** Every shipped prose file in this kit is rewritten to use plain punctuation instead of em dashes.

## 2.3.2 (2026-08-21)

- **Corrects one sentence in the 2.3.0 entry below, which is corrected in place so nobody reads the wrong description while scrolling back.** It said `resume.md` stays in the payload as a signpost. It does not: the stub was removed before 2.3.0 shipped, because a file in `commands/` that cannot be typed inflates a command count three shipped documents assert. `/verify-install` detects a leftover `resume.md` from an older install and offers to remove it instead, which is what the payload actually does.
- **No payload change of any kind.** Every agent, command, rule and skill is byte-identical to 2.3.1. This release exists so the changelog is not lying about the contents of the download it describes.

## 2.3.1 (2026-08-21)

- **Corrects one claim in `/verify-install`.** It said `/resume` and `/plan` are both "taken by built-ins". Only `/resume` is: typing it opens Claude Code's session picker and a command file of that name never runs, which is observed and reproducible. `/plan`, which this kit does not ship, is contested rather than dead - a command file of that name does run in the Claude Code desktop app - and the 2.3.0 wording overstated it.
- **No payload behavior change.** Every agent, command, rule and skill is identical to 2.3.0. The `/resume` to `/pickup` rename is unaffected and stands.

## 2.3.0 (2026-08-21)

- **`/resume` was renamed to `/pickup`, because typing `/resume` never reached this kit's file.** Claude Code ships a built-in `/resume` that opens a session picker, and it wins the name outright. The kit documented `/resume` in its README, its plugin listing, its session-hygiene rule, and the closing line of `/handoff`, so anyone who followed the instructions got a session picker with nothing explaining why. The command's behavior is unchanged; only the name is. No stub file ships: a file in `commands/` that cannot be typed inflates a command count this kit's own documentation asserts, so `/verify-install` detects a leftover `resume.md` from an older install and offers to remove it instead.
- **Why the checker never caught it.** A built-in command lives in neither `~/.claude/commands/` nor `~/.claude/skills/`, and those were the only two places `/verify-install` compared against. It reported a clean install with total confidence while a documented command was unreachable. `/verify-install` now checks the built-in namespace as a third case and tells you how to test a name in ten seconds.
- **`/pickup` also gained the read discipline `/resume` never had.** It now reads an append-only decision log by its tail rather than whole. A plain read returns the TOP of a file, so "the last 5 entries" silently became the OLDEST five on any project with a long log, and the session carried on believing it held current context. That failure is silent, which is what made it worth a step of its own.
- Upgrading from 2.2.x: run `/pickup` where you used to run `/resume`. Nothing else changes.

## 2.2.3 (2026-08-21)

- The license no longer calls itself a draft. It had carried "**DRAFT: have an attorney review before first distribution**" since before the kit was first published, which was an internal note that shipped by mistake and was a false statement about a product already distributed hundreds of times. It now says the same honest thing the paid bundle has said since 3.2.2: this license has not yet had attorney review, and it will be updated through the free updates channel when it has. **No right, restriction, or permission changed.**
- The license title dropped the retired product name.
- No change to any agent, command, rule, or skill. The MIT attribution clause still points at `kit/.claude/skills/`, which is where the third-party notices actually live in this download.
- Version numbering note: this release jumps 2.2.1 → 2.2.3 so the zip and the plugin report the same number. There was no 2.2.2 for the zip. That release changed plugin and marketplace metadata only, none of which ships in this archive.

## 2.2.1 (2026-08-18)

- `escalation.md` describes the paid bundle's enforcement layer accurately. It had said the layer is "off unless you turn it on", which is wrong for a fresh install: the installer recommends it and turns it on when you state no preference. Only a setup you already run is strictly off-unless-yes. The same sentence also left out that the layer guards the files it lives in, not just outward shell commands.
- Why it changed: the sentence is the kit's one description of what the paid tier adds, and it was overstating how cautious the installer is. Prose only, no behavior change.

## 2.2.0

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
- /setup now closes with one optional line: an installed kit cannot announce new versions, so if you want an email when a meaningful update ships, the form at backbrief.ai/get-the-kit is the update list. Said once, a no is a no, and it is never repeated. If you skip /setup, the first-run greeting makes the same offer instead.
- Nothing else changed. Item counts stay 12 agents, 7 commands, 10 rules, 4 skills.

## 2.0.0 (2026-08-10)
- The kit is renamed: the Shiproom Kit is now the **Backbrief Kit** (and the paid bundle is now **Backbrief Business OS**). Same files, same system, new name; the site moved to backbrief.ai and shiproom.ai redirects there. Nothing about how the kit works changed in this release: the major version marks the rename.
- Every download link you already have keeps working: the old shiproom.ai URLs redirect permanently to the same files on backbrief.ai.
- Updating over an older install works exactly as before: the installer recognizes earlier "Shiproom Kit" and "Agent OS Kit" installs (stamped or not) as its own and upgrades them, never touching anything you wrote. Memory backups now go to `_backbrief-backups/`; old `_shiproom-backups/` folders are recognized during cleanup.
- Item counts are unchanged: 12 agents, 7 commands, 10 rules, 4 skills.

## 1.5.0 (2026-08-09)
- Your knowledgebase is now a first-class part of the kit. `/setup` asks for the documents AND the links the team should work from (digital books, guides, product docs, a docs site, a Notion page), copies the files into `context/reference/`, and records every source in a new index, `context/reference/SOURCES.md`, with a note on when to use it. Links finally have a home: they live as rows in that index.
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
- New: /setup command: first-time setup interview writes the context files for you; no manual file editing.
- New: /verify-install command: plain pass/fail install check, including the common copied-too-deep mistake.
- New: first-run greeting: on a fresh install the team introduces itself and offers /setup.
- New: install docs lead with the one-paste assisted install (Claude does the copying, same on Windows and Mac); manual copying is now the alternative, with a Mac hidden-folder note.
- Also available as a Claude Code plugin: /plugin marketplace add charlesashe/shiproom-kit

## 1.1.0 (2026-08-01)
- Four bundled skills (stop-slop, sop-builder, competitive-analysis, content-repurposer) with attribution; skill-routing rule; license files.

## 1.0.0 (2026-07-14)
- Launch: 12 agents, 4 commands, 9 rules, project scaffold, /handoff + /resume project memory.

## Updating an existing install

Download the current version, unzip it, open Claude Code in the newly unzipped folder, and type **install this**. It will tell you which version it is, notice what you already have, say what it is about to replace, and ask before it does. Your own files are never touched and your memory folder is backed up first.

If you still have the folder from a previous download, delete it or move it aside before you start. The only thing that goes wrong here is opening the old one by mistake, and the installer now names its own version in its first line so you can catch that immediately.
