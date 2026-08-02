# Agent Routing

Delegate by domain and tier:
- orchestrator: multi-step work spanning more than one agent, planning, or an unclear starting point.
- researcher: gathering facts, sources, prior art, options.
- planner: turning a goal into an ordered plan with acceptance criteria.
- builder: producing the actual artifact (code, copy, document, config).
- reviewer: a quality pass on a draft before it is finished (not the final gate).
- runner: cheap, mechanical, verifiable work with explicit acceptance criteria (a cheap model).
- verifier: the final fresh-context check against acceptance criteria before delivery.

Cost routing (see token-discipline for the full model ladder):
- Mechanical, fully-specified work goes to the runner (Haiku). Routine production and structured judgment — builder, researcher, reviewer, council advisors — run on the mid tier (Sonnet), pinned in their definitions. Deep planning, coordination, and final verification — planner, orchestrator, verifier — stay on the strong model.
- Cap runner retries at two; on the second failure, escalate to a strong model instead of looping.
- Never run an unattended loop without an iteration cap and stop criteria.
