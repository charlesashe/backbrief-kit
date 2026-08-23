# Backbrief Kit: Claude Code plugin

Run your Claude Code project like a team: 12 agents (including an orchestrator that plans and routes and a fresh-context verifier that gates finished work) plus 10 rules, 4 bundled skills, and project memory that survives across chats (/handoff + /pickup), now with an opt-in hook that recalls it automatically at every session start.

This repo is the **plugin installer** for the free kit. Full product page: [backbrief.ai](https://backbrief.ai) · built by [Charles Ashe](https://charlesashe.ai).

## Install (three commands, Windows and Mac identical)

```
/plugin marketplace add charlesashe/backbrief-kit
/plugin install backbrief-kit@backbrief
/backbrief-kit:setup
```

`/backbrief-kit:setup` installs the kit (globally or into your project; it asks), runs a self-check, then interviews you in plain words to configure the project. No file copying, no hidden folders, no editing markdown by hand.

After setup, use the kit's own commands with no prefix: `/next`, `/critique`, `/council`, `/grade-idea`, `/handoff`, `/pickup`, `/setup`, `/verify-install`.

## Updating

```
/plugin update
/backbrief-kit:setup
```

Setup upgrades the kit's own files and adds what's new; it never overwrites your files, context, or memory (memory is backed up first).

## Prefer a zip?

The same kit ships as a downloadable zip (delivered by email) at [backbrief.ai](https://backbrief.ai), identical contents, assisted one-paste install.

## If you want the fuller system

This kit is complete and free. It is not a trial, nothing in it expires, and nothing is held back.

There is also a paid product, **Backbrief Business OS**, and it is shipping today. It contains this
kit plus a CEO loop (a structured intake, a business plan, a graded stress-test against a published
rubric, and a recorded go/no-go) and an operations tier that stays locked until a plan has actually
been approved. It is at [backbrief.ai](https://backbrief.ai).

## What's inside

- `kit-payload/team/`: the installable `.claude/` payload: agents, commands, rules, skills, root CLAUDE.md
- `kit-payload/scaffold/`: the per-project working folders and templates
- `kit-payload/memory-layer/`: the optional automatic-memory layer, an opt-in SessionStart hook that recalls your newest handoff brief and decision-log tail at the start of every session (its README explains the one-question install)
- `commands/`: the plugin's installer (`setup`) and checker (`verify-install`)

Licensing: the kit is free to use and share unmodified, not to resell (LICENSE.md). The four bundled skills are third-party MIT work with attribution; see `kit-payload/team/skills/THIRD-PARTY-LICENSES.md`.

The paid tier, **Backbrief Business OS** (ops agents + the intake/plan/grade/approve loop + 17 revenue skills), is at [backbrief.ai/business-os](https://backbrief.ai/business-os).
