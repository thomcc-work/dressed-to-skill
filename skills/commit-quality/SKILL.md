---
name: commit-quality
description: Write or review commit messages, split work into atomic commits, and prepare a finished change for commit. Use whenever creating commits, deciding commit boundaries, proposing messages, or judging commit quality.
---

# Commit Quality

Write for the next person who will debug or review the change. Use a concise, imperative subject that names the affected behavior; do not merely label the diff.
Assume readers know the project but have not seen this conversation or its planning notes.
Describe the actual change and its reason, using [descriptive names](../holistic-writing/references/editorial-pass.md#use-descriptive-names)
rather than conversation-local task labels.

Follow the user's and repository's rules for staging and committing.
Writing or reviewing a commit message does not authorize either action.
A local commit does not authorize pushing or other remote changes.

If the diff does not make the reason, failure mode, constraints, or verification obvious, explain the relevant points in the body:

- the user-visible or operational problem;
- why the previous behavior was wrong;
- the important design choice or constraint behind the fix;
- verification only when it records non-obvious evidence, an unusual choice of where to observe the tested behavior, or a material limitation.

Record only what a reader would otherwise have to reconstruct. Do not narrate files or repeat the subject. Do not append a routine `Verification:` section or command list. Ordinary test, lint, and formatting results belong in the review report or CI record, not the commit message.

For bug fixes, explain how the cause leads to the symptom. For tests, say what regression they would have caught. For security changes, state who or what gains or loses permission to do what, and why the checks that enforce those permissions remain sufficient. Mention verification when it establishes something durable and non-obvious, such as reproducing a bug in production, a migration result, a compatibility limit, or a test environment that future readers might otherwise assume was covered.

Before committing, inspect the complete diff. Then write the message to describe the finished change.

## Atomic commits

Divide the changes you are responsible for by purpose before committing. Each commit should be independently coherent: it establishes one behavior, invariant, migration step, or policy change and includes the tests and documentation needed to make that result complete.

Do not confuse atomic with small. Keep inseparable behavior, tests, generated artifacts, and user-facing documentation together. Separate changes that can be reviewed, reverted, or explained independently; never absorb unrelated pre-existing work merely to leave a clean working tree.

Inspect `git status`, `git diff`, and `git diff --cached` before staging.
If the index contains unrelated work, coordinate before changing it or committing.
For files with mixed edits, use `git add --patch -- path/to/file` to select only your hunks.
If the edits cannot be separated safely, ask before proceeding; do not discard someone else's work.
Review the complete `git diff --cached` before committing, then check the remaining working changes afterward.

Order commits so every intermediate revision is valid under the repository's required checks. Preparatory refactors must be useful and behavior-preserving on their own, not incomplete pieces whose only justification appears in a later commit.

## Paragraph breaks

With only the intended changes staged, pass each paragraph as a separate `-m` argument
so Git inserts real blank lines:

```bash
git commit \
  -m 'Fix clipboard publication' \
  -m 'Explain the failure mode and design choice.' \
  -m 'Record any verification that matters later.'
```

Do not write `-m 'First paragraph.\n\nSecond paragraph.'`; ordinary shell quotes preserve `\n` literally.
For a generated message, write actual newline bytes to a temporary file.
Check that generation succeeded before passing its path with `git commit --file <path>`.

After committing, inspect `git log -1 --format=%B` to verify the saved message and paragraph breaks.
