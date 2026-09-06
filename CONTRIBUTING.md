# Contributing to FoldSpace Orchestrator

Contributions should make the protocol clearer, more consistent, and easier to
adopt honestly. This is a documentation project, not an executable agent
framework. See the [README](README.md) for its scope and the [MIT License](LICENSE)
for the terms under which it is distributed.

## Useful contributions

Corrections, clearer navigation, bounded examples, better explanations of
failure modes, and evidence-backed host-specific observations are welcome.
For a material policy change, describe the problem and affected contracts
before proposing a broad rewrite.

Do not add speculative runtime code, installers, workflows, dependencies, or
empty generated project-state templates as though they were already part of
FoldSpace. A proposed expansion of product scope needs explicit discussion.

## Keep the references and guides consistent

The four uppercase root documents are the canonical detailed references.
They were published unchanged from the supplied revision 2.0 archive dated
6 September 2026. The README and `docs` guides orient readers; they should not
silently introduce competing policy.

Avoid incidental reformatting, encoding changes, or line-ending normalization
in the originals. `.gitattributes` preserves their bytes. If a canonical
correction is intentional, identify the source section, explain the change,
and keep revision/provenance notes and affected guides consistent. Do not keep
claiming byte-identical revision 2.0 content after an intentional source revision.

Preserve relative links when moving files. Check local targets and heading
anchors, fenced blocks, tables, and Mermaid rendering. Keep filesystem paths
in PowerShell examples Windows-style. Distinguish project-specific
`docs/ai` outputs from files actually shipped in this pack.

## Make claims that the evidence supports

Describe intended benefits as mechanisms, not guaranteed outcomes. Do not
invent speedups, supported versions, native commands, tool names, or universal
host compatibility.

For a capability observation, identify the relevant host context and what was
actually demonstrated without publishing private configuration. Distinguish
documented behavior, configured behavior, local exercise, intended-runtime
verification, and blocked checks. Document assisted/manual alternatives and
their limitations.

Keep ownership, authority, budgets, queue preservation, candidate-specific
evidence, and reconciliation-before-replay consistent across examples.
Prompts cannot enforce locks, wake idle sessions, recover inaccessible intent,
or guarantee exactly-once effects. Preparation is not release authorization.

## Protect private information and attribution

Do not include credentials, tokens, private keys, internal hostnames, real
private user paths, customer/organizational data, raw operational logs, private
conversations, or sensitive queue/checkpoint contents in commits, issues, or
pull requests. Use clearly fictional placeholders and minimal reproductions.
The small `.gitignore` is a convenience, not a secret-scanning control.

If you discover sensitive material, do not quote it in a public report. Remove
it from your proposed contribution and use an appropriate private reporting
channel available to you.

Submit only material you have the right to contribute under the project's
MIT terms. Preserve the existing license and applicable attribution. Use the
FoldSpace Orchestrator name consistently; do not add franchise quotations,
artwork, logos, or suggestions of official GitHub, Microsoft, or *Dune*
affiliation.

## Review expectations

Keep a contribution focused. Its pull request should explain the reader's
problem, changed files and source sections, any behavioral or compatibility
implications, and how the examples and links were checked.

For consequential policy edits, describe effects on active assignments,
ownership, prior authority, attempts/budgets, live operations, and migration.
Do not present a documentation-only change as demonstrated runtime enforcement.

Reviewers will look for grounded claims, consistent contracts, readable
examples, valid navigation, preserved provenance, and public-safe content.
There is no package build, test suite, or required installed documentation
linter in this pack. Use existing or native checks and inspect the rendered
Markdown; do not add tooling just to validate prose.
