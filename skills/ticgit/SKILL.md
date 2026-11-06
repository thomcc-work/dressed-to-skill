---
name: ticgit
description: How to use TicGit (`ti`) to track Git-native tickets in a local repository. Use when you need to interface with an existing local TicGit tracker or the user explicitly selects TicGit for the task. Does not select a tracker or authorize remote operations.
---

# TicGit Agent Guide

Use `ti` for planning, progress notes, triage, and resolving work within the authorized local tracking task.
Use plain `ti list` for compact tables, `--markdown` for detailed inspection, and `--json` for programmatic queries.
Use explicit ticket and writeup IDs; do not rely on current-ticket defaults.

Use the local store selected for the task; verify which repository it belongs to before writing.
If the store is unclear, ask the user to select it.
Check that the installed `ti` supports the commands needed for the task.
If `ti` or the store is unavailable, report the limitation and continue other authorized work using
the current system's existing planning facilities. Do not fall back to a remote tracker.
Do not install TicGit or initialize a store automatically.

## Basic Workflow

### Inspect a ticket

Inspect the assigned ticket.
Use listing to locate tickets when needed:

```sh
ti list
ti show <id> --markdown
```

### Choose work when authorized

Use `next` only when authorized to choose work, with filters appropriate to that scope.
For example:

```sh
ti next --assigned <email> --tag <tag> --markdown
```

Treat the result as a recommendation, not a persistent selection or reservation.
Inspect its assignment and blockers before starting; `next` can return blocked tickets and excludes child tickets.
It does not supersede an assigned task or coordinate ownership between agents.
Pass the ticket ID on every later operation, including work delegated to subagents.
Include the selected store's location with ticket IDs in handoffs and delegated work,
especially when implementation spans other repositories.

### Claim only when assignment is intended

Claim a ticket only when assigning it to the configured author and setting its status to open and state to assigned are both intended.
Claiming can reopen a closed ticket or replace an in-progress or blocked state; do not use it merely to announce that work starts.

```sh
ti claim -t <id>
```

Assignment and explicit ticket IDs do not reserve work for an agent.
Filter assignments explicitly with `ti list --assigned <email>`.

## Inspect An Issue Graph

Inspect tracker state, dependencies, and acceptance records:

```sh
ti list --state in-progress --subissues
ti list --all --subissues --json
ti show <id> --filter .comments
```

Include `--subissues` when listing the whole graph; the default list omits child tickets.
Use JSON to join tickets with their dependency IDs and identify unfinished prerequisites.
A ticket whose dependencies are closed is not necessarily authorized or ready to start; inspect its required inputs and the workflow it must follow.
`next` can recommend an in-progress ticket, so it is not an unclaimed-work queue.

### Establish whether the outcome is accepted

Distinguish whether dependencies are closed, what state the tracker records, whether work is running, and whether its results meet the acceptance criteria.
An in-progress state does not prove an agent is currently executing the task, and a closed dependency may be resolved, rejected, or a duplicate.
Read the authoritative acceptance record before reporting that the required outcome is met; `resolved` alone is not acceptance evidence.
For an overview, link to that record in its chosen home, such as ticket comments, a specification, or a linked artifact.

## Create And Edit Tickets

For new or substantially rewritten ticket titles and descriptions, use [holistic-writing](../holistic-writing/SKILL.md) before submitting them.
Tracker mechanics do not replace editorial review.
State changes, tags, and routine progress comments do not require that pass.

Create a ticket from a UTF-8 file whose first line is the title and remaining lines are the description:

```sh
ti new -F ticket.md --tags bug,parser --markdown
```

Edit the title and description with the same file format:

```sh
ti edit <id> -F ticket.md
```

Supply files or explicit text instead of requesting an interactive editor.
`-F -` names a literal file called `-`; it does not read stdin.

## Progress Notes

Add comments with an explicit target and body:

```sh
ti comment -t <id> -- "found the failing case"
ti comment -t <id> -- "implemented fix; running the tests"
```

## State And Triage

Tickets have a broad status and a specific state:

```text
open: new, assigned, in-progress, blocked, review
closed: resolved, wontfix, duplicate, invalid
```

Useful updates:

```sh
ti state blocked -t <id>
ti state review -t <id>
ti close <id>
```

`ti close` resolves the ticket and records the configured author as `closed_by`.

## Planning Fields

Set priority, tags, estimates, or milestones only when the task or project workflow calls for them.
These are independent operations, not required setup steps:

```sh
ti priority -t <id> 2
ti tag -t <id> bug parser
ti points -t <id> 3
ti milestone -t <id> v1.0
```

Read existing requirements before implementing and clarify missing decisions when needed.
Use the ticket's `spec` field when it is the chosen home for those requirements or implementation notes.
Do not create a spec for every change or duplicate a maintained repository specification:

```sh
ti spec -t <id> -F spec.md
ti show <id> --filter .spec
```

## Dependencies

Track ordering constraints explicitly:

```sh
ti dep <blocker-id> -t <id>
ti dep <blocker-id> -t <id> --remove
```

`ti next` skips tickets whose dependencies are not closed; it does not require those dependencies to be closed as resolved.

## Writeups

Use a writeup when the task calls for a versioned draft, not as a required step before creating tickets.
Create a ticket directly for actionable work; use ticket comments for incremental observations about existing work.

Create and inspect a draft:

```sh
ti writeup new --title "Parser cleanup" -F writeup-body.md
ti writeup list
ti writeup show <writeup-id>
```

For `writeup new`, the file contains only the body; supply the title separately.
To revise the draft:

```sh
ti writeup edit <writeup-id> -F revised-writeup.md
```

For `writeup edit -F`, the first line is the updated title and remaining lines supply a new body version when present.
Alternatively, `--body` supplies a complete new body version without changing the title.
Neither form appends observations to the previous body; default `show` and promotion use the latest version.
Use `ti writeup show <writeup-id> --all` to inspect earlier versions.

Linking to an existing ticket and promotion into a new ticket are different choices, not required sequential steps.
To link a draft to existing work:

```sh
ti writeup link <writeup-id> <ticket-id>
```

To create a new ticket from the draft:

```sh
ti writeup promote <writeup-id>
```

Promotion creates a ticket and closes the writeup; use the returned ticket ID for later work.

## Boundaries And Failures

Store initialization, user-map administration, and tool/schema upgrades require explicit user direction.
Do not use `checkout`, interactive UI/editor, or self-update commands.

Local ticket work does not authorize imports, metadata transfer, or remote issue creation, updates, or closure.
Those operations require explicit user direction and verification of the source or destination and the selected scope.
Before remote issue changes, verify which repository or project is affected and which issue tracker it uses.
Do not infer the project's issue tracker from the local store's Git remote.
`ti sync` pulls and pushes TicGit metadata through Git; it does not synchronize GitHub Issues.
Reading remote issues as context does not authorize importing or publishing them.

A failed or disconnected mutation may already have changed metadata.
Inspect the affected ticket or writeup before deciding whether to retry; never retry automatically.

## Agent Practices

- Use explicit ticket/writeup IDs or unique prefixes.
- Read existing requirements and clarify missing decisions; add a ticket spec only when those requirements belong in the ticket.
- Comment when you learn something important or finish a meaningful step.
- Mark blockers with an explicit state update and dependencies with `ti dep`.
- Resolve tickets only after their acceptance criteria are met and verified.
