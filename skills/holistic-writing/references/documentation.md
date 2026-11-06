# Documentation

Use this reference for documentation-specific authoring decisions and usability or correctness reviews.
It supplements the guidance for writing complete documents; it does not start a separate workflow.
Routine additions to an established section need validation of changed text and links, not a review of the complete document.
Use `readme-writing` for an introductory README; it remains independently usable.
Use `reorganize-docs` for existing page splits, renames, consolidation, archives, or navigation redesign.
Follow [Documentation conventions and placement](../../references/documentation-placement.md),
even when keeping the existing destination.

## Establish the reader's task

Read the current page, the nearest index or introductory page, authoritative inputs, and representative examples of how the documented system is used.
Reuse the established reader, purpose, evidence, destination, and decisions when another procedure has already supplied them.
Identify whether the reader needs to learn, perform a task, look up facts, understand a design, or review a decision.
Establish which page will be authoritative for the new content and where it belongs; retain the destination in a review unless relocation is requested.
Do not select a design or author a human-owned product brief as incidental documentation work.

## Choose the form

Keep these needs distinct without imposing a fixed page template:

- **Tutorial:** guide a learner through a safe, successful experience.
  State what she will build or understand, prerequisites, and the safe starting state.
- **How-to:** help a competent reader accomplish a specific task.
  State the task, prerequisites, expected result, and important hazards.
- **Reference:** present accurate, neutral facts structured like the subject.
  State the covered system, version, scope, notation, and how to find an entry.
  Do not force motivation or design goals into neutral reference material.
- **Explanation:** develop understanding through context, reasons, examples, and consequences.
  Explain the problem, goals, and important non-goals before the proposal.

A design document combines explanation with requirements for what to implement and how to verify it.
For an already selected design or implementation spec, use [Design documents](design-documents.md).
That reference does not choose the design or impose its progression on other documentation.
Within a page, separate mixed reader needs with clear sections or links.
Route a multi-page split or navigation redesign to `reorganize-docs` rather than treating it as incidental prose editing.

## Make starting points and routes usable

Assume the reader opens the page directly months later.
State required background, prerequisites, authoritative inputs, and important limitations where needed to begin safely.
Use a glossary only when many project-specific terms interact; state the audience and assumed background when either is not obvious.
Make clear which page defines each concept and link from relevant starting points rather than copying its procedure.
Keep action-specific warnings beside the actions they govern: cost, destructive effects, and safety conditions must not be hidden behind links.
Check command references, examples, installation or migration instructions, and introductory pages for stale behavior.
Preserve exact commands, interfaces, paths, conditions, exceptions, and links needed to find instructions when revising.

## Validate the reader's workflow

Follow the intended reader's route from its starting state through the task or lookup to the expected result.
Check that prerequisites arrive before dependent actions and warnings before their hazards.
Check which pages are authoritative, which versions are supported, what limitations apply, and which decisions remain unresolved.
Successfully following the links and steps does not substitute for judging how the complete document reads.
Validate changed links, commands, and examples and the final rendered or compiled representation with applicable repository checks.
Distinguish reviewing whether readers can understand and use the text from verifying how the system works; report failed or unavailable checks, parts not checked, and remaining uncertainty.
Finish when the reader can start, find authoritative information, and complete the intended task without session context.
Review-only work reports findings and the smallest useful corrections without unauthorized edits.
