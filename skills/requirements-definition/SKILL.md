---
name: requirements-definition
description: Author solution-neutral requirements from established goals and authoritative sources when explicitly asked to draft requirements. Use for requirements definition and traceability; do not use for product discovery, implementation specifications, architecture, or requirements review.
---

# Requirements definition

## Scope and authority

Use this skill when a person explicitly asks you to draft or revise requirements.
Establish product intent from the user's request and governing sources, including an approved brief when one exists.
A separate brief is not required unless the project's process requires one.
Additional authoritative sources may clarify or constrain intent, but may not expand or contradict it.

Do not author a requirement that expands or contradicts established product intent.
If resolving the conflict is necessary to state the requested requirements, record `NEEDS_PRODUCT_DECISION`
and ask for the missing decision. Follow any required revision and approval process.
Otherwise, raise the idea only as a non-normative suggestion.

Use other sources only when the requester or governing product documentation identifies them as authoritative.
Do not infer required approval from a draft, discussion, ticket, request for ideas, or implementation task.

This skill owns requirements definition only. It does not discover or approve product intent, invent scope, choose an implementation, write implementation specifications, design architecture, define internal APIs, prescribe files, define exact tests, or plan delivery sequencing. Use [specification review](../spec-review/SKILL.md) when a requirements review is requested.

If product intent or required approval is unclear, report the missing authority or decision and stop dependent drafting.
Continue drafting the settled requirements; do not invent scope to fill the gaps.

## How to write a good requirements document

Focus primarily on making the document easy to review.
Use the [shared editorial pass](../holistic-writing/references/editorial-pass.md) for whole-artifact reader experience without changing the requirements decisions owned here.

- Group requirements by review task.
- Put each requirement's source references after its acceptance evidence; keep full citations and a list showing where each source goal, constraint, and non-goal is addressed in an appendix.
- Do not restate decisions multiple times in the doc. Do not repeat documentation or guidelines already available elsewhere; link it instead.
- Include rejected alternatives only when authoritative decisions about them explain
  the requirements or their boundaries.
- Mention relevant edge cases, especially when they explain important boundaries.

## Procedure

### 1. Establish the working inputs

Record, separately:

- the request or brief and its goals, constraints, non-goals, assumptions, and authoritative decisions;
- any additional authoritative sources and their authority;
- the explicit drafting request;
- unresolved questions or conflicting sources.

Do not turn examples, preferences, implementation suggestions, or ambiguous language into requirements without authoritative support.

### 2. Build the traceability inventory

Refer to each source goal, constraint, and non-goal by its existing name, section, or identifier.
Include enough descriptive wording to identify its subject, with a link or short quotation locating the source.
Add a source key only when a tool or record needs an exact reference that the source does not already provide.

For each proposed requirement or exclusion, identify the exact sources that justify it: positive requirements trace to an established goal, constraint, or other explicitly authoritative source; exclusions trace to established non-goals.
A reference points to a source, but the clause's actual wording determines whom a restriction applies to, under what conditions, and during which phase.
For restrictions on who or what qualifies, reasons for rejection, and required evidence, identify the clauses that justify them. Preserve whom and what they apply to, their conditions, and their phase in definitions and acceptance wording.
For example, if a source limits rejection to one named phase, do not write a definition that makes the same restriction apply in every phase.

A material unsupported choice belongs in a review-decisions section clearly marked as not defining requirements when it would change a requirement's meaning or acceptance; mark it `NEEDS_PRODUCT_DECISION` rather than deciding it in the requirement.
Optional, non-blocking agent suggestions are different: label them separately in the response or a section that does not define requirements,
and never turn either suggestions or unresolved decisions into invented requirements.

### 3. Draft observable, solution-neutral requirements

**Define and identify each requirement.**
Give each requirement a short descriptive name.
Retain or assign stable identifiers when checks or other records need exact matches across revisions.
Follow the [naming guidance](../holistic-writing/references/editorial-pass.md#use-descriptive-names)
for identifiers and mnemonic reference labels, and include the name alongside the identifier in prose.
Do not reuse an identifier for a different requirement.

Write each requirement so that an independent evaluator can determine whether it is satisfied from externally observable behavior. Prefer:

- actors, conditions, inputs, outputs, and state transitions visible to users or authorized external systems;
- explicit defaults and precedence when an authoritative source supports them;
- observable error conditions and user-visible or externally relevant error behavior when supported;
- compatibility, security or trust, performance, and operational constraints only when an authoritative source supports them.

**Keep the statement solution-neutral.**
Exclude implementation mechanisms, file paths, internal APIs, architecture, exact test cases, technology choices, and delivery sequencing unless the item is itself an externally observable, authoritative constraint.
Preserve exact identifiers, numbers, error text, and uncertainty from the sources; do not silently normalize or embellish them.

Separate requirements from rationale, evidence, assumptions, and open decisions. Do not hide a product decision inside acceptance wording.

When a requirement has independently decidable parts, state which parts authoritative sources settle and name each unresolved choice by its effect on observable behavior or acceptance.
Keep the requirement and acceptance evidence limited to what is settled; put each unresolved choice in the review-decisions section, outside the requirements, and identify the affected requirement there.
Do not treat settled parts as open merely because another part remains undecided.

### 4. Define acceptance evidence

For every requirement, state concise acceptance evidence describing what would demonstrate satisfaction. Evidence must be observable and proportionate; it is not an implementation plan and must not prescribe exact tests.

**Preserve permitted explanation modes.**
When a source permits more than one way to explain or establish something, keep those modes distinct rather than silently narrowing them to one.
For each permitted mode, state the minimum observable evidence sufficient for acceptance so terms such as “explained,” “justified,” “supported” or “valid” do not leave implementers to decide which cases qualify.
Keep the evidence appropriate to each mode, and do not require evidence from another mode unless the source requires it.
If a source explicitly permits an explanation without derivation, missing derivation alone cannot invalidate that explanation.
Preserve the source's distinction between rule derivation and its other permitted explanation modes.

**Resolve unsettled evidence.**
If sources leave evidence unsettled and plausible readings would accept different cases, do not choose a new burden to make the evidence look complete.
Record `NEEDS_PRODUCT_DECISION` and apply `spec-review`'s [check for unsupported restrictions](../spec-review/references/non-narrowing.md), including its procedure for uncertainty about which cases qualify, without starting a full specification review.

Choose evidence that could show the requirement was not met, such as an observable scenario, result, boundary, or recorded operational measure when the source supports one.
If defining such evidence would require inventing behavior, do not fill the gap in the requirement or its acceptance evidence.
Record the missing decision in the review-decisions section, outside the requirements, and identify the affected requirement, if any.

### 5. Produce the requirements document

**Requirements document.**
This is the artifact that states what must be true and how satisfaction can be assessed.
Use this compact structure unless the requester requires an equivalent structure:

1. **Status and authority** — approval state, source documents, and scope.
2. **Definitions** — only terms needed to interpret the document.
3. **Requirements** — one entry per named requirement, containing:
   - identifier, when needed for exact references;
   - statement;
   - acceptance evidence;
   - source references;
   - dependencies or notes only when authoritative.
4. **Explicit non-goals** — established non-goals that prevent scope expansion.
5. Rejected alternatives, when relevant: authoritative decisions that explain the requirements or their boundaries.
6. **Review decisions and scope, when needed** — `NEEDS_PRODUCT_DECISION` items naming affected requirements or sources,
   clearly separated from the requirements themselves.
7. **Source and coverage appendix** — map each source goal, constraint, and non-goal to named requirements, exclusions,
   `NEEDS_PRODUCT_DECISION`, or explicitly no requirement because it is a non-goal.

For a small scope, keep the document compact by combining sections, but retain identifiers in use, source traces,
and acceptance evidence. Do not require a separate review packet.

### 6. Check boundaries and completeness

Before presenting the draft, verify:

- no requirement lacks authoritative traceability;
- every established goal and supported constraint appears in coverage;
- concrete permitted and rejected cases preserve the governing sources and product decisions; apply `spec-review`'s [check for unsupported restrictions](../spec-review/references/non-narrowing.md) to flag uncertainty about which cases qualify and unsupported restrictions, not merely check citations; this focused check does not start a full specification review;
- non-goals are not accidentally restated as scope;
- material unsupported choices affecting requirements are `NEEDS_PRODUCT_DECISION`; optional suggestions remain clearly separate from requirements;
- defaults, errors, compatibility, trust, performance, and operations are included only where supported;
- wording is observable and solution-neutral;
- implementation specification has not begun;
- identifiers, numbers, exact errors, and unresolved uncertainty were preserved.

Report inspected sources, excluded or unresolved items, and any ambiguity that prevents a reliable requirement. Do not claim complete coverage when a source was unavailable or conflicting.

### 7. Present the draft

Present the requirements as a draft, with unresolved decisions and coverage limits.
Request approval when the task or project's process requires it; otherwise delivering the draft completes the request.
Do not proceed to implementation specification or implementation from this skill.
Approval of the requirements is not approval of an implementation.

## Output rules

A valid completion consists of the requirements draft and any unresolved decisions or coverage limits.
If a prerequisite blocks part of the draft, identify the affected requirements and precise missing authority or decision.
If the work reveals a material unsupported choice affecting a requirement, retain `NEEDS_PRODUCT_DECISION`
rather than guessing; keep optional proposals clearly separate from requirements.
