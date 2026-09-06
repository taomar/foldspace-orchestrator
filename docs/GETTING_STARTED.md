# Getting started with FoldSpace Orchestrator

**Your first goal:** approve a run, hand one bounded task to a worker, and
receive a result you can review and continue from. FoldSpace is a documentation
pack, not an installed agent runtime.

[Overview](README.md) | [Benefits](BENEFITS.md) |
[Operator guide](../operations/OPERATOR_GUIDE.md) | [Prompt examples](../operations/EXAMPLES.md)

## Contents

Follow this path:
1. [Open your target project and obtain the references](#prerequisites).
2. [Choose a new project, new run, or continuation](#choose-the-project-path).
3. [Send the bootstrap prompt and approve the interview](#send-a-bootstrap-prompt).
4. [Complete one bounded worker handoff](#a-bounded-worked-example).
5. [Continue safely](#fresh-session-discovery-and-continuation).

## Prerequisites

Have a target repository, access to a Copilot host, and one concrete outcome.
The **pack repository** holds reference documents; the **target repository**
is where your actual project work happens. Do not replace one with the other.
No packages are needed; Git is only needed for the clone option.

Before changes, identify existing instructions, uncommitted work, active owners,
and running operations. Unknown ownership is not unclaimed ownership.

## Obtain the documentation pack

From a directory where `foldspace-orchestrator` does not already exist:

```powershell
git clone https://github.com/taomar/foldspace-orchestrator.git .\foldspace-orchestrator
```

Alternatively, download and extract the repository ZIP from GitHub. Record the
revision you use. Open your **target repository** in the intended Copilot host.

## Make references available without overwriting instructions

Attach or otherwise load these three files using a mechanism your host supports:

- [protocol/FIRST_SESSION_AND_ORCHESTRATION.md](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md)
- [operations/OPERATOR_GUIDE.md](../operations/OPERATOR_GUIDE.md)
- [protocol/RUN_CONFIGURATION.md](../protocol/RUN_CONFIGURATION.md)

Ensure the questionnaire is actually accessible, not just a link in an
attachment the host cannot follow. Ask the session to identify what it read.
Supply deployment and revision references when needed. There is no universal
instruction entrypoint or attachment command.

**Optional copy recipe:** skip this if attachments work. Otherwise replace the
paths below to copy the linked reference set and MIT license into a new,
dedicated location in the target project. The preflight refuses an existing
destination or missing source; individual copies also refuse overwrites.

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

The copied bootstrap file is at
`docs\reference\foldspace\protocol\FIRST_SESSION_AND_ORCHESTRATION.md`
in the sample target. The other files retain the same relative layout.
Keep the license when redistributing. **Do not overwrite existing instructions
or live state:** reconcile active rules and reuse authoritative records.
Copying references alone does not activate the protocol.

## Choose the project path

### New project

State the desired outcome, acceptance criteria, constraints, and permitted
actions. Establish that project's own state; do not import another project's
unrelated owners or assumptions. Reconcile any genuinely shared resources.

### Existing project

For a **new run in the same project**, inventory current work and explicitly
reconfirm run settings. Preserve requirements, tasks, owners, operations,
resource exclusions, pending steering, evidence, and consumed/reserved budget.
A new run does not stop an old worker or free its resources.

For **same-run continuation**, restore the approved policy and ledger rather
than repeating the interview for every call. A fresh session is not necessarily
a new run. Expanded scope or limits still require approval.

## Send a bootstrap prompt

Replace the fields. This is an ordinary-language prompt, not a native command:

```text
Use the supplied FoldSpace protocol, operator guide, and RUN_CONFIGURATION.md.
Project mode: [new project / new run in this project / same-run continuation]
Outcome: [one bounded result]
Acceptance: [observable criteria]
Scope and authority: [allowed files/actions, compatibility, excluded effects]
Known ongoing work: [owners, changes, operations, or explicitly unknown]

Preserve existing instructions, authoritative state, active owners and work.
For a new run, conduct the mandatory configuration interview one question at
a time and obtain my final approval before discovery workers, other workers,
or direct external LLM calls. Until approval, only safe local preparation in
this current bootstrap chat is allowed. Do not probe endpoints with private data.

Confirm approved exact models and fallbacks; per-model supported minimum,
default and maximum reasoning or explicitly accepted N/A; external consent;
aggregate budget/units, allocations, concurrency, retries and stop policy.
No silent defaults: external calls start denied and missing budget is not unlimited.
For continuation, retain valid approvals and all charges/reservations.

After approval, verify required host controls, reserve parent budget, and
prepare one versioned assignment with a named owner and result return path.
Use demonstrated nonblocking dispatch or an approved manual worker packet.
Require candidate-specific evidence; do not expand scope or release authority.
```

### Answer the interview before dispatch

Expect these decisions, with compound fields asked separately where supported.
No model IDs, reasoning levels, or spending caps are preselected by this guide.

| The coordinator asks for... | You explicitly approve... |
|---|---|
| Models | Providers/families, exact supported IDs, default and role overrides, approved fallbacks |
| Reasoning, for each model | Minimum/maximum and a default within those bounds, using that model's verified supported order; accepted N/A for fixed/nonconfigurable reasoning |
| Direct external LLM calls | Disabled, or provider/endpoint, models, purpose, permitted data, secure credential references (never keys), and budget |
| Budget and execution | Aggregate cap and real units, native/external allocations and relevant subcaps, concurrency, retries/replacements, stop/escalation policy |
| Final confirmation | The resolved run policy/version, approval source/time, and disclosed capability limits |

Native Copilot permission does not authorize direct external calls. Missing
settings block affected dispatch, not safe local preparation. Explicitly
uncapped scope needs deliberate opt-in and risk acknowledgment; do not invent
conversions between tokens, credits, and money. Reserve before parallel dispatch.
Children, fallbacks, retries, and replacements inherit or tighten limits and
retain accounting. Full details: [run configuration](../protocol/RUN_CONFIGURATION.md).

## Record actual host capabilities

Record each relevant control as **Verified automatic**, **Assisted**,
**Unavailable**, or **Not checked**, with evidence and limitations. In
particular, establish how the host applies/proves model and reasoning settings,
accounts for the approved budget, launches a worker, and returns its result.
Documentation or a configured feature is not proof it works.

If required settings or bounds cannot be applied and evidenced, block affected
autonomous dispatch or use an explicitly approved, demonstrable manual path.
See [runtime checks](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md#4-verify-the-runtime-before-promising-orchestration).

## Understand the project records

Reuse the project's authoritative records: `POLICY` owns approvals/settings and
the ledger or its owning reference; `CAPABILITIES` owns supporting evidence;
`PROJECT_STATE` points to the active run, owners, ledger and next action.
Suggested `docs/ai/*` files are **target-project outputs, not assets shipped
here**. Keep sensitive records out of public commits; retain retrievable work,
not just summaries. See [project memory](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md#5-install-small-authoritative-project-memory).

## A bounded worked example

**Task:** correct one setup-guide section after an existing configuration option
changed. First approve the run interview; then fill the assignment from real
project facts rather than launch the placeholders below.

| Assignment item | Bounded example |
|---|---|
| Identity | `DOC-SETUP-1`, version `1`, registered dispatch ID and current coordinator |
| Owner and workspace | One named documentation worker in its assigned workspace, after checking existing changes |
| Input and dependency | Agreed current option behavior and the setup guide; wait if that behavior is unsettled |
| Scope and authority | Only the identified guide section; no code edits, external calls, deployment, or publication |
| Run controls | Approved policy reference, evidenced model/reasoning, parent budget reservation, and operator-approved attempt/stop limits |
| Acceptance | Guidance matches the option, links resolve, unrelated content is preserved |
| Handoff and stop | Agreed result/checkpoint location; return a blocker if code changes or conflicting ownership are discovered |
| Result | Identified commit or preserved patch, criterion-by-criterion evidence, actual settings/usage, surviving operations or uncertainty, and next action |

1. The coordinator registers the complete [assignment contract](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md#8-give-every-assignment-a-complete-versioned-contract),
   checks ownership/dependencies and reserves budget before dispatch.
2. The worker acknowledges the assignment and performs the bounded work.
   A prepared or acknowledged packet is not proof execution has started.
3. Review the identified candidate; use independent review when useful and
   feasible, and disclose its limits. An authorized integration worker applies
   it and checks the combined result; changed candidates need renewed evidence.
4. The coordinator records acceptance against the criteria. Submission,
   integration, acceptance, and permission to publish are different facts.

One execution worker may be enough. Unrelated ready tasks need not wait for it
if their own dependencies, resources, authority, and budget are satisfied.

## Manual worker fallback

If automatic nonblocking launch is unavailable:

1. The coordinator prepares the complete approved packet, including effective
   settings, reservation, workspace/scope, stop conditions and return path.
2. The operator uses **verified local steps** to open a separate worker session
   and supply its instructions/inputs. Apply and evidence approved settings
   before effects; do not invent a universal command or use silent defaults.
3. The worker confirms ownership and dependencies, inspects surviving work,
   owns its operations/checkpoints, and returns an identified result. The
   operator carries acknowledgements and results back if needed.
4. The coordinator distinguishes receipt from execution and reviews the
   current assignment/candidate evidence before acceptance.

If no separate session or adequate control is available, report the limitation
and hold affected work; do not have the coordinator silently absorb execution.
See [worker launch and return fields](../operations/OPERATOR_GUIDE.md#5-launch-workers-with-an-explicit-task-and-job-handoff).

## Fresh-session discovery and continuation

Use the host's verified mechanism to open a continuation session. It must find
its role, instructions, current run/assignment, owners, approval/ledger,
checkpoint, and next action. A worker also needs its explicit packet.

Restore accessible work and inspect surviving operations before effects.
Retain owners, resource exclusions, attempts, charges and reservations across
new sessions **and new runs**. A surviving migration blocks conflicting writes,
not unrelated eligible work. Ownership transfer requires the existing safe
handover/fencing rules; silence does not prove termination.

Before disruption, capture accessible pending intent and attachments in
appropriate storage. If delivery, effects, or charges are uncertain, reconcile
before retrying or reallocating; do not invent inaccessible queued messages.
Use the [continuation and recovery prompts](../operations/EXAMPLES.md#recover-context-without-reclaiming-ownership-blindly).

## Upgrade without resetting live work

Review changes before replacing references or active instructions. Preserve
customizations, authoritative state, owners, operations, prior authority,
pending intent, evidence and accounting; reconcile changed assignments
prospectively. Do not reset a tracker or kill stateful jobs to install a cap.
See [upgrade guidance](../reference/REVIEW_AND_CHANGES.md#4-apply-the-revision-without-resetting-the-project).

## If you get stuck

| Situation | Next action |
|---|---|
| A referenced file was not loaded | Attach it explicitly or correct the accessible copy path; include `RUN_CONFIGURATION.md` |
| The host is manual-only | Use the verified [manual handoff](#manual-worker-fallback); do not mark a prepared packet running |
| Reasoning is unsupported | Record accepted N/A if fixed; otherwise block autonomous claims or use a provable approved manual configuration |
| The cap cannot be measured/enforced | Disclose the limitation and obtain an approved measurable bound or explicit uncapped opt-in; do not invent a conversion |
| External calls are denied | Keep them blocked; already-approved native work can continue within its own scope |
| Another owner or uncertain operation exists | Preserve its exclusions and reservations, reconcile or safely transfer ownership, and continue only nonconflicting eligible work |

For day-to-day steering, use the [operator guide](../operations/OPERATOR_GUIDE.md).
The canonical references own the detailed policy; this guide is the first-use path.
