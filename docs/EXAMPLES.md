# Prompt cookbook

These are **ordinary-language prompts**, not native slash commands, installed
tools, or guarantees that the host can perform the requested action. Replace
bracketed fields and provide the referenced project records through a supported
mechanism. A request to report capability evidence must not be satisfied by
inventing that evidence.

Use the [getting-started guide](GETTING_STARTED.md) for adoption. The
[canonical protocol](../FIRST_SESSION_AND_ORCHESTRATION.md) and
[operator guide](../OPERATOR_GUIDE.md) define the full contracts behind these
short prompts.

## Contents

- [Start a bounded project task](#start-a-bounded-project-task)
- [Steer work without losing prior intent](#steer-work-without-losing-prior-intent)
- [Ask for status that distinguishes progress from activity](#ask-for-status-that-distinguishes-progress-from-activity)
- [Prepare a bounded worker handoff](#prepare-a-bounded-worker-handoff)
- [Return a worker result](#return-a-worker-result)
- [Recover context without reclaiming ownership blindly](#recover-context-without-reclaiming-ownership-blindly)
- [Capture intent before a disruption](#capture-intent-before-a-disruption)
- [Recover a connection and reconcile before replay](#recover-a-connection-and-reconcile-before-replay)
- [Review and integrate the actual candidate](#review-and-integrate-the-actual-candidate)
- [Prepare a release without implying permission](#prepare-a-release-without-implying-permission)
- [Authorize a specific release action](#authorize-a-specific-release-action)

## Start a bounded project task

Use after making the two bootstrap references available and identifying whether
this is a new or existing project.

```text
Use FoldSpace Orchestrator for [new/existing project] in this repository.
Outcome: [specific result].
Acceptance: [observable criteria].
Allowed scope: [components/files and compatibility constraints].
Budget: [effort/cost/retry allowance].
Authority: [permitted actions]. Excluded effects: [publication/deployment/etc.].

Preserve the current instructions, requirements, work, owners, operations,
pending steering, and existing authority. Reuse authoritative records.
Identify the current coordinator and verify the host capabilities required
for the first assignment. Record unsupported behavior honestly.
Dispatch the next ready, authorized bounded task through a demonstrated path,
or prepare a complete operator-carried packet without claiming it has started.
```

Reference: [starting or upgrading a project](../OPERATOR_GUIDE.md#1-start-a-new-project-or-upgrade-an-existing-one).

## Steer work without losing prior intent

Use when changing priorities or requirements while workers may still be active.
Do not assume a chat message instantly updates every worker.

```text
Record this steering change against [objective/requirement identity]:
[the new requirement, priority, constraint, or cancellation].

Preserve the original intent and append its new disposition/version.
Identify affected assignments, shared resources, queued work, and live effects.
Apply the change to future dispatch and reconcile affected owners before new
incompatible effects. Preserve useful prior work and unaffected assignments.
Use supported controls for cancellation or handover; a new record alone
does not stop an existing writer. Keep inherited budgets and prior authority.
Report what was captured, delivered, acknowledged, and actually applied,
plus any uncertainty and the accountable next action.
```

Reference: [operator guide](../OPERATOR_GUIDE.md), particularly sections 4 and
6, and the [canonical queued-intent policy](../FIRST_SESSION_AND_ORCHESTRATION.md#10-back-up-queued-intent-reconnect-and-apply-pending-work).

## Ask for status that distinguishes progress from activity

```text
Give a short evidence-based status for [objective].
Separate prepared, dispatched, running, result submitted, review passed,
integrated, accepted, blocked, cancelled, and superseded work.

For each relevant assignment, name the owner, version, candidate if present,
actual dependency state, latest useful progress/evidence, surviving operation,
remaining budget, and next action. Do not treat a queued prompt, heartbeat,
silent session, or successful reconnect as completed work.

Explain ready-but-idle work with an evidenced blocker or capacity constraint,
an accountable unblocker, and an observation trigger. Consider review and
integration backlog before dispatching more work. Do not fill worker slots
for their own sake or wait for unrelated workers.
```

These are reporting distinctions, not a replacement task-state machine.
Reference: [idle sessions and queues](../OPERATOR_GUIDE.md#6-diagnose-idle-sessions-and-piled-up-queues).

## Prepare a bounded worker handoff

Send this to the coordinator. It asks for a completed project-specific packet,
not for placeholders to be handed to a worker as though they were a contract.

```text
Prepare one execution assignment for [bounded objective].
Fill and register the canonical versioned contract using current project facts:
task and parent objective, requirement revisions, assignment version, dispatch
ID, coordinator association, named owner, inputs, dependency versions and
required states, workspace, write scope, shared resources, authority, needed
capabilities, inherited budget, acceptance, stop conditions, deliverables,
operation observation, checkpoint location, and explicit result return path.

Use only [allowed scope]. Do not perform [excluded effects].
If a required fact is unknown, resolve it or mark the assignment blocked;
do not invent ownership, authority, environment state, or native tool names.

Use verified nonblocking launch if available. Otherwise provide the exact
locally verified operator steps to open a separate worker session and carry
the complete packet there. Distinguish prepared packet, delivery/launch
acknowledgement, and evidence that execution actually began.
```

For the receiving worker, prepend this to the **completed packet**:

```text
You are the execution worker for the attached assignment, not a second
coordinator. Confirm the assignment identities, ownership, workspace, scope,
dependencies, authority, budget, acceptance, and return path before effects.
Inspect current work and surviving operations. Stop for incompatible ownership
or unknown effects rather than assuming they ended with the previous session.
Own your execution handles, checkpoints, and evidence. Return an identified
candidate and result through the packet's agreed channel.
```

References: [assignment contract](../FIRST_SESSION_AND_ORCHESTRATION.md#8-give-every-assignment-a-complete-versioned-contract),
[worker launch](../OPERATOR_GUIDE.md#5-launch-workers-with-an-explicit-task-and-job-handoff),
and [manual fallback](GETTING_STARTED.md#manual-worker-fallback).

## Return a worker result

```text
Submit the result for [task / assignment version / dispatch ID].
Include the coordinator association, a result ID, input/contract versions,
and the immutable candidate or accessible preserved snapshot.

Map each acceptance criterion to the actual observation and outcome.
Identify changed artifacts, exact checks and their candidate/environment,
review limits, uncertainties, surviving operations and real handles,
remaining inherited budget, and the next action.
Link suitable evidence artifacts; do not include secrets or private logs.
Freeze this submitted candidate. If it changes, submit a new candidate identity.
Do not report integration, deployment, or acceptance that did not occur.
```

A branch label alone is not enough to identify what was checked.
Reference: [candidate verification](../FIRST_SESSION_AND_ORCHESTRATION.md#15-verify-results-on-the-actual-candidate).

## Recover context without reclaiming ownership blindly

Use in a continuation or replacement session with access to the target
project's records and checkpoints.

```text
Recover context for [objective/assignment] from authoritative records.
Identify the intended role, coordinator/assignment identities, requirements,
active owners, pending steering, previous attempts, remaining budget/authority,
accepted candidates, and next action.

Recover actual tracked and untracked work bytes and accessible artifacts,
not only summaries or hashes. Inspect live operations and uncertain effects.
Preserve useful failed hypotheses and valid unaffected worker assignments.

Do not infer abandonment from silence or reset ownership by editing an epoch.
Before conflicting writes, require a supported fence/stop or confirmed handover
from the former owner. If unavailable, limit work to safe inspection or
isolated preparation and report the blocker.
Continue only the next ready action within current authority.
```

Reference: [context recovery](../OPERATOR_GUIDE.md#7-recover-context-and-coordination-without-losing-work)
and [ownership restoration](../FIRST_SESSION_AND_ORCHESTRATION.md#13-preserve-recoverable-work-and-restore-ownership-safely).

## Capture intent before a disruption

Use while a healthy actor can still access the relevant intent. If you expect a
reset, capture before resetting; after-the-fact reconstruction is not equivalent.

```text
Before [planned reconnect/reload/handoff], preserve the pending intent that
is actually accessible, including original text, recoverable attachments,
sender/intent identity, order, destination, and known delivery/application
evidence. Keep original captures unchanged and append reconciliation events.
Use suitable controlled storage, not a public commit of private conversations.

Identify coverage gaps: unsent UI text, upstream queues, attachments, provider
jobs, or other material this host cannot export. Do not claim to back up
inaccessible content. Give exact assisted capture steps where available and
report remaining gaps before disruptive actions.

Preserve surviving operation handles, candidate/work snapshots, pending
cancellations and constraints, and the incident's inherited recovery budget.
Do not invent provider IDs or assume a local journal creates exactly-once delivery.
```

If a message cannot be recovered, ask the operator to supply the missing intent
and label the gap. Do not synthesize a supposedly original queued message.
Reference: [assisted backup, reconnect, and restore](../FIRST_SESSION_AND_ORCHESTRATION.md#assisted-backup-reconnect-and-restore).

## Recover a connection and reconcile before replay

Use a healthy actor with demonstrated observation/recovery controls. A broken
session cannot be assumed capable of supervising its own recovery.

```text
Investigate [connection/incident] using the narrowest verified recovery control.
First inspect captured intent, pending cancellations/constraints across all
affected connections and resources, surviving jobs, candidate artifacts,
operation handles, and delivery/application/effect evidence.

Do not automatically cancel stateful jobs or assume a timeout stopped them.
Before new effects or declaring another lane unaffected, screen the relevant
pending steering. Preserve original intent identities and append observations.

If reconnect is authorized and needed, record the actual control used and
the new connection generation. Reconcile real effects and surviving results
before retrying anything with an unknown outcome.

Replay only valid pending intent in bounded, causally correct chunks.
Honor newer cancellations; do not blindly replay FIFO or deduplicate distinct
legitimate intentions merely because their text is identical.
Keep the inherited recovery allowance and stop at its limit.

Report recovered work, applied intent, suppressed actions, remaining unknowns,
and the next accountable action. Reconnect success alone does not close
the incident or replace the coordinator's ownership.
```

Reference: [queued-intent and connection recovery](../FIRST_SESSION_AND_ORCHESTRATION.md#10-back-up-queued-intent-reconnect-and-apply-pending-work).
This protocol cannot repair a host/provider defect or guarantee job recovery.

## Review and integrate the actual candidate

```text
Assign review of [immutable candidate/snapshot] for [task and assignment].
Check requirement revisions, contracts, acceptance evidence, relevant failure
modes, and the actual configuration/environment. Report concrete findings
against this candidate and disclose limits to review independence.

Have the authorized integration owner apply the eligible candidate to
[integration target] within the assigned write/resource scope.
Check the combined result using the project's existing validation mechanisms.
If conflict resolution, dependencies, or substantive content change, identify
the new candidate and renew affected evidence. A clean merge is not proof
of behavioral compatibility.

The coordinator should record acceptance only for the current or explicitly
adopted valid assignment and the actual candidate/effect target.
Preserve stale useful output for revalidation, but do not auto-accept it.
Avoid accepting duplicate reports of the same logical result twice.
```

Reference: [candidate-specific verification](../FIRST_SESSION_AND_ORCHESTRATION.md#15-verify-results-on-the-actual-candidate).
Required gates remain required even if a worker is unavailable.

## Prepare a release without implying permission

```text
Prepare the release path for [project / candidate / intended target].
This request authorizes [specific preparation scope] only.
It does not authorize publication, environment mutations, migrations,
credential changes, or other external effects unless already explicitly
covered by the project's recorded authority.

Assign bounded execution to an owner with the relevant workspace/resources.
Discover the actual build, artifact, configuration, platform, and validation
mechanisms; do not assume a cloud, container system, or pipeline product.
Prepare the necessary files/runbook and perform only authorized checks.

Return the candidate and artifact identity, required gates, observed evidence,
target, authority coverage/gaps, recovery constraints, and exact remaining
action. Distinguish files prepared, automation exercised, environment changed,
and release verified. A generated pipeline is not proof of active protections.
```

A deployment coordinator remains a coordinator. A single deployment executor
can own a bounded release assignment; if several workers are needed, return
the decomposition to the coordinator rather than quietly combining roles.

References: [deployment roles](../OPERATOR_GUIDE.md#9-assign-deployment-coordination-and-execution-explicitly)
and [deployment/build reference](../DEPLOYMENT_BUILD_INSTRUCTIONS.md).

## Authorize a specific release action

**Only send this if you are actually granting the stated authority.** Replace
every bracketed field and do not include effects you have not approved.

```text
I authorize [named executor/assignment] to perform [specific release effects]
for [candidate/artifact identity] on [exact destination/environment].
Scope and limits: [permitted resources, timing, budget, and exclusions].
Required gates: [evidence/approvals/health criteria that must hold].
Recovery authority: [permitted rollback/recovery actions and stop conditions].

Record this grant in the project's authority record. Before effects, confirm
candidate, target, assignment, required gates, and resource ownership still
match the grant. Reuse existing authority where it covers the same action;
do not infer expanded authority from a replacement session or changed target.

Execute through the assigned worker using demonstrated controls.
Preserve operation handles and reconcile uncertain effects before retries.
Observe the actual destination and required health criteria.
Report what changed, which candidate is present, remaining risks, and the
next action. Do not claim that code rollback reverses data changes or that
backup existence proves recovery.
```

Reference: [release identity, authority, and state](../DEPLOYMENT_BUILD_INSTRUCTIONS.md#5-track-release-identity-authority-and-actual-state)
and [interrupted deployment recovery](../DEPLOYMENT_BUILD_INSTRUCTIONS.md#6-recover-interrupted-deployment-work-without-duplicate-effects).
