---
name: implementation-plan
description: Work out or review how to implement a given ticket in the current repository. Use when explicitly asked to plan a ticket's implementation or review its implementation plan. Identify the existing code path, required changes, verification, and material unresolved choices. A concrete requested change can supply the task when no ticket exists; do not require ticket creation. Not for decomposing a broad goal, selecting product scope or architecture, ordinary ticket refinement, executing agreed work, or adding a mandatory planning stage to an already-actionable ticket.
---

# Implementation Plan

Work out how to implement one ticket using the current repository's code and test facilities.
Consume the ticket's outcome, acceptance conditions, and settled design; supply only the missing execution detail.
A concrete requested change can serve as the task when no ticket exists; do not create a ticket just to use this procedure.
Use this procedure when planning or plan review is requested; ordinary investigation during implementation does not require it.
An already-actionable ticket needs no separate planning stage.
Keep a complete path from the caller to the required result throughout planning; add inspection, verification, or commit structure only when it helps establish that path.
Simplicity concerns the proposed work, not just the length of the document, and must not change the selected design or weaken required behavior or verification.

## Procedure

1. **Establish the ticket's outcome and constraints.** Read its current acceptance conditions, linked design, existing implementation detail, and repository guidance.
   Reuse settled decisions, contracts, and non-goals; do not reconstruct the wider goal's decomposition.
   Identify required observable results and known preservation requirements before choosing implementation machinery.
   Classify material choices as `decided`, `conservative default`, or `unresolved`; mark unresolved choices as blocking or non-blocking.
   If inspection exposes an unsettled architecture, a missing prerequisite, or a necessary change to the ticket's boundary, report it and stop dependent planning.
   Do not silently expand the ticket, select a replacement architecture, or revise the issue graph.
   Continue independent planning within the settled scope.
2. **Start with a complete working path.** Sketch how the caller reaches the required result using existing facilities and the selected design.
   Carry forward known error, lifecycle, and compatibility requirements, not just the successful request.
   Name uncertainties that could change this candidate; do not fill them with speculative components or interfaces.
   This candidate is the basis for inspection and revision, not an extra document or approval stage.
3. **Inspect to resolve those uncertainties.**

   **Trace the candidate.**
   Follow its entry points, data flow, side effects, deployed consumers, and affected bypass paths.
   Inspect relevant tests, docs, and dependencies to establish which existing facilities suffice.

   **Resolve unknowns that could change the plan.**
   Each further investigation must resolve an unknown that could change the candidate or its verification; stop when the evidence settles it.
   Separate observations from assumptions.

   **Establish what must stay compatible and what each interface guarantees.**
   Before treating preservation as required, cite its source and trace whether affected consumers change and deploy together.
   Apply [Compatibility](../references/change-with-evidence.md#compatibility); mark unknown preservation requirements as unresolved rather than conservative defaults.
   Reference existing ownership, effects, representations, lifecycle, and compatibility contracts.
   Fill only gaps that could change the plan using the applicable [boundary-contract questions](../architecture-design/references/boundary-contracts.md).

   **Trace affected transitions.**
   Check relevant setup, error, cancellation, cleanup, concurrency, shutdown, and consumer-specific transitions without reopening unchanged lifecycle categories.
4. **Revise the candidate as evidence changes.** First try to accommodate each finding through the current path and its existing owners.
   Before adding a control, component, interface, test fixture, or phase, identify a required case the smaller candidate cannot handle.
   A useful purpose does not establish that a separate mechanism is necessary.
   If another complete approach is smaller, replace the candidate rather than retaining its machinery and adding workarounds.
   When controls always vary together for current consumers, represent them as one concept; preserve independent choices that a current caller actually needs.
   Require a concrete second consumer or governing constraint before adding reusable infrastructure or supporting additional scopes.
   A current caller's need to choose a value can justify a narrowly scoped option without a second consumer.
   Do not widen adjacent operations merely to match a new operation, or defer unnecessary work into a supposedly required later phase.
   Keep useful optional work out of the required path.
   Check interfaces against affected callers, producers, and transitions; specify high-risk behavior and invariants, leaving low-risk mechanics to implementation.
5. **Choose verification for that path.** Identify the behavior the consumer must observe or the realistic regression each check must detect.
   Separate the required evidence from the machinery that produces it; compare existing test facilities before proposing a new maintained runner or fixture.
   A required check against the real system does not by itself justify new test infrastructure; compare ways to set it up using the same reasoning as for the implementation.
   For a small finite behavior space, use an exhaustive table or transition matrix with focused regression cases.
   Require generated properties or action sequences only for identified invariants or combinations those cases cannot adequately cover.
   Use integration, pseudo-terminal, migration, or real-service tests when the observable boundary requires them, not merely because those tools exist.
6. **Order the required edits.** Identify the affected files or subsystems and the useful intermediate results.
   Include commit boundaries only when requested or when they materially help implementation or review.
   For proposed commits, give an imperative subject and verification that passes at that point; use `commit-quality` for commit boundaries and messages.
   Land tests with their behavior; keep preparatory refactors independently justified and behavior-preserving.
   Commit boundaries organize the candidate; they do not justify extra architecture, fixtures, or deliverables to make a commit look self-contained.
7. **Record only the missing implementation detail.** Keep it in the existing ticket when updates are authorized.
   Remote ticket updates require explicit user direction; a planning request alone does not authorize them.
   If ticket updates are not authorized, return the proposed detail in the response or requested local artifact.
   A read-only or proposal-only request requires reporting the proposed detail without changing the ticket.
   Do not maintain a parallel plan; create a separate artifact only when requested or needed by a concrete reader, and link it from the ticket when authorized.
   State each rule once, beside the interface guarantee or work it constrains.
   Group related failures under their governing invariant; keep reproductions and expected outcomes in one acceptance section.
   Let steps identify the work and reference its checks rather than restating the rules.
   Retain reasons that could change an implementation decision; omit investigation chronology, speculative extensions, and unsupported safeguards.
8. **Check completeness against the repository.** Confirm that the current candidate still covers the governing requirements and required verification.
   Within affected paths, check bypass paths, global state, unbounded resources, cancellation ownership, error precedence, compatibility, docs, generated files, dependencies, and platform behavior.
   Check that every addition is still needed for a required case the smaller candidate cannot handle, and that the plan's detail does not exceed what the evidence supports.

## Output

Use [descriptive names](../holistic-writing/references/editorial-pass.md#use-descriptive-names)
for tasks and decisions, retaining existing issue numbers and specification references.

Default to a compact plan containing:

- **Task and constraints:** reference the ticket's outcome, acceptance conditions, and settled design rather than copying them; identify material implementation decisions.
- **Implementation steps:** affected files, useful intermediate results, and checks that pass at each step; include logical commits only when useful or requested.
- **Verification:** concrete acceptance cases and required repository checks.
- **Material unresolved questions:** only those that can change implementation, marked blocking or non-blocking; omit if none remain.

Put storage, lifecycle, and compatibility details beside the contract or step they constrain.
Add separate sections only when they make the implementation easier to follow; the above is not a mandatory heading template.
Keep implementation detail in the ticket when one exists and updates are authorized.
Otherwise return a concise proposal in the requested format and location, following repository conventions.
For a task without a ticket, do not create tracker work or a separate maintained artifact unless authorized.
Separate docs from behavior only when repository practice or generated output warrants it.

## Constraints

- Do not edit implementation files unless implementation was also requested.
- A request to create the selected design's artifact or execute agreed work is implementation, not a request for another plan.
- Give effort ranges only with evidence and dominant assumptions.
- Make affected cancellation, cleanup, output ownership, compatibility, and error precedence explicit; reference settled contracts for unchanged behavior.
- Review existing facilities before proposing a dependency.
- Prefer a short complete plan over possibilities or premature implementation detail.
