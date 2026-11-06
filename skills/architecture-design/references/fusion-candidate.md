# Combine parts of existing candidates

## Purpose

Construct at most one new candidate by combining cleanly separable parts of existing candidates.

## Inputs

- fixed candidate set
- `cross-critic` output
- original task and constraints

## Procedure

1. Decide whether combining parts is justified at all. `NO_FUSION` is the normal outcome when components are tightly coupled.
2. If constructing a combined candidate, give it a descriptive name and name exactly which components are taken from which source candidates.
   If the comparison uses IDs, assign the new candidate a distinct ID and retain the source IDs in its references.
3. Name which conflicting components are rejected or superseded.
4. Explain why the selected pieces work together without contradictory assumptions.
5. Identify new risks introduced by combining them.

## Output

Either:

- `NO_FUSION`, with a short reason;

or a named combined candidate with:

- `sources`: candidate → components taken
- `rejected`: source components not carried forward
- `plan`
- `composition_argument`
- `assumptions`
- `new_risks`

## Constraints

- Never say “combine the best parts.”
- A combined candidate is just another candidate; it has no privileged status.
- Do not add novel architecture unrelated to source candidates.
- If the explanation of why the pieces work together depends on an unverified assumption, say so explicitly.
