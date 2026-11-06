# Choose among the reviewed candidates

## Purpose

Evaluate a fixed candidate set in fresh contexts when possible,
and decide whether available evidence justifies selecting one.

## Inputs

- original task and constraints
- fixed candidates with descriptive names and any matching IDs, including any candidate that combines parts of others
- `cross-critic` report
- optional factual evidence

## Procedure

1. Review every candidate adversarially against the same criteria.
2. Do not invent another candidate or change the set of approaches being compared.
3. Treat unsupported assumptions as liabilities.
4. Do not reward verbosity, familiarity, confidence, or synthesis merely for including more ideas.
5. If multiple candidates remain materially indistinguishable, return `EQUIVALENT`.
6. If missing evidence could change the decision, return `ABSTAIN` and name the cheapest useful next inquiry.
7. Otherwise return `SELECT <candidate>`.

## Output

Exactly one:

- `SELECT`: candidate, reasons, important rejected alternatives, remaining uncertainty
- `EQUIVALENT`: candidate set, reasons, optional deterministic tiebreak criterion
- `ABSTAIN`: reasons, missing evidence, cheapest useful next inquiry

## Constraints

- Use the names and any identifiers from the supplied fixed set.
- When candidate IDs are supplied, return them for exact matching and include the names in the explanation.
- Selecting a candidate that combines parts of others is ordinary `SELECT <candidate>`; it is not a separate decision kind.
- No new design may be synthesized during judging.
