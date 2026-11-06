# Independent design deliberation

Use only when evidence establishes an unresolved choice between architectures that needs independently developed proposals and critique to resolve it.
A local change, a single design to assess, or a choice settled by repository evidence does not need this workflow.
Compare simpler alternatives directly using [Map design alternatives](alternatives.md).
This procedure selects a design; it does not authorize implementation or expand the task.

Prefer subagents in fresh contexts for the planning and review phases below.
If subagents are unavailable or the user asks to work without them, perform the comparison directly;
the fresh-context and withheld-input requirements then do not apply.
Report that limitation, and leave any explicitly required independent evidence unverified.

## Inputs

Use the original design question, user constraints and non-goals, repository evidence, and existing candidates.
Name the user-visible outcome, current baseline, and difference that would justify changing it.
Work through one complete affected case before expanding comparison; keep the baseline among the candidates.
Internal completeness or consistency supports the decision but does not replace the governing outcome.
A worked case need not be a finished implementation or benchmark.

Use historical evidence when it could change the decision; do not require a history investigation for every comparison.
If existing candidates cover the material choices, skip the search for alternatives.
For one supplied design, do not manufacture alternatives unless an unresolved architectural choice remains.

## Compare the unresolved approaches

Read each phase reference only when entering its phase.
For a delegated phase, supply its full text or resolved absolute path, shared inputs, and only that phase's candidate material.
These references are not registered skills or names for subagent preloading.

1. **Map missing options:** use [alternatives](alternatives.md) only when material choices remain uncovered.
2. **Develop plans independently:** assign one [independent plan](independent-plan.md) per viable brief, in parallel when practical.
   Each receives only its own brief plus shared task, constraints, and evidence.
   Use consistent [descriptive names](../../holistic-writing/references/editorial-pass.md#use-descriptive-names)
   for candidates in reports. Retain or assign stable candidate IDs alongside the plans when matching worker outputs
   and reviews; pass the same IDs through each phase and keep them fixed during the comparison.
   If fewer than two viable plans survive, stop and report why.
3. **Critique:** [compare the candidate plans](cross-critic.md) without selecting or rewriting them.
   Supply alternatives rejected during the initial search only after this comparison.
4. **Consider combining parts:** [construct a combined candidate](fusion-candidate.md) only if critique identifies components that may work together cleanly.
   Keeping the candidates separate is a normal result; any combined design remains an ordinary candidate with stated sources and risks.
5. **Review a fixed set:** [choose among the reviewed candidates](council-review.md) using the candidates and critique.
   Do not add or rewrite candidates once review starts; hide the provider or author where practical and ignore ordering.
   Accept selection, equivalence, or abstention; abstention identifies missing evidence and the cheapest useful inquiry.

## Stop and hand off

Use at most three initial plans and at most one candidate that combines parts of those plans.
Do not add revision rounds, recursive debate, or forced agreement after equivalence or abstention.
Add a heavier step only after observing a concrete failure it would prevent, not for a speculative omission.
Prefer tests, type checks, static analysis, benchmarks, and repository evidence to additional model votes.
A selected design is a hypothesis, not verification.
Carry its existing boundary contract forward; revise only unresolved or changed contracts, without a new declaration phase.
Use [implementation-plan](../../implementation-plan/SKILL.md) only when a plan is requested.

Report the selected candidate, equivalent set, or abstention; decisive reasons; important uncertainty; whether combining parts was considered; and the next useful action.
Keep intermediate transcripts out unless requested.
