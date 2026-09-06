# Contributing to FoldSpace Orchestrator

Contributions should make the protocol clearer, more consistent, and easier to
adopt honestly. This is a documentation project, not an executable agent
framework. See the [README](../docs/README.md) for its scope and the [MIT License](../LICENSE)
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

The four canonical documents under `protocol`, `operations`, and
`reference` are the detailed references. Revision 2.0 was
published unchanged in commit `38e9ce2`; revision 2.1 reorganizes those files
and adds mandatory run configuration. The immutable source archive remains
historical evidence, not a claim that active files are unchanged.
The README and adoption guides orient readers; they should not
silently introduce competing policy.

Avoid incidental reformatting, encoding changes, or line-ending normalization
in the canonical documents. `.gitattributes` disables text normalization. If a canonical
correction is intentional, identify the source section, explain the change,
and keep revision/provenance notes and affected guides consistent. Do not keep
claiming byte-identical revision 2.0 content or current runtime verification
based on historical 2.0 review notes.

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

Preserve the mandatory pre-run interview across new/existing bootstrap,
discovery workers, manual dispatch, deployment, fallback models, and recovery.
Models and per-model reasoning bounds/defaults need explicit approval and
supported-value evidence. External calls default denied with separately scoped
consent. Budgets need approved units/caps or explicit uncapped opt-in;
reservations and consumption survive retries and handoff. A missing capability
must not become a false enforcement claim or a silent runtime default.

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

### Issue-linked publication

Use one public GitHub issue per distinct problem or change; reuse it across
related pushes rather than opening an issue for each push. Before publishing,
record the problem, public-safe evidence, expected behavior, root cause
(confirmed versus hypothesis), proposed fix, affected paths/revision, acceptance
criteria and known limits. Update it with the final fix as the work develops.

Include a non-closing `Refs #N` in related commits until scoped acceptance is
met. **Every related push requires an issue update** with before/after SHAs or
full commit links, the concrete fix and impacted files/revision, evidence
actually observed, and remaining blockers or unverified behavior. Include a
follow-up pinning or guide-only push too. If a commit already exists, link it
from the issue rather than rewriting published history. Name one publication
owner to post updates when contributors are coordinating, avoiding duplicates.

Keep the issue open until its scoped acceptance is met; close only the fixed
scope and identify any remaining work. Published policy and document checks
are not proof that an adopter loaded it or that a host runtime defect is fixed.
Never include private screenshots, paths, conversations, logs or credentials.

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
