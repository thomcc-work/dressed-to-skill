# Writing selected designs and implementation specs

Use this reference when documenting an already selected design or writing an implementation spec.
It does not select a design, write requirements, or replace the people, skills, or procedures responsible for the development process or design review.
Use `requirements-definition` for requirements from established goals and authoritative sources and [spec review](../../spec-review/SKILL.md) for auditing the specification's contract.

## Explain the proposal before its technical details

For a selected nontrivial design, consider this progression when it helps the reader understand the proposal.
Do not use it as a mandatory writing workflow or heading template:

1. **Motivation:** what is difficult today and why it matters.
2. **Goals:** observable outcomes and protected behavior.
3. **Proposal in plain language:** what the named design means and does not mean.
4. **Terms and examples:** vocabulary and representative cases.
5. **Evidence:** what was measured, using which inputs and limitations.
6. **Scope and boundaries:** ownership, authority, effects, compatibility, and non-goals.
7. **Detailed design:** data model, algorithms, lifecycle, failure behavior, schemas, and interfaces.
8. **Delivery:** implementation sequence, migrations, documentation changes, and commits.
9. **Proof:** tests, acceptance checks, unresolved decisions, and completion condition.

This is guidance, not a mandatory heading template; preserve the dependency: readers should understand the problem, proposal, and examples before encountering solver models, schemas, hashes, or APIs.

Explain a nontrivial mechanism as:

1. the problem;
2. a concrete example or trace;
3. the solution and its invariant.

## Organize implementation requirements

For implementation specs, outline the requirements for parts that can be implemented independently before drafting details.
Order sections by dependency.
Before filling them in, check whether sections bundle separate decisions or make readers collect a part's requirements from distant passages; reorganize as needed.
For each part, make inputs, required behavior, failure cases, and examples or evidence that it meets the requirements easy to locate.
Distinguish rationale from required behavior.
This is structural guidance, not a fixed template.

Preserve exact API, serialization, failure, and lifecycle contracts after the reader has the model needed to understand them.

## Make the selected design reviewable

A selected design should make these reviewable without reconstructing hidden decisions:

- motivation and success criteria;
- exact meaning of the named design;
- rejected alternatives that explain why the design includes some behavior and excludes other behavior;
- authoritative and derived representations;
- ownership and approval;
- normal behavior, errors, ambiguity, and recovery;
- compatibility and migration effects;
- representative single and composed cases;
- implementation order;
- verification tied to requirements;
- blocking decisions and completion condition.
