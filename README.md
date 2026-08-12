# Backbrief Kit — Claude Code plugin

Run your Claude Code project like a team: 12 agents — including an orchestrator that plans and routes and a fresh-context verifier that gates finished work — plus 10 rules, 4 bundled skills, and project memory that survives across chats (/handoff + /resume).

This repo is the **plugin installer** for the free kit. Full product page: [backbrief.ai](https://backbrief.ai) · built by [Charles Ashe](https://charlesashe.ai).

## Install (three commands, Windows and Mac identical)

```
/plugin marketplace add charlesashe/backbrief-kit
/plugin install backbrief-kit@backbrief
/backbrief-kit:setup
```

`/backbrief-kit:setup` installs the kit (globally or into your project — it asks), runs a self-check, then interviews you in plain words to configure the project. No file copying, no hidden folders, no editing markdown by hand.

After setup, use the kit's own commands with no prefix: `/next`, `/critique`, `/council`, `/handoff`, `/resume`, `/setup`, `/verify-install`.

## Updating

```
/plugin update
/backbrief-kit:setup
```

Setup upgrades the kit's own files and adds what's new; it never overwrites your files, context, or memory (memory is backed up first).

## Prefer a zip?

The same kit ships as a downloadable zip (delivered by email) at [backbrief.ai](https://backbrief.ai) — identical contents, assisted one-paste install.

## What's inside

- `kit-payload/team/` — the installable `.claude/` payload: agents, commands, rules, skills, root CLAUDE.md
- `kit-payload/scaffold/` — the per-project working folders and templates
- `commands/` — the plugin's installer (`setup`) and checker (`verify-install`)

Licensing: the kit is free to use and share unmodified, not to resell (LICENSE.md). The four bundled skills are third-party MIT work with attribution — see `kit-payload/team/skills/THIRD-PARTY-LICENSES.md`.

The paid tier, **Backbrief Business OS** (ops agents + the intake/plan/grade/approve loop + 17 revenue skills), is at [backbrief.ai/business-os](https://backbrief.ai/business-os).
