# Getting started with FoldSpace Orchestrator

**Open your target project and paste the prompt below.** You do not need to
clone this repository, download a ZIP, attach documents, or run a copy script.
Copilot retrieves the public references and, after your run approval, assigns
a worker to localize them safely and continue your actual build objective.

FoldSpace is a documentation protocol, not an installed runtime. Fetching and
writing depend on the tools and permissions available in your Copilot host.

[Overview](README.md) | [Benefits](BENEFITS.md) |
[Operator guide](../operations/OPERATOR_GUIDE.md) | [Prompt examples](../operations/EXAMPLES.md)

## Contents

1. [Open the target project](#prerequisites).
2. [Paste one bootstrap prompt and approve the run](#send-a-bootstrap-prompt).
3. [Let Copilot localize what the project needs](#make-references-available-without-overwriting-instructions).
4. [Complete a real bounded task](#a-bounded-worked-example) and [continue safely](#fresh-session-discovery-and-continuation).

## Prerequisites

Open the repository where you want to build in your Copilot host. Supply a
concrete outcome and its constraints. That is the **target repository**;
FoldSpace's GitHub repository is only the public reference source.

The supported automatic path needs public URL retrieval and authorized target
workspace writes. Use normal host permission prompts if required. No package,
FoldSpace checkout, or assumed instruction-entrypoint filename is required.

## Send a bootstrap prompt

Replace the bracketed fields and paste this **whole prompt** into the target
project's Copilot session. It is ordinary language, not a native slash command.

```text
Use FoldSpace Orchestrator in this target repository. Do not ask me to clone
the FoldSpace repo, download a ZIP, attach its files, or run a copy script.
Read only this compact public Markdown entry first:
https://raw.githubusercontent.com/taomar/foldspace-orchestrator/main/protocol/BOOTSTRAP.md
Use its source map to retrieve detailed references only when needed.

Project mode: [new project / new run in this project / same-run continuation]
Outcome: [what I want built or changed]
Acceptance: [observable criteria]
Scope and authority: [allowed actions/files, compatibility, excluded effects]
Known ongoing work: [owners, changes, operations, or explicitly unknown]

Acknowledge supplied intent/run mode, ask one next unresolved question, and
end the first response before scans, setup generation or worker launch.
Use bounded public reference reads and safe local preparation; no private
project/user data may be uploaded or sent to external inference for this.
If URL access or writes are unavailable, request normal host permission or
report the exact gap; never claim a file was fetched or localized when it was not.

Before any worker, including setup/localization/discovery, or direct external
LLM call, complete the mandatory interview and obtain my final approval:
exact supported providers/models, role defaults and fallbacks; per-model
minimum/maximum and default within supported bounds or accepted N/A;
external consent; aggregate budget/units, allocations, concurrency,
retries/replacements, reservations, and stopping/escalation rules.
No silent defaults: external calls begin denied; missing budget is not unlimited.
For same-run continuation retain valid approvals, owners, charges and reservations.

After approval, assign a bounded setup worker using demonstrated controls.
Resolve one source commit, preview local paths and conflicts, and fetch the
required reference files and LICENSE from that same revision without cloning.
Save versioned reference copies, preserve their layout and source provenance,
and reuse matching existing copies rather than overwrite them.
Adapt the existing host-supported project instructions and authoritative
policy/capability/state records separately from the reference copies.
Preserve user edits, live owners/operations, queued intent and budget exposure.

Verify instruction discovery and the handoff, then continue implementing my
actual outcome with the project's existing tooling and acceptance criteria.
Do not stop at downloading documents or expand deployment/publication authority.
Keep the coordinator available; use an approved manual worker path if native
dispatch is unavailable. Reconcile unknown effects before retrying.
```

### Answer the interview before dispatch

Expect one unresolved question or bounded-action checkpoint, then a completed
response, not a silent full-repository audit. Missing input/evidence should
produce an explicit hold and next actor. A host question tool may itself suspend
the request; use its actual answer/cancel control rather than a message queued
behind it. No model IDs, reasoning levels, or spending caps are preselected here.

| The coordinator asks for... | You explicitly approve... |
|---|---|
| Models | Providers/families, exact supported IDs, default and role overrides, approved fallbacks |
| Reasoning, for each model | Minimum/maximum and a default within those bounds on that model's verified supported order; accepted N/A for fixed/nonconfigurable reasoning |
| Direct external LLM calls | Disabled, or provider/endpoint, models, purpose, permitted data, secure credential references (never keys), and budget |
| Budget and execution | Aggregate cap and real units, native/external allocations and relevant subcaps, concurrency, retries/replacements, stop/escalation policy |
| Final confirmation | The resolved run policy/version, approval source/time, and disclosed capability limits |

Reading public GitHub documentation is not an external LLM inference call.
Native Copilot permission does not authorize direct external inference.
Missing settings block affected dispatch; uncapped scope requires deliberate
opt-in and risk acknowledgment. Do not invent conversions between tokens,
credits and money. Reserve before concurrent dispatch, and retain consumption
and reservations across children, retries and replacements.

The complete questionnaire is in the
[run-configuration reference](../protocol/RUN_CONFIGURATION.md), available to
Copilot through the entry's full-URL source map.

## Obtain the documentation pack

**Copilot obtains the needed references; you do not prepare a local pack.**
The first read is the small
[public bootstrap body](https://raw.githubusercontent.com/taomar/foldspace-orchestrator/main/protocol/BOOTSTRAP.md).
Its [source map](../protocol/BOOTSTRAP.md#source-map) contains the full public
Markdown URLs for the protocol, configuration, operator guide, deployment
reference, history and license. Retrieval is on demand, not one large opening
context load.

Before saving reference copies, the approved setup worker resolves one source
commit and retrieves all selected files at that revision. It records the
source identity and does not describe several moving `main` reads as an atomic
snapshot. If the host cannot establish a consistent revision, it reports that
limitation rather than silently mixing versions.

## Make references available without overwriting instructions

After approval, Copilot delegates the following work to a bounded setup worker:

1. **Preview the change.** Identify the target repository, existing instruction
   entrypoints, dirty files, active owners and proposed reference/adaptation
   paths. Reuse project conventions and report conflicts.
2. **Save necessary references.** Copy the linked reference closure and MIT
   license from one source revision, preserving their folder/link layout.
   A suggested target location is `docs\reference\foldspace\<commit>`.
   Verify and reuse matching copies; do not overwrite conflicting content.
3. **Localize the operating setup.** Derive a compact project-native runtime
   core and adapt the host-supported instruction entrypoint. Reuse existing
   requirements, policy, capabilities, state and task tracking. Reference files
   are not live project state and must not replace local customizations.
4. **Verify and continue.** Record source URLs/commit, document revision, local
   paths and hashes. Establish that the intended session discovers the right
   instructions. Return the next ready assignment and continue the actual
   implementation/build goal under its approval and budget.

The suggested destination is inside **your target project**, not a new folder
in this documentation repository. Full mechanics and the standard reference
set are owned by the
[localization contract](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md#localize-github-references-without-cloning).

If network or workspace writes are blocked, use normal host permissions or
report the exact unavailable capability. Manual transfer is an exceptional
assisted fallback, not a prerequisite. Do not bypass access controls or claim
activation merely because a URL was mentioned or files were copied.

## Choose the project path

### New project

State the intended product, acceptance criteria and allowed actions. Establish
that project's own state without importing unrelated owners or assumptions.
Reconcile any genuinely shared resources before conflicting effects.

### Existing project

A **new run in the same project** explicitly reconfirms settings while
preserving requirements, tasks, owners, operations, resource exclusions,
pending steering, evidence and budget exposure. It does not stop old work.

A **same-run continuation** restores valid policy, pinned local references and
the ledger; it does not re-interview every call or silently refresh source
versions. Expanded scope/limits need approval. A fresh session is not
necessarily a new run.

## Record actual host capabilities

Record relevant controls as **Verified automatic**, **Assisted**,
**Unavailable**, or **Not checked**, with evidence. This includes reference
retrieval and writes, instruction discovery, actual model/reasoning selection,
budget accounting, nonblocking dispatch and result return.

If required controls cannot be applied/proved, hold affected autonomous work
or use an explicitly approved demonstrable manual path. A document describing
a feature does not install it. See the [runtime checks](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md#4-verify-the-runtime-before-promising-orchestration).

## Understand the project records

`POLICY` owns approvals/settings and the ledger or its owning reference;
`CAPABILITIES` owns supporting evidence; `PROJECT_STATE` points to the current
run, owners, ledger and next action. Existing equivalents remain authoritative.

Suggested `docs/ai/*` files are **target-project outputs, not preinstalled pack
assets**. Keep pinned reference copies separate from those adapted records.
Keep private operational material out of public commits and retain retrievable
work, not just summaries. See [project memory](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md#5-install-small-authoritative-project-memory).

## A bounded worked example

**Outcome:** correct one setup-guide section after a configuration option changed.

First, the approved setup assignment localizes the reference set and returns
its source commit, local paths, instruction-discovery evidence and limitations.
It does not claim the documentation change itself is complete.

The next assignment is the actual work:

| Contract item | Bounded example |
|---|---|
| Identity and owner | `DOC-SETUP-1`, version `1`, registered dispatch/coordinator, named worker and assigned workspace |
| Inputs and dependency | Current setup guide and agreed option behavior; wait if the behavior is unsettled |
| Write scope and authority | Only the identified guide section; no code edits, external inference, deployment or publication |
| Run controls | Approved policy/model/reasoning, parent budget reservation, operator-approved attempt and stop limits |
| Acceptance | Guidance matches the option, links resolve, unrelated content is preserved |
| Return and stop | Identified patch/commit, criterion-specific evidence, actual settings/usage, uncertainty and next action; return a blocker if code changes or conflicting ownership are needed |

Review the identified candidate and disclose review-independence limits.
An authorized integration worker checks the combined result; changed candidates
need renewed evidence. The coordinator records acceptance against the actual
criteria. Submission, integration, acceptance and publication are distinct.
Unrelated eligible work need not wait for this assignment.

## Manual worker fallback

If native nonblocking launch is unavailable, the coordinator prepares the
complete approved packet with source URLs or localized paths, effective
settings, reservation, workspace/scope, stop conditions and return channel.

The operator opens a separate worker through verified local steps. The worker
confirms ownership and dependencies, applies/proves approved settings, owns
its operations/checkpoints and returns an identified result. The operator
carries acknowledgements/results back only if the host requires it.

A prepared packet is not a running worker. If no adequate execution path
exists, hold affected work; do not have the coordinator silently absorb it.
See [worker launch and return fields](../operations/OPERATOR_GUIDE.md#5-launch-workers-with-an-explicit-task-and-job-handoff).

## Fresh-session discovery and continuation

Resume from compact project-native instructions/state and the explicit
assignment, not another full remote pack load. Identify current owners,
approval, ledger, checkpoint and next action before effects.

Preserve task ownership, exclusions, attempts, charges and reservations across
new sessions and runs. A surviving migration blocks conflicting writes, not
unrelated eligible work. Transfer ownership only through the existing safe
handover/fencing rules; silence does not prove termination.

Capture accessible pending intent before disruption. Reconcile uncertain
delivery, effects and charges before replay or reallocation; do not invent
inaccessible messages. Use the [recovery prompts](../operations/EXAMPLES.md#recover-context-without-reclaiming-ownership-blindly)
only through a responsive, authorized route.

## Upgrade without resetting live work

A newer remote source does not automatically replace active instructions.
Pin and compare the proposed revision, preserve existing reference copies,
customizations, live ownership/effects, approval and accounting, and apply
reviewed changes prospectively. Do not reset state or kill jobs to install a cap.
See [upgrade guidance](../reference/REVIEW_AND_CHANGES.md#4-apply-the-revision-without-resetting-the-project).

## If you get stuck

| Situation | Next action |
|---|---|
| Public URL retrieval or workspace writes are blocked | Request normal host permission or name the missing capability; manual transfer is exceptional, not a clone/attachment prerequisite |
| Copilot received page chrome, an error, or partial content | Retrieve the actual Markdown body through a supported route; do not save it as a successful reference copy |
| Existing references/instructions conflict | Compare and report the conflict, reuse only verified matches, and hold affected writes rather than overwrite |
| Reasoning or budget controls are unsupported | Disclose the limit; obtain accepted N/A where genuinely fixed or an approved measurable/explicitly uncapped budget choice as applicable; no invented settings or conversions |
| External inference is denied | Keep it blocked; this does not prohibit the user-approved public documentation GET or already-approved native work |
| Bootstrap or automation messages keep queuing | Do not append recovery prompts. Use [independent host controls](../operations/OPERATOR_GUIDE.md#automation-admission-and-out-of-band-recovery), preserving intent and live operations |

The canonical references own the detailed policy. This guide gets you from
one pasted URL-bearing prompt to a localized setup and actual project work.
