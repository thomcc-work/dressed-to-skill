---
name: autonomous-work
description: Pursue an explicitly requested autonomous or unattended task, or an active user-authorized tracked goal, through verified completion. Use for implementation, research, writing, planning, or review, including resuming an established run. Do not use for an ordinary request without permission to work autonomously, passive goal tracking, or a paused, blocked, or budget-limited goal alone. Preserve the requested activity; autonomy does not authorize implementing a plan, fixing review findings, publishing writing, or other unrequested effects.
---

# Autonomous work

Before starting, confirm either an explicit request for an autonomous run or an active, user-authorized tracked goal.
An active goal authorizes work only within its objective.
An ordinary request for a fix, answer, draft, plan, or review does not authorize an autonomous run.
Reassess activation when the task changes; having this skill in context does not activate it for the next task.
Respect paused, blocked, and budget-limited states and the current system's resume requirements.
An inactive goal is saved state, not permission to continue.

This skill determines when to start, continue, save progress, and stop, and which acceptance conditions must be met first.
[Work-selection](../work-selection/SKILL.md) determines what to do next, which dependencies are necessary, and when to reconsider or investigate an approach within the authorized task.
Activity-specific skills define their procedures; use goal tools for status changes and budgets.
Autonomy authorizes persistence within the task, not a different activity or additional effects.

## Establish what is authorized and what must succeed

Read the request, governing requirements, repository guidance where applicable, and current artifacts or evidence.
Before starting, identify the permitted activity, protected work, acceptance criteria, and authorized effects:

- **Implementation:** deliver the requested behavior through its intended consumer and required checks, within the authorized change scope.
- **Research:** answer the agreed question from evidence, distinguishing supported conclusions, conflicting sources, and unresolved uncertainty.
- **Writing:** produce or revise the agreed artifact against its brief and factual requirements; drafting does not authorize publication.
- **Planning:** produce a usable plan supported by evidence, with dependencies and uncertainties; planning does not authorize execution.
- **Review:** complete the agreed inspection and substantiate findings; review does not authorize repairs.

Do not invent human approval or substitute a different activity for an unmet result.
A review-ready artifact can complete a draft request, but not a goal that explicitly requires the user's approval.
Do not ask again for investigation, edits, or repairs the task already authorizes; a failed attempt does not impose a one-attempt limit.

Derive remaining outcomes from the full governing request, not from worker assignments, progress summaries, or optional cleanup.
A narrower investigation does not narrow the goal or milestone.
Follow the required acceptance order.
For the next unmet condition, identify its observable result, current evidence, missing work, and cheapest realistic check.
Use the task's actual criteria: sources and reasoning for research, the brief for writing, feasibility for planning, inspection evidence for review, and consumer behavior for implementation.
Keep each condition open until its required evidence passes; an explicitly scoped feasibility or component result does not complete downstream obligations.

Use existing goal, plan, or session state; do not create another tracking system.
Record acceptance cases before substantive work, and refine them only within the governing scope.
Read-only work may retain state in the session; recording progress does not authorize project-file edits.
Create a tracked goal only when explicitly requested; unavailable goal tools do not prevent an otherwise authorized run.

At run startup, consider delegating substantial work or independent investigation and review.
Assess responsibilities from the original request before adopting a diagnosis or implementation approach.
Repeat that assessment when a distinct workstream begins, reviewing and adjusting existing assignments instead of automatically spawning a new team.
This assessment does not change the permitted activity or authorize additional effects.

## Organize remaining outcomes

### For multi-outcome goals

For an authorized autonomous goal with multiple independently verifiable outcomes or dependent workstreams,
use the current system's existing planning facilities to organize the remaining work.
Use [goal-to-issue-graph](../goal-to-issue-graph/SKILL.md) only when the user explicitly selects that local TicGit workflow.
TicGit is not a prerequisite for an autonomous run; its absence does not authorize using a remote tracker.
Check existing plans or graphs against current instructions and permissions, work products, and evidence before using them; do not blindly follow a stale task list.
Cover root acceptance, remaining outcomes, genuine dependencies, and integration checks appropriate to the permitted activity.

### For a single bounded task

A single bounded task may use its existing acceptance criteria without a graph.

### Planning rules

Use permitted existing goal, plan, or session state; this requirement neither mandates a new tracking system nor authorizes tracker mutation or project-file edits for read-only work.
Maintain a selected local graph within the authorized scope. Remote tracker changes require explicit user direction.

Initial investigation may precede decomposition.
Keep downstream work provisional where discovery or an unresolved choice can change it; do not require an exhaustive audit before the first consumer path.
As evidence or the approach changes, update or supersede obsolete tasks and dependencies while preserving the governing outcomes.
Working from the graph means advancing an unmet root outcome and closing work when evidence shows it is complete, not following abandoned approaches or treating revisable agent assumptions as user requirements.
Graph work does not expand scope, change the authorized activity or effects, or resume an inactive goal.
When selected, the graph skill owns decomposition; work-selection still owns the next action.

## Select work within the authorized run

Use [work-selection](../work-selection/SKILL.md) to choose the next action, justify dependencies, and compare continuing with other authorized approaches.
Also use it before extending repeated similar batches during an active run, even when they succeed.
Keep unmet acceptance conditions and what each blocker prevents visible while advancing independent authorized work.
Continue integration and accept results only when the required prerequisites and evidence permit.

## For implementation work only

For implementation work, use these companion procedures when their conditions apply:

- Use [change guidelines](../references/change-with-evidence.md#design-choices) for unresolved modeling, interface, ownership, or invariant decisions, and [testing guidance](../references/testing.md) for test-strategy choices.
  For an established pattern, follow the surrounding code and tests without another design procedure.
- [Review evidence standards](../references/review-evidence.md) distinguish local/component checks, integration, and required real-input evidence.
  Consult them for milestone readiness.
  A routine localized change needs a diff review and appropriate native checks, not a full audit.

For an implementation acceptance case, identify the actual entrypoint, authoritative inputs, intervening interfaces, final consumer, and cheapest realistic check.
Require end-to-end evidence unless the governing scope explicitly declares a feasibility or component milestone.
Do not replace that condition with a helper's local success.
Before adding more prerequisites or capabilities without a new result the intended consumer can use, attempt the closest check through that consumer.
If it cannot run, identify the missing dependency and use work-selection to compare repair with the smallest authorized alternative.
Connect each component's output to the intended consumer or remove the temporary path before adding another capability that works only with fixtures.
If a repair displaces integration, retain integration as the next action for that acceptance condition.
If blocked, retain downstream obligations rather than silently deferring them.
Missing real inputs do not block integration using valid fixture inputs, but fixtures do not satisfy requirements for real-input evidence.
Where acceptance permits partial results, keep unsupported cases explicitly held while supported cases reach the consumer.
This does not narrow the milestone or certify held cases.
Reuse producer outputs that remain valid for the required consumer and repair the failing boundary; regenerate only invalidated or missing work.
Record implementation results as integrated, local-only, or blocked with the exact check and evidence.

Commit only when the task or repository policy authorizes repository changes and commits; use [commit-quality](../commit-quality/SKILL.md).
When commits are authorized, commit integrated results rather than waiting until the end of the session.
Do not turn read-only research or review into repository mutations to satisfy an implementation procedure.

## Record decisions and preserve resumable state

Record corrections, constraints and their sources, failed approaches, and decision-changing untried alternatives in existing authoritative task state.
Use [descriptive names](../holistic-writing/references/editorial-pass.md#use-descriptive-names)
for goals, tasks, milestones, and decisions in saved state and progress reports.
Follow the current system's normal memory and history practices; this skill does not introduce storage locations,
additional memory files, or a separate task database.
Keep governing requirements distinct from revisable agent choices in saved state; summaries must not promote the latter into user instructions.
Record user decisions before delegating work that depends on them, and update superseded holds, questions, and worker instructions without dropping constraints that still apply.
Do not rely on compaction to retain everything needed to resume.

### Preserve state and resume

When preparing a checkpoint or handoff through the current system's existing facilities, preserve:

- the governing objective, permitted activity and effects, and protected boundaries;
- unmet acceptance conditions, next actions, and integration displaced by repairs;
- what each blocker prevents and which other obligations remain;
- evidence already obtained and references to work products, with what they establish;
- assumptions, pending decisions and effects of workers' actions, and checks needing rerun.

Persist only state expensive to reconstruct and use a permitted existing surface.
Reference existing acceptance records and results rather than copying their contents into another task database.
A recovery checkpoint preserves state; it does not create a human approval requirement or stop instruction.
On resume, read that state and update it to reflect later user instructions before choosing work.
Before recording a summary's assertion that the user stopped work or required approval, recover its source message or authoritative goal state and check what it applies to.
If that source is unavailable, state the uncertainty rather than attributing the restriction to the user.
Ask for clarification only when uncertainty about permission affects the next action; continue independent authorized work.
Respect actual human stops and the current system's pause, block, budget, and resume controls; a missing citation is not permission to bypass them.
Check current artifacts, pending workers, and evidence freshness; do not replay completed mutations or trust stale summaries over current state.

## Ask, block, pause, or finish honestly

"Autonomous" does not mean the user is gone; it means they are not actively paying attention.
Ask the user for missing decisions and continue independent authorized work while awaiting an answer.
Do not guess missing semantics, invent approval, or certify held results.

Before declaring the run blocked, compare the dependency with the full objective and governing requirements.
Record what it prevents, supporting evidence, the input or decision needed, and independent work that can proceed.
A blocked investigation is not a blocked goal; continue useful authorized work when only one path is blocked.
Distinguish a missing external dependency from an in-scope repair or an unavailable tool for which an authorized alternative exists.
Use [creative-inquiry](../creative-inquiry/SKILL.md) if another approach could reach the same outcome with fewer assumptions.
Declare the whole run blocked only when no meaningful authorized progress remains, then explain the dependency.

At completion, compare the actual result with the original request and acceptance cases using the permitted activity's evidence standards.
Require concrete evidence for every explicit requirement and no required work remaining.
For completed implementation, apply the review threshold above.
For research, writing, planning, and review, verify the requested answer or artifact without executing the proposed work or repairing findings unless separately authorized.

If only externally blocked obligations remain, report partial completion, exact blockers, and the next possible action.
If interrupted by time, budget, or tool failure, report paused work and preserve the next action.
Neither state is completion; do not spend the run on unrelated cleanup or change goal status outside its controls.
