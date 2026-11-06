---
name: dependency-review
description: Review third-party dependencies and externally sourced tooling when a task proposes adding, updating, replacing, pinning, or vendoring a library, package, framework, plugin, action, CLI, toolchain, binary distribution, container image, or package manager. Do not use merely to inspect or use an unchanged existing dependency, action, tool, binary, or image.
---

# Dependency Review

## Establish need and installation path

Apply [decision authority](../references/change-with-evidence.md#decision-authority)
when establishing why the dependency is needed.

For review-only work, inspect available evidence and recommend whether to proceed.
Do not add, install, pin, or vendor dependencies unless those changes are also authorized.
Report checks that would require those changes as unperformed.

An implementation task that reasonably requires a dependency authorizes adding it through an existing mechanism,
within the user's and repository's constraints.
When making an authorized change, add dependencies through the owning component's existing package manager.
Obtain external tools and artifacts through the repository's existing installation or image mechanism.

Do not introduce a package manager or installation mechanism solely for one dependency.
Ask first when the owning component has none.

## Check how the selected dependency reaches its consumer

Before selecting or changing a dependency or external artifact, identify the source, lockfile, installer, or image that selects it, and known consumers that update independently.
Trace the proposed update to its intended consumer; changing test dependencies does not establish that the deployed software uses the new version.

## Review and verify

Review its source scope, maintenance activity, release provenance, known security concerns, and compatibility in proportion to its authority and risk.
Prefer primary sources; inspect the source when the dependency is small or receives significant authority.

When making an authorized change, pin or lock the selected version according to repository conventions.
Then verify the installed artifact, image digest, or lockfile and exercise the behavior that required it.
