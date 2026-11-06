---
name: opportunity-scan
description: Find the highest-leverage project improvement without anchoring on recent changes, current work, churn, or problems that have already been fixed. Use for broad codebase improvement, project opportunity scans, and deciding what to work on next; not for designing a solution within an already-selected area.
---

# opportunity-scan

## Purpose

Find high-leverage opportunities across an entire software project without anchoring on whatever was touched most recently.

Use this skill for broad goals such as “make this project better”, “what should I work on next?”, or “find the highest-leverage improvement”. Its job is to choose *where to look*, not to design the solution.

## Core rule

Recent activity is evidence of attention, not evidence of importance.

Do not begin from the latest commits, current diff, open branch, or the subsystem already occupying the parent conversation. First build a coarse map of the project and deliberately search across it.

Do not limit possible improvements to open issues, TODOs, roadmap items, or recent work. First identify improvements that are not already explicitly tracked. Afterward, consult tracked work to detect overlap, supporting evidence, or neglected known problems.

## Inputs

- broad project-improvement goal
- explicit user constraints or priorities
- repository contents and documentation
- repository history when available
- issue/bug/performance/user evidence when available

## Procedure

### 1. Map the project before ranking opportunities

Construct a coarse subsystem map from sources such as:

- top-level source directories and packages;
- architecture/design documentation;
- public APIs and user-facing commands;
- tests and integration suites;
- build/deployment tooling;
- major runtime components;
- long-lived modules visible in repository history.

Aim for roughly 5–12 meaningful areas. Do not make every directory its own subsystem.

For each area, record only enough to orient later investigation:

- purpose;
- major interfaces or responsibilities;
- whether it is user-facing, infrastructural, or internal;
- rough evidence sources available.

### 2. Neutralize recency bias

Before inspecting recent work in detail, sample evidence across the project.
Treat the current working area as one candidate area, not the default candidate.

When repository history is available:

- inspect multiple time windows where history allows, rather than only commits close to HEAD;
- inspect areas with low recent churn as well as high churn;
- distinguish repeated historical pain from a one-off recent refactor.

If history is missing or too short for those comparisons, continue by sampling current code, tests, and documentation
across subsystems.
Use dated issues or other available records for historical evidence, and state what could not be checked.
Do not infer age, churn, or recurrence from missing history.

If practical, define a recent window such as the last 30–90 days. Evidence confined to that window should not by itself justify “highest leverage”.

Do not mechanically penalize recent work. A recently touched subsystem may still be the best opportunity when there is independent evidence: repeated historical failures, user pain, known architectural limits, or unfinished high-value work.

### 3. Look for evidence of possible improvements

Search each major area for evidence such as:

- recurring bugs or regressions;
- repeated cross-module edits or awkward coupling;
- known performance or scalability limits;
- user-facing limitations or missing capabilities;
- fragile or weakly enforced invariants;
- disproportionately complex interfaces;
- duplicated mechanisms;
- maintenance hotspots that recur over long periods;
- neglected important subsystems with little ownership or test coverage;
- capabilities the architecture makes unnecessarily difficult;
- places where a small change would remove recurring work elsewhere.

Do not equate churn with pain. Churn can mean investment, healthy evolution, generated code, or mechanical migration.

### 4. Verify that the problem remains

Before shortlisting an area, confirm that the problem still needs work in the current tree,
regardless of where the evidence came from.

For each candidate:

- inspect current design documents, implementation, tests, and open work;
- identify the concrete behavior, invariant, capability, or cost that remains unresolved;
- distinguish problems already fixed from those that remain;
- check whether recent changes already removed or materially narrowed the problem;
- name the smallest experiment, reproduction, or audit that would establish how much an improvement would help.

Do not shortlist an area on historical recurrence alone.
If the current implementation already enforces the proposed invariant, report that it already works or identify a narrow follow-up rather than treating it as a project-level opportunity.

### 5. Produce a cross-project shortlist

Return 3–5 opportunity areas from distinct subsystems when the evidence supports it.

Each opportunity should state:

- the area;
- the concrete current problem or limitation;
- why it matters;
- evidence supporting it;
- existing design, code, tests, or corrective work;
- why it may be high leverage;
- important uncertainty;
- the cheapest check that could disprove or narrow it;
- whether the evidence is recent-only, recurring, user-facing, architectural, or mechanical.

When available evidence identifies the most recently active subsystem, at least one shortlisted opportunity
should come from outside it unless there is a concrete reason no such opportunity is competitive.

### 6. Rank cautiously

Rank opportunities only after constructing the shortlist and verifying that each problem remains.

Prefer, roughly in this order:

1. repeated or independently corroborated problems for users or with reliability;
2. constraints that block multiple valuable changes;
3. recurring maintenance burden or invariant failures;
4. simplification that substantially benefits the components or people that depend on it;
5. speculative cleanliness or aesthetic improvement.

Do not give recent activity an intrinsic positive score.

If the evidence does not support a clear winner, return a small ranked set rather than manufacturing certainty.

## Output

Use a compact structure like:

```text
project map
- parser: ...
- incremental engine: ...
- build-rule DSL: ...
- watcher: ...
- docs/tooling: ...

opportunities
1. <area>: <current problem>
   evidence: ...
   existing work: ...
   remaining gap: ...
   leverage: ...
   uncertainty: ...
   check that could rule it out: ...
   evidence covers: recurring | historical | recent-only | user-facing | ...

2. ...

recent-work check
- most recently active area: <x, or unknown>
- shortlisted because: <independent evidence> | not shortlisted

recommended next investigation
- <area>
- why this beats the alternatives
```

## Handoff

This skill chooses an opportunity area; it does not choose an architecture.

After selecting an area:

- use `pain-axis` to investigate its historical failure/coupling evidence in depth when useful;
- use `architecture-design` when a bounded subsystem and architectural problem are selected; its optional alternatives reference covers unresolved choices between designs;
- use a smaller local workflow when the opportunity is already concrete and does not require architectural exploration.
