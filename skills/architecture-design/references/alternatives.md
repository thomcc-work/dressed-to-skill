# Map design alternatives

## Purpose

Use when tracing an existing path leaves a genuine unresolved architectural choice.
Produce up to three viable, materially distinct briefs; diversity must come from different underlying decisions, not wording or role-play.
Skip this technique when supplied candidates already cover the material choices.

## Inputs

- the design task or question
- explicit user constraints
- relevant repository context
- optional evidence from `pain-axis`

## Procedure

1. Identify the few decisions that distinguish the possible designs: ownership, persistence, synchronization, representation, lifecycle, compatibility, consistency, abstraction boundary, etc.
2. Reject an alternative only when there is a concrete reason:
   - violates an explicit requirement;
   - internally inconsistent;
   - duplicates another approach closely enough to add no useful choice;
   - strictly dominated on the stated criteria.
3. Check that a rejection does not impose a preferred design's optional guarantee on its competitor or compare one repaired candidate with another's unrepaired state.
   Name the governing requirement or evidence behind the rejection; keep missing evidence distinct from a demonstrated failure.
4. Produce up to three briefs for viable approaches that make materially different decisions; do not fill unused slots.
   Give each a short [descriptive name](../../holistic-writing/references/editorial-pass.md#use-descriptive-names)
   based on its design, such as "Shared queue" or "Queue per worker". Preserve any supplied identifiers alongside the names.
   Retain or assign stable candidate IDs when matching plans across workers or review phases.
5. Each brief should be small: key decisions, rationale, important assumptions, and what would make the brief invalid.
6. Record rejected alternatives and reasons separately.

## Output

For each brief:

- `name`: short descriptive name, used consistently in later comparisons
- `id`: stable candidate key, when needed for exact matching
- `key_decisions`: short list of concrete decisions
- `rationale`: why this approach is viable
- `assumptions`: assumptions that matter
- `invalid_if`: evidence that would rule it out
- `why_distinct`: which decisions differ from the other briefs, and how

Also return `rejected_forks` with reasons.

## Constraints

- Do not write complete implementation plans.
- Do not invent weak alternatives merely to fill three slots.
- Unconventional is not the same as bad.
- `why_distinct` must name specific differing decisions, not vague style labels.
- If fewer than three genuinely viable approaches exist, say so rather than fabricating one.
