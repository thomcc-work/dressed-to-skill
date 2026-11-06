---
name: reorganize-docs
description: "Restructure existing project documentation or navigation, or review how its pages are organized and linked without editing. Use for organizing documentation, consolidation, splits, renames, archives, and reviewing how readers find linked documents. Not for choosing where a new paragraph or section belongs, polishing wording alone, or checking whether a documentation site builds or renders correctly."
---

# Reorganize Documentation

Improve how readers find and use documentation without losing policy, rationale, examples, or historical evidence needed by its readers.

Do not invoke this workflow merely to add a paragraph or section to the page that already covers its topic.
For review-only work, follow Read first, Observe, Diagnose, Verify, and Report within the selected documentation scope.
Skip Plan, Edit, and verification of changes not made; a review request does not authorize file changes.

## Read first

Within the selected documentation scope, discover and follow the target repository's development lifecycle, documentation entrypoint, prose and ownership rules, source-of-truth policy, and guidance for repository-local skills.
Read the nearest index for every documentation subtree in scope.
Follow the [documentation conventions](../references/documentation-placement.md) when editing.

Use the relevant skill or procedure for specifications, generated documentation, or public docs.
Use the [shared editorial pass](../holistic-writing/references/editorial-pass.md) to review the complete text when prose has been substantially revised.

## Observe

1. Inspect the working copy and protect unrelated changes.
2. Inventory paths, titles, headings, line counts, internal links, and the starting page that links to each group of current documents.
3. Identify broken targets, orphaned active pages, unlinked children, likely overlap, misleading names, mixed purposes, and archive roots that no active page exposes.
4. Read the starting pages first, then the pages that may have problems.
5. Search repository-wide for every path proposed for movement or renaming.

An unlinked page is not necessarily obsolete.
Determine whether it is active policy, reference, a decision record, a work note, or historical evidence.

## Diagnose

Classify each page by its primary reader need:

- Tutorial: learn through a guided sequence
- How-to: complete a concrete task
- Reference: look up exact facts or contracts
- Explanation: understand reasons, concepts, or tradeoffs
- Policy: follow repository-owned constraints
- Archive: retain historical evidence without presenting it as current guidance

When consolidating copied guidance, apply the [consolidation check](../holistic-writing/references/consolidation.md); record which page readers should rely on for each topic and preserve links from the pages where they start the affected tasks.
Organization is suspect when:

- One index mixes ordinary work, specialized authoring, maintenance, and release operations
- Several pages each define the same workflow or checklist
- One page mixes policy, procedure, reference, and historical design
- A page lists filenames without usable links or labels that name the reader's task
- Active-looking notes are orphaned, speculative, completed, or superseded
- Names describe implementation accidents rather than reader tasks
- A split adds navigation hops without giving the reader enough information to choose the next page
- Moving material to a reference page hides rules, decisions, safety constraints, or stop conditions needed every time someone follows the procedure

Fragmentation alone is not a defect.
Keep pages that cover a narrow topic when the pages linking to them tell readers when to use each one.
Do not split by line count alone.

## Plan

Before editing, state:

- Pages to preserve and which ones readers should rely on for each topic
- Pages to merge, split, rename, or archive
- Navigation, reciprocal links, and links to archives to add
- References that must move with renamed paths
- Any additional links readers will need to follow and how the linking pages will help them choose where to go
- For each proposed extraction, whether it contains required steps or reference material needed only under certain conditions
- Validation commands for each changed format

Prefer the smallest change that helps readers find the documentation or resolves which page to rely on for a topic.
Do not normalize unrelated names or headings merely for visual uniformity.

## Edit

1. Improve the page where readers start before adding deeper structure.
2. Group navigation by reader task or lifecycle stage.
3. Keep one canonical rule and replace duplicates with links.
4. Preserve split or moved text mechanically or section by section before refining it.
   When automating section extraction, use Markdown-aware boundaries or verify that headings inside fenced examples were not treated as document sections.
5. Keep mandatory sequence, decision rules, safety constraints, and stop conditions on the page where readers start the task.
   Move only material that can be read conditionally, such as catalogs, literal templates, extended examples, and variant-specific detail.
6. Describe links well enough that readers can choose the right page without opening each one.
7. Archive completed spikes, tentative notes, and superseded designs without presenting them as current guidance.
   Record the former path, archive date, known source date and author or commit, explicit unknowns, and why the record is historical.
8. Link the archive index from an appropriate active reference page;
   archived leaves may remain outside ordinary task navigation.
9. Update repository references in the same change, including agent instructions, skills, specifications, and generated owners.
10. Remove empty directories and disposable platform debris only within scope.

Do not archive unresolved work unless another current document or issue records that it still needs to be done.
Do not turn a historical decision into current policy without verifying that it still governs the repository.

## Verify

- Check Markdown link targets, active-page reachability, and whether each archive root is reachable from active reference navigation
- Review prose references such as "the command above", "below", and "the previous section" after moving content.
  Replace references that no longer identify the intended procedure with an explicit command or link.
- Search repository-wide for stale paths and old names;
  distinguish records of former paths from links or instructions that still use an old path
- Compare moved or split pages with the prior revision;
  account for policy, rationale, commands, examples, and warnings
- Explain where each removed block now belongs or why readers no longer need it, not merely whether it appeared in the old page. A block may move to another page, be omitted because the code defines an implementation detail readers do not need, or be deleted because it serves no reader decision, action, or necessary understanding. Name the new page or reason; do not silently discard required instructions or historical constraints.
- Expect introductions, relative links, headings, and statements about which pages define rules to change. Investigate unexplained omissions rather than automatically restoring old detail.
- Read each common starting page alone first;
  confirm it still contains every rule needed to begin, decide, act safely, stop, and validate
- Then follow its links and judge whether readers can more easily choose the material needed for their circumstances, not merely reach it
- Run the smallest format-specific lint or compile check for each affected part of the documentation
- Inspect the final diff for formatting-only churn and unrelated files
- Obtain review of the current changes when they are broad, affect several areas, or move where policies are defined

## Report

For review-only work, report prioritized navigation and supporting-page findings, evidence, proposed corrections, and inspected or unverified scope.
Distinguish proposed changes from edits actually made and textual review from checks performed.
For restructuring work, report how the pages were reorganized and which ones readers should now rely on for each topic, which pages were archived and where they came from, validation results, areas deliberately left unchanged or not checked, and any material now one click farther away.
