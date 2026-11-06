# Documentation conventions and placement

Read before editing documentation, prose source, or agent instructions, or drafting GitHub discussions or comments.
This applies even when you already know which page covers the topic and where the new content belongs.
Choosing where to put content does not require a review of the complete document.
Restructuring existing pages or navigation belongs to `reorganize-docs`.

## Documentation

When changing behavior, update affected documentation, including code comments, in the same change.
For user-facing changes, check authoritative documentation, introductory pages, examples, command references,
and installation or migration instructions for stale behavior before declaring the work complete.
Do not duplicate guidance for reminder, reinforcement, or visibility.
Add a link from another starting page only when someone has failed to find the
guidance from there, and do not repeat the guidance there.

1. Name the reader and the decision, action, or understanding the content serves.
   Omit content with no such purpose; do not document a detail merely because it
   changed during implementation.
2. Read the nearest documentation index and the page that already covers the topic before choosing
   a destination. Prefer an existing task or subsystem page to a new page.
3. Match the content to its scope:
   - Root README: repository-wide orientation, common starting instructions, and
     routes to specialized tasks—not an inventory of subsystem internals.
   - Subsystem or task documentation: usage, prerequisites, observable contracts,
     hazards, recovery, and reader-relevant limitations.
   - Code documentation: caller-facing purpose and usage contracts beside declarations;
     implementation rationale, algorithm summaries, and non-obvious constraints beside the relevant code.
     Keep operator instructions and guarantees between independently maintained components in their documentation.
4. Link to the page that defines the guidance from relevant starting pages rather than copying its content.
   Keep safety constraints needed at the point of action; do not make a reader
   follow a link to discover that a command costs money or can destroy data.

For example, document compaction replay cost and failure recovery in operator
instructions. Keep a saved checkpoint offset's encoding beside the code that
reads and writes it; document the resulting replay limitation for operators. An
internal capture timeout belongs in a README only if readers need it to diagnose
or operate the system.

For a small addition to an established section, validate the changed text and links.
A new heading alone does not require a review of the complete document.
Use [holistic-writing](../holistic-writing/SKILL.md) for writing complete documents,
substantial revision, or editorial review, including documentation usability or
correctness reviews and prose outside documentation.
Its [documentation reference](../holistic-writing/references/documentation.md)
covers documentation-specific reader tasks, forms, prerequisites, and workflow checks.
Use `readme-writing` independently for an introductory README; no sequence of writing
skills is required.

## Prose source formatting

In prose source, use one sentence per line when rendering joins those lines into paragraphs, so diffs are easier to review.
For GitHub discussion or comment text where newlines become visible breaks, keep each prose paragraph on one source line instead.
When using sentence-per-line formatting, semicolons may count as a line break.
Try to keep those source lines under 150 columns wide.

## Agent instruction files

Use the repository's agent instructions to direct agents to the right documentation and correct their plans before they start work.
Include only rules that always apply within its scope, links to the authoritative task documentation,
and constraints that must change the agent's plan before further work.
