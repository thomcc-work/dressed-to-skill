# Compare candidate plans

## Purpose

Compare a fixed set of independently generated plans without collapsing them into one design too early.

## Inputs

- original task and constraints
- candidate plans with descriptive names and any matching IDs
- optional repository evidence
- alternatives rejected during the initial search, shown only after the first independent comparison pass

## Procedure

First pass, without seeing the rejected alternatives:

1. Identify each candidate's unique strengths.
2. Identify unsupported assumptions, hidden costs, missing requirements, and likely failure modes.
3. Distinguish real architectural differences from cosmetic ones.
4. Identify any important approach apparently missing from all candidates.
5. Identify components that seem cleanly separable from their proposed designs and might be combined, but do not create a combined design yet.

Second pass, after seeing the rejected alternatives:

6. Review rejected alternatives skeptically; do not assume the initial search was correct to reject them.
7. Call out any rejection that looks premature or any missing approach that should be reconsidered.

## Output

- per-candidate strengths
- per-candidate problems
- decisive comparisons
- missing approaches
- components that might be combined
- missing evidence that could change the ranking
- rejected alternatives worth reconsidering

Preserve supplied candidate IDs for matching findings to plans, and use the names in the explanation.

## Constraints

- Do not choose a winner.
- Do not rewrite the candidates.
- Do not create a combined plan; leave that to the `fusion-candidate` phase.
- Treat candidate ordering and verbosity as irrelevant.
