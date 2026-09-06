# Getting started with FoldSpace Orchestrator

Adopt the protocol in the repository where your work actually happens.
FoldSpace is a documentation pack: copying its references does not install an
agent runtime or activate a scheduler.

[Overview](README.md) | [Benefits](BENEFITS.md) |
[Prompt examples](../operations/EXAMPLES.md) | [Canonical operator guide](../operations/OPERATOR_GUIDE.md) |
[Run configuration](../protocol/RUN_CONFIGURATION.md)

## Contents

- [Prerequisites](#prerequisites)
- [Obtain the documentation pack](#obtain-the-documentation-pack)
- [Make references available without overwriting instructions](#make-references-available-without-overwriting-instructions)
- [Choose the project path](#choose-the-project-path)
- [Send a bootstrap prompt](#send-a-bootstrap-prompt)
- [Record actual host capabilities](#record-actual-host-capabilities)
- [Understand the project records](#understand-the-project-records)
- [A bounded worked example](#a-bounded-worked-example)
- [Manual worker fallback](#manual-worker-fallback)
- [Fresh-session discovery and continuation](#fresh-session-discovery-and-continuation)
- [Upgrade without resetting live work](#upgrade-without-resetting-live-work)

## Prerequisites

You need a target repository or project workspace, a Copilot host you can
actually use with it, and an outcome concrete enough to evaluate. Every new
run requires an explicit model/reasoning, external-call consent, and budget
interview before workers start, including discovery workers. Unknown settings
block affected dispatch, not safe local planning in the bootstrap chat.
State permitted changes and compatibility needs; do not invent project facts.

Identify existing instructions, task tracking, unfinished changes, other active
workers, and any running operations before assigning overlapping work. Preserve
the repository's established build, validation, and review practices.

There is **no package installation required**. Git is needed only if you choose
the clone option below. Automatic worker launch is not a prerequisite for using
the protocol's assisted form; someone must carry the handoff when the host
cannot do it.

Do not assume a particular instruction filename, slash command, hook, menu
item, or persistent-session feature exists. Discover the entrypoints and tools
your actual host supports.

## Obtain the documentation pack

Clone the public repository into a **separate documentation directory**. This
PowerShell example uses the current directory as the parent; choose a location
that does not already contain a folder named `foldspace-orchestrator`.

```powershell
git clone https://github.com/taomar/foldspace-orchestrator.git .\foldspace-orchestrator
```

Alternatively, download a ZIP of the repository through its GitHub page and
extract it to a separate folder. This repository download is the published
documentation pack, not a runtime installer. If you need repeatable adoption,
record the repository revision or download provenance you used.

Do not replace your target repository with this one. Open the target repository
in the host where you intend to do the actual project work.

## Make references available without overwriting instructions

Make these two references available to the target session:

- [protocol/FIRST_SESSION_AND_ORCHESTRATION.md](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md)
- [operations/OPERATOR_GUIDE.md](../operations/OPERATOR_GUIDE.md)

Use file attachments if your host supports them. Otherwise, copy the reference
files to a reviewed location in the target repository and use that host's
supported way of including their content. Ask the session to identify the
references it actually read. A filename mentioned in a prompt is not proof it
was loaded.

The following optional PowerShell example copies **the four canonical
references, run-configuration guide, and license** to a dedicated subdirectory.
It preserves the pack's folder layout and their relative links. Replace the
sample paths first. The command refuses to use an existing destination so it
cannot silently overwrite a previous copy or live instruction file.

```powershell
$ErrorActionPreference = 'Stop'
$pack = 'C:\work\foldspace-orchestrator'
$target = 'C:\work\your-project'
$destination = Join-Path $target 'docs\reference\foldspace'
$references = @(
    'protocol\FIRST_SESSION_AND_ORCHESTRATION.md'
    'operations\OPERATOR_GUIDE.md'
    'protocol\DEPLOYMENT_BUILD_INSTRUCTIONS.md'
    'reference\REVIEW_AND_CHANGES.md'
    'protocol\RUN_CONFIGURATION.md'
    'LICENSE'
)

if (-not (Test-Path -LiteralPath $target -PathType Container)) {
    throw 'The target project directory does not exist.'
}
if (Test-Path -LiteralPath $destination) {
    throw 'Destination already exists. Review its contents before updating.'
}
foreach ($name in $references) {
    $source = Join-Path $pack $name
    if (-not (Test-Path -LiteralPath $source -PathType Leaf)) {
        throw "Missing reference: $name"
    }
}

New-Item -ItemType Directory -Path $destination | Out-Null
foreach ($name in $references) {
    $source = Join-Path $pack $name
    $copy = Join-Path $destination $name
    $parent = Split-Path -Parent $copy
    if (-not (Test-Path -LiteralPath $parent -PathType Container)) {
        New-Item -ItemType Directory -Path $parent | Out-Null
    }
    [System.IO.File]::Copy($source, $copy, $false)
}
```

If you only attach the first two documents rather than redistribute copies,
consult the other references from this pack when needed. When redistributing
the documents, retain the MIT copyright and permission notice.

**Do not paste the whole protocol over an existing instruction entrypoint.**
First reconcile the project's instruction hierarchy and existing policies.
Keep one authoritative version of each rule. The full references can remain
reference material; adoption should derive a small project-specific runtime
core and link to details as needed.

The copied bootstrap reference is at
`docs\reference\foldspace\protocol\FIRST_SESSION_AND_ORCHESTRATION.md`
relative to the sample target project. Attach the copied operator guide from
`docs\reference\foldspace\operations\OPERATOR_GUIDE.md`, or use the original
pack's references through a verified host mechanism.

Copying files is not activation. A later fresh-session check must show that
the intended host discovers the right project instructions and state.

## Choose the project path

### New project

State the intended product or result, known constraints, and acceptance
criteria. Establish the smallest useful project structure rather than
inventing architecture, tools, or a release topology.

Complete and approve the run interview first. Safe local capability reading
in the current bootstrap chat may prepare the questions without launching
workers or probing external LLM endpoints. Then initial discovery should
identify the project boundary, existing repository
assets, supported host mechanisms, and the appropriate validation path. Under
the protocol, substantial discovery is a bounded worker assignment; the
coordinator organizes it and maintains the objective. Useful independent work
can proceed when its own prerequisites and authority are satisfied.

### Existing project

Begin with reconciliation, not reinitialization. Preserve current requirements,
decisions, task identities, owners, assignment versions, worktrees, incomplete
changes, operation handles, pending steering, budgets, authority, and accepted
evidence.

Reuse the existing tracker and records wherever they already own the relevant
state. Adapt conflicting active instructions explicitly rather than appending
a second coordinator policy. Do not declare live workers abandoned because
their instructions predate adoption.

For the canonical paths, see
[operator guide section 1](../operations/OPERATOR_GUIDE.md#1-start-a-new-project-or-upgrade-an-existing-one)
and [revision migration guidance](../reference/REVIEW_AND_CHANGES.md#4-apply-the-revision-without-resetting-the-project).

## Send a bootstrap prompt

Replace every bracketed field. This is ordinary language, not a native command
or a request to install every optional mechanism mentioned by the references.

```text
Adopt FoldSpace Orchestrator for this target repository using the supplied
FIRST_SESSION_AND_ORCHESTRATION.md and OPERATOR_GUIDE.md as references.

Project path: [new project / existing project]
Outcome: [the bounded result I want]
Acceptance: [observable checks or review criteria]
Scope and compatibility: [allowed files/components and required behavior]
Budget: [known effort/cost/retry limits, or explicitly unknown]
Authority: [permitted local actions and any separately authorized effects]
Do not: [out-of-scope changes, publication, deployment, or other restrictions]
Known ongoing work: [owners, pending changes, jobs, and steering; or unknown]

Identify the current coordination owner and preserve existing work and policy.
Do not create a competing tracker or assume unknown ownership is unclaimed.
Separate short coordination work from substantial execution assignments.

Before workers or direct external LLM calls, ask one question at a time for
approved providers/families and exact supported model IDs, role defaults and
fallbacks, per-model supported minimum/default/maximum reasoning, external-call
consent (explicitly disabled or precisely scoped), and aggregate budget/units,
allocations, concurrency, retries/replacements, and stopping/escalation policy.
Record explicit acceptance of N/A reasoning where it is not configurable.
Missing settings are not permission for runtime defaults or unlimited spend.
External calls default denied, independently of native Copilot authorization.
Reconfirm for a new run; carry approved scope forward on within-run handoff.

Discover the instruction-loading and worker mechanisms available in this host.
Record each relevant capability as Verified automatic, Assisted, Unavailable,
or Not checked, with evidence and a concrete fallback where applicable.
Do not turn a configured feature into a claim of demonstrated behavior.

Reuse or create the smallest authoritative project records. Keep sensitive
operational material out of public commits. Define versioned assignments,
resource/write scopes, inherited budgets, and candidate-specific acceptance.
If native nonblocking dispatch is unavailable, prepare an operator-carried
worker packet with verified local launch steps and an explicit result path.

Report the next ready assignment, its owner, any blockers, and the next action.
Dispatch only once approved settings can be applied and evidenced and parent
budget is reserved. Continue authorized work without waiting for unrelated
tasks or expanding authority. Keep uncertain usage reserved during recovery.
```

If authority, ownership, or a required prerequisite remains unknown, the next
action can be bounded discovery or clarification. It is not permission for
conflicting writes or external effects.

Use the [complete questionnaire and examples](../protocol/RUN_CONFIGURATION.md)
to conduct the interview. Persist approved policy/version and its source/time
in the existing `POLICY` arrangement, capability evidence in `CAPABILITIES`,
and active run/ledger references in `PROJECT_STATE`. Do not create competing
copies of approved settings. Subtasks, fallbacks, retries, and replacements
inherit or tighten settings and retain usage/reservations.

## Record actual host capabilities

Create or update the target project's capability record, suggested as
`docs/ai/CAPABILITIES.md`, or reuse its existing equivalent. For every relevant
mechanism, record the observed environment, evidence, limitations, and exact
operator action when assistance is needed.

| Status | What the entry should mean |
|---|---|
| Verified automatic | The required automatic behavior was demonstrated in the intended runtime, with evidence |
| Assisted | A defined person-assisted path is available; identify what the person must actually do |
| Unavailable | The required mechanism is not available in this host |
| Not checked | No adequate observation has established the behavior yet |

Start with the capabilities necessary for your first task:

- Can a fresh session discover the intended instructions and current state?
- Is there a separate execution context, and can the coordinator remain
  responsive while it works?
- What proves launch, running status, individual result return, and cancellation?
- Which files and shared resources are isolated, and what actually enforces ownership?
- Can a new session retrieve the checkpoint, work bytes, and operation status?
- Can the host select and prove the actual model and per-model reasoning, and
  observe/reserve usage in the approved units without inventing conversions?

Check recovery, queue capture, reconnect, persistent follow-up, independent
monitoring, and deployment controls before relying on them. You need not
pretend to have every optional facility in order to start a safe local task.

Keep drill evidence precise: **documented**, **configured**, **locally
exercised**, **verified in the intended runtime**, and **blocked** are different
claims. A synchronous subagent call may provide a separate context while still
blocking the coordinator; it does not establish nonblocking orchestration.

These status records are observations, not a compatibility certification.
Use [canonical runtime checks](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md#4-verify-the-runtime-before-promising-orchestration)
and [activation guidance](../operations/OPERATOR_GUIDE.md#2-confirm-activation-in-a-fresh-session)
for the complete requirements.

## Understand the project records

The following are **suggested outputs in your target project**, not files
shipped in this repository and not empty templates to install in bulk.

| Suggested location or existing equivalent | Responsibility |
|---|---|
| Host-supported instruction entrypoint | Make the role boundary and discovery order visible to future sessions |
| `docs/ai/RUNTIME_CORE.md` | Compact, frequently needed operating rules |
| `docs/ai/SESSION_PROTOCOL.md` | Detailed project-specific procedures |
| `docs/ai/PROJECT_STATE.md` | Objective/version, coordinator, current assignments, blockers, evidence, next actions |
| `docs/ai/REQUIREMENTS.md` or existing tracker | Stable requirement identities, revisions, and acceptance mapping |
| `docs/ai/CAPABILITIES.md` | Demonstrated mechanisms, limits, and assisted steps |
| `docs/ai/POLICY.md` | Authoritative approved run models/reasoning, external consent, budgets/ledger ownership, authority, and project gates |
| Existing task tracker or `docs/ai/tasks/` | Versioned assignments, dependencies, attempts, ownership, and results |
| Suitable controlled artifact storage | Work snapshots, operation records, evidence, queue journals, and recovery checkpoints |

Link to authoritative records instead of manually synchronizing competing
copies. Version durable policy where appropriate, but do not commit secrets,
private queued messages, sensitive logs, or all transient checkpoints by
default. Recoverable artifacts need actual retrievable content, not only a
checksum or a diff summary.

Different branches containing the same state filename do not create a shared
lock or a shared database. Use the project's existing shared tracking or a
demonstrated mechanism when multiple machines or sessions need common state.
See [canonical project memory](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md#5-install-small-authoritative-project-memory).

## A bounded worked example

Suppose an existing repository needs a corrected contributor setup section
after a supported configuration option changed. The goal is a small,
reviewable documentation candidate, not deployment or framework adoption.

The identifiers below are examples to replace with your project's own records.
They are not installed task files or commands.

| Contract item | Example |
|---|---|
| Objective / requirement | `DOC-SETUP`: document the current option and remove stale setup guidance |
| Assignment | `DOC-SETUP-1`, version `1`, with a recorded dispatch ID and current coordinator association |
| Approved run policy | A current policy/version with evidenced model and reasoning settings; external calls disabled; an available parent budget reservation |
| Owner and workspace | One named documentation worker in its assigned workspace, after inspecting existing changes |
| Inputs | Current option definition, existing setup guide, accepted requirement revision |
| Dependencies | Agreed option behavior; if still changing, wait for the required accepted contract/artifact |
| Writes and resources | Only the agreed setup section; no application changes, shared-environment mutations, or publication |
| Acceptance | Guidance matches the actual option, examples are internally consistent, local links resolve, unrelated text is preserved |
| Budget | One bounded edit attempt and one bounded correction pass within the parent allowance; stop if code changes are needed |
| Return | A preserved patch or commit identifying the candidate, changed paths, evidence, limitations, and next action |

1. After the run interview is approved, the coordinator checks ownership,
   effective model/reasoning, and reserved budget, records the assignment, and chooses a
   demonstrated dispatch path or the manual fallback below.
2. The worker acknowledges the exact assignment, inspects the current option
   and guide, and returns the bounded documentation candidate with evidence.
3. A reviewer checks that candidate against the acceptance criteria. Use an
   independent reviewer when useful and feasible; disclose a same-worker
   review's independence limit.
4. An authorized integration worker applies the candidate to the intended
   branch and checks the combined result. A conflict resolution or substantive
   edit requires renewed evidence for the changed candidate.
5. The coordinator records acceptance only for the identified result that
   meets the requirement. A submitted patch is not automatically integrated
   work, and integration is not permission to publish it.

If inspection shows the option's behavior is unsettled, return the dependency
and next action instead of broadening the assignment into implementation.
Parallelize only genuinely independent ready work; this example may not need
multiple execution workers.

## Manual worker fallback

When native nonblocking worker launch is unavailable, use a real separate
session with an operator-carried packet. Do not invent a tool or silently have
the coordinator perform the heavy execution.

1. **Approve, prepare, and register.** Complete the run interview first.
   The coordinator records a complete versioned
   assignment and its intended owner, result location, and observation trigger.
   Include the approved policy/version, effective model/reasoning, external
   consent scope, and parent budget reservation. Record it as prepared;
   do not mark it running.
2. **Give local launch instructions.** Identify the actual verified way the
   operator can open a separate session in this host and select the intended
   workspace. If that mechanism has not been checked, say so and have the
   operator establish it before claiming a usable assisted path. Include
   exact approved model/reasoning configuration steps and obtain evidence
   of the applied settings before effects. Unsupported controls cannot be
   replaced with silent host defaults.
3. **Carry the packet.** The operator opens that session and supplies the packet
   plus the applicable project instructions, inputs, and accessible artifacts.
   Preserve its task/assignment/dispatch identities rather than regenerating
   them during the copy.
4. **Confirm before acting.** The worker confirms its role, identities,
   workspace, current owner, dependencies, write scope, shared resources,
   authority, budget, stop conditions, acceptance, and return channel. It
   inspects existing work and surviving operations before new effects.
5. **Distinguish receipt from work.** Return a delivery/launch acknowledgement
   through the agreed channel. Record actual execution only when evidenced;
   a pasted prompt, queue entry, or acknowledgement is not proof of a running job.
6. **Execute within the assignment.** The worker owns its commands, real
   operation handles, checkpoints, and evidence. If another owner or unknown
   operation can still write the same resource, reconcile or stop rather than
   assuming a new session makes the resource safe.
7. **Return and reconcile.** The worker writes or sends its result through the
   agreed accessible path; the operator carries it back if necessary. The
   coordinator checks assignment currency, candidate, evidence, live effects,
   and remaining budget before review, integration, or acceptance.

A packet should cover the fields in the
[canonical assignment contract](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md#8-give-every-assignment-a-complete-versioned-contract):
task and parent objective, requirement references, assignment/dispatch/coordinator
identities, owner, objective and acceptance, inputs and dependencies, workspace,
write scope and resource reservations, authority and needed capabilities,
inherited budget, execution/liveness/checkpoint arrangements, stop conditions,
deliverables, and the return path.

The result needs those identities plus a result ID, contract versions,
immutable candidate or preserved snapshot, acceptance outcomes and actual
checks, changed artifacts, uncertainty, surviving operations, remaining budget,
and next action. Include effective run policy/model/reasoning, actual
usage by accounting path/unit, reservations, and uncertain in-flight charges.
Raw logs belong in suitable linked artifacts, not a claim of
success with no candidate.

If no separate session is available at all, prepare the bounded packet and
report execution as blocked or operator-performed. Do not claim that the
coordinator/executor separation has been demonstrated.

## Fresh-session discovery and continuation

Before relying on the setup, open a fresh session using your host's verified
mechanism and establish what it actually finds. For a worker session, supply
its explicit assignment; discovering the general protocol alone is insufficient.

The session should be able to identify its role, instruction revision,
objective and requirements, coordinator and assignment, workspace and owner,
authority and remaining budget, relevant live operations, latest accepted
evidence, pending steering, blockers, and exact next action.

A fresh session continuing an approved run inherits its policy and ledger;
a new run must explicitly reconfirm settings. Neither a new session nor a new
run label erases outstanding charges or reservations from prior work.

It must not assign itself ownership just because the previous conversation is
quiet. Check the relevant branch, worktree, shared tracker, and accessible
artifacts. If discovery fails, fix the actual loading or access path and repeat
the observation; do not merely declare activation complete.

For continuation:

```text
Continue from the target project's authoritative state and checkpoint.
Identify my requested outcome, current role and assignment, active owners,
remaining authority and budget, pending steering, surviving operations, and
the last accepted candidate/evidence.
Restore the approved run policy/version, selected models/reasoning, scoped
external consent, reservations, actual usage, and uncertain charges.
Reconfirm settings only if this is a new run or the scope must expand.

Inspect accessible tracked and untracked work before changing anything.
Reconcile unknown external effects before replay or replacement writes.
Do not reset attempts, duplicate assignments, or infer completion from silence.
If records conflict or required artifacts are unavailable, report the specific
gap and choose a safe discovery action. Otherwise continue the next ready,
authorized action and preserve the next checkpoint.
```

Coordinator replacement needs a supported handover/fencing mechanism or a
confirmed surrender of ownership. A new epoch written in Markdown does not
revoke the old coordinator's tools. Adopt valid unaffected worker assignments
explicitly rather than discarding them.

See [context recovery](../operations/OPERATOR_GUIDE.md#7-recover-context-and-coordination-without-losing-work)
and [recoverable work and ownership](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md#13-preserve-recoverable-work-and-restore-ownership-safely).

## Upgrade without resetting live work

Treat a newer protocol revision as a migration of active rules, not a new
project. Inventory which files are reference assets, which are local policy,
and which carry live state.

Preview and review differences before replacing any reference or instruction.
Preserve task identities and versions, owners, budgets and attempts, pending
intent, prior authority, operation handles, evidence, and incomplete work.
Apply assignment changes prospectively, reconcile affected workers, and pause
incompatible operations before switching formats. For a 2.0-to-2.1 upgrade,
inventory existing effects and obtain missing run approvals before new affected
dispatch; do not kill stateful operations or reset accounting to install a cap.

Do not introduce duplicate rules, replace local customization silently, reset
a tracker, or discard historical decisions. Keep a recovery route for the
changed assets; reverting instructions must not erase project state or imply
that external effects were undone.

The canonical upgrade guidance is in
[REVIEW_AND_CHANGES.md](../reference/REVIEW_AND_CHANGES.md#4-apply-the-revision-without-resetting-the-project)
and [setup distribution](../protocol/DEPLOYMENT_BUILD_INSTRUCTIONS.md#deliver-the-copilot-working-setup).
