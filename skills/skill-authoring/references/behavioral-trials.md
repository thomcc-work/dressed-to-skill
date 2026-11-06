# Behavioral trials

Read this reference before arranging behavioral evidence about a prompt or skill change, including passive observation, or preparing paired behavioral or summarization trials.
Skill edits and textual reviews do not require a trial by default.
Use the current system's evaluation facilities when available and authorized.
If execution is unavailable, inspect the cases directly and report textual findings;
do not count that review as observed behavior or independent evaluation.

## Choose what to test and what the result would establish

State which decision the trial is meant to inform and what observation would change that decision.
Distinguish a useful answer, a changed research action, and reliable compliance; they require different evidence.
For a failure-driven comparison, begin with the failure task and a nearby control before adding variants or domains.
For a fresh paired comparison, run the baseline first.
Verify that it reaches the decision being tested before expanding the comparison.

If the baseline does not reproduce a failure, do not credit the revision with fixing it.
Choose one of these outcomes:

- Repeat a bounded comparison.
- Assess a different observed behavior explicitly.
- Stop and report an inconclusive result.

When the next decision depends on consistency, repeat the matched comparison before widening the task matrix.
When it depends on transfer, add a task outside the originating domain instead.
Repetition does not separate the instruction change's effect from changes in retrieved results, task state, or which instructions the agent received.

## Test the instructions as the agent is meant to receive them

Test instructions through the delivery path whose behavior matters: startup injection, an explicit file read, or a task message.
For claims about deployment in root sessions, use fresh or correctly reloaded root sessions with the normal startup path.
Do not require root sessions when worker, continuation, or handoff behavior is the subject of the trial.
Inspect the effective instructions in both conditions, including automatic context injection, before interpreting their outputs.
A complete read result establishes that the agent received that text, not that the text had system-instruction priority or loaded automatically at startup.
Check that the baseline has not inherited the revised rule through another instruction source.
If the deployment path cannot be tested, a bounded explicit-load or worker comparison can still provide useful observations.
Report that substitution and limit the conclusion; do not describe it as a deployment test.

## Observe ongoing work

When observing ongoing work to judge whether guidance helped, inspect the existing transcript, artifacts, and ordinary completion events.

Do not announce the evaluation or disclose its criteria to the observed agent.
Do not request evaluation-specific reports from that agent.
When a result is not yet available, wait for normal completion evidence rather than asking the observed agent to produce monitoring callbacks.

When authorized to intervene in the observed task, deliver the changed instructions and request that they be loaded
when needed to establish exposure.
Keep that notice separate from evaluation instructions, and verify from the resulting record that the agent loaded them before judging behavior.

If the task needs further coaching or intervention, provide it within the existing authorization, but record it as an additional influence.
Do not attribute subsequent improvement to the prompt or skill change alone.
When passive observation cannot provide enough evidence, report that limit rather than changing the observed workflow merely to make evaluation easier.

## Replay and paired trials

### Preserve history and isolate state

For trials based on a past session, use a conversation fork or replay at the decision point if the current system
supports it and can preserve the original session and isolate replayed actions.
If unavailable, use a new task grounded in the failure or inspect the recorded evidence directly.
Label that result as a fresh trial or textual review, not a faithful continuation of the original session.

For a faithful continuation, preserve its actual messages, tool calls, and tool results.
Do not replace them with a summary or a new user message quoting the history.
Protect the original session and real user state from replayed actions.
Use disposable resources for state those actions can modify.

A conversation fork preserves messages, not filesystem or runtime state.
Relevant inputs can include current source files, unsolicited messages, and automatic context injection.

### Choose where the replay begins

Trace the failure backward to the earliest unsupported inference or commitment the test asks a fresh continuation to make.
Begin before that choice while retaining the feedback needed to reach it; the last user message is not automatically the right starting point.
Include preceding diagnostic results, user corrections, and recorded compaction when they occur before the chosen judgment.
Do not include the original faulty plan or action when testing whether the continuation independently chooses it.
A later-stage trial of carrying out an existing plan measures follow-through, not independent choice; label it separately.

### Choose the state and handoff method for the tested behavior

Use the instructions and context actually handed to another agent instead only when that handoff or the receiving agent's behavior is itself the subject of the trial.
A handoff trial does not establish how the original agent would continue or whether its decisions improve.
If the original session is unavailable or cannot be resumed, report that limitation and label reconstructed inputs as an approximation.

Preserving history and isolating changes do not by themselves require reconstructing the historical filesystem.
Start with the closest available runnable state that preserves governing requirements and the evidence available at the chosen judgment.
Restore relevant historical state when the comparison question requires it; otherwise disclose differences and their possible effects.
For failure reproduction, try this condition before recovering unrelated environmental details.
If a condition fails its reproduction check, use the trace to identify a concrete missing input or execution difference.
Restore the missing input or relevant execution behavior if another reproduction attempt is warranted.
Freeze each changed condition and report its counts separately.
Once the failure meets the chosen repeatability check, stop reconstructing historical state.
Proceed to the requested comparison or minimization.
If the evidence identifies no further difference that can be corrected, report the reproduction limit rather than repeat unchanged trials just to obtain a failure.
A bounded revised-only replay may use recorded earlier outputs for comparison; report it as a quality observation, not a controlled experiment.
Do not block that replay solely because a fresh baseline is unavailable.

### Verify the instructions loaded before judging continuation

Verify that the updated instruction body successfully loaded before treating a continuation as evidence about its behavior.
Inspect actual actions and outputs; investigate a failed check before expanding the replay.
A reload, a read attempt, or a completed answer alone does not establish that the agent received the updated instructions.
Inspect the full relevant continuation, including earlier responses and actions at the tested decision.
An interface that shows only the latest final response may hide those earlier outputs.

Preserve normal coordinator tools and native completion delivery when assessing delegation, coordination, or latency.
Removing tools can force extra delegation; manually passing results between agents can introduce pauses absent from the real workflow.
If isolation changes either, record the differences and do not attribute the resulting delegation or waiting to the guidance under test.

For paired behavioral trials, fix the comparison question, outcome criteria, replay starting point, model, and task inputs before generation;
vary only the instruction change under test.
Inspect the exact worker inputs and keep reference outputs and later diagnoses out of them.
Judge actual decisions and actions afterward, not just formatting or workflow compliance.
For outcomes that depend on several causes and effects, distinguish evidence for each cause and its effect from evidence that they occur together.
Do not require one example to demonstrate every cause and effect when separate evidence could already change the assessment.
Separate examples do not establish the combined outcome.
Separate recorded actions from verified source support.
Search queries and page-open records show research targeting, not everything retrieved or read.
An independent post-run source check can support an answer's factual claims, but cannot establish that the worker performed the same investigation.

For a failure-driven revision, use the inputs available at the recorded failure decision point.
Include a nearby control that should retain its existing path.
For example, pair a decision about replacing custom profiling instrumentation with an obvious mechanical repair that needs no redesign.
Test whether the new guidance changes the failure decision without adding unnecessary steps to the control.

## Example: revising an artifact-writing skill

Suppose an introductory README task requires a whole-document reading-quality score of at least 3.
Choose a difficult README and a nearby case that the previous skill handled well before generating a large batch.
The new draft may explain one mechanism through a satisfying example while the remaining configuration inventory still makes the complete reading experience a 2.
That is a useful passage-level improvement, not acceptance of the complete artifact.
Generate and judge the control again under the revised skill; its saved earlier 3 does not establish what the revised skill produces.
If the new control is a 2, withhold a broad success claim and inspect the actual prose before expanding the batch.
One generation does not establish that the skill caused the difference rather than sampling variation.

Keep three comparisons distinct:

- The original document establishes whether the revision improves on what the user already had.
- An earlier skill's generated output preserves a usable partial result and evidence about that earlier condition.
- A freshly generated control tests the revised skill on a previously successful task.

Without the original-document comparison, report acceptable candidate quality rather than demonstrated improvement over the original.
A skill change does not erase an earlier useful artifact, but its score cannot stand in for newly required evidence about the changed skill.
Use the governing task to determine which acceptance checks need rerunning; this example does not require every skill edit to regenerate every historical output.

## Report scope and cost

For each variant, report task outcomes alongside token use and elapsed time where available.
Include tool and review overhead when they are part of the compared workflow; separate shared experiment setup from execution cost.
Assess the added skill against the existing workflow.
If costs are unmeasured, report quality observations without claiming efficiency or net benefit;
one task does not establish general reliability.

For summarization trials, distinguish incremental replay (previous checkpoint plus subsequent history)
from blind reconstruction (preceding raw history without reference summaries or later critique).
Blind reconstruction must restore the underlying raw history, not merely delete the previous checkpoint.
These are different tasks; do not describe their outputs as a comparison using the same inputs.
