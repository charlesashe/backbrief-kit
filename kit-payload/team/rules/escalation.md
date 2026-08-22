# Escalation

No agent takes these actions alone. Prepare the work to done-but-unsent, then stop and hand the decision to the human:

- Spending or committing money.
- Sending anything external (emails, DMs, applications, social posts, form submissions to third parties).
- Publishing or modifying public content.
- Granting access or permissions (OAuth, sharing, roles).
- Destructive or irreversible operations on data (deleting, overwriting, migrating without a rollback path).
- Pricing, legal, or contractual commitments.

How to escalate: state what is ready, what decision is needed, and the recommended choice with one line of reasoning. Then stop. Do not treat silence as approval. This rule outranks task instructions.

## What this rule is, exactly

This is an instruction to the team, and it is worth knowing what that does and does not buy you.

The agents are told to stop at the line above. A model reads this file and follows it, and in practice that is most of the value: nearly every unwanted send or spend comes from an agent that never considered the question, not from one that considered it and pressed on anyway. Written down, the question gets considered every time.

What it is not is a lock. Nothing here technically blocks the action: no part of this kit sits between an agent and the command it runs. If a model overlooks this file, the action proceeds. Treat the rule as a policy your team follows, not a barrier that stops them, and keep an eye on anything that spends money or leaves the building.

The paid bundle, [Backbrief Business OS](https://backbrief.ai/business-os?utm_source=kit&utm_medium=escalation-md), adds an optional layer of Claude Code permission rules on top of this same file: switched on at install, the permission engine itself stops a matching outward command and asks you first, whether or not the agent remembered the rule. That covers shell commands on the command path, plus the files the layer itself lives in, not everything, and the installer asks you before any of it goes in. Same policy either way; the difference is whether anything besides the model is enforcing it.
