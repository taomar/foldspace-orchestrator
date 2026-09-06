# Prompt cookbook

These are **ordinary-language prompts**, not native slash commands, installed
tools, or guarantees that the host can perform the requested action. Replace
bracketed fields and provide the referenced project records through a supported
mechanism. A request to report capability evidence must not be satisfied by
inventing that evidence.

Use the [getting-started guide](../docs/GETTING_STARTED.md) for adoption. The
[canonical protocol](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md) and
[operator guide](OPERATOR_GUIDE.md) define the full contracts behind these
short prompts. Start the coordinator with the compact
[bootstrap entry](../protocol/BOOTSTRAP.md), not the entire reference pack.
Before any new run, use the mandatory
[run-configuration interview](../protocol/RUN_CONFIGURATION.md).

To upgrade an existing FoldSpace setup, use the single
[pinned in-place upgrade prompt](../docs/GETTING_STARTED.md#upgrade-without-resetting-live-work),
not a new-project bootstrap. Read its queued-session warning before pasting.

All coordinator prompts retain the
[persistent role/action gate](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md#persistent-role-and-action-admission):
answer from held evidence/compact coordination state or route existing-owner-first
before tools/skills. "Continue/fix it" changes intent, not role; child coordinators
have the same boundary. Execution prompts authorize workers to execute.

## Contents

- [Start a bounded project task](#start-a-bounded-project-task)
- [Upgrade an existing setup](../docs/GETTING_STARTED.md#upgrade-without-resetting-live-work)
- [Approve or decline run controls](#approve-or-decline-run-controls)
- [Bootstrap transition examples](#bootstrap-transition-examples)
- [Coordinator role routing cases](#coordinator-role-routing-cases)
- [Prevent and recover missed idle delivery](#prevent-and-recover-missed-idle-delivery)
- [Steer work without losing prior intent](#steer-work-without-losing-prior-intent)
- [Ask for status that distinguishes progress from activity](#ask-for-status-that-distinguishes-progress-from-activity)
- [Triage a queued bootstrap outside its queue](#triage-a-queued-bootstrap-outside-its-queue)
- [Prepare a bounded worker handoff](#prepare-a-bounded-worker-handoff)
- [Safe assignment and uncertain delivery cases](#safe-assignment-and-uncertain-delivery-cases)
- [Return a worker result](#return-a-worker-result)
- [Recover context without reclaiming ownership blindly](#recover-context-without-reclaiming-ownership-blindly)
- [Capture intent before a disruption](#capture-intent-before-a-disruption)
- [Recover a connection and reconcile before replay](#recover-a-connection-and-reconcile-before-replay)
- [Review and integrate the actual candidate](#review-and-integrate-the-actual-candidate)
- [Prepare a release without implying permission](#prepare-a-release-without-implying-permission)
- [Authorize a specific release action](#authorize-a-specific-release-action)

## Start a bounded project task

Use with the public bootstrap URL below or an already available `BOOTSTRAP.md`.
No clone is needed. Do not preload the entire protocol and operator guide.

```text
Use FoldSpace Orchestrator for [new/existing project] in this repository.
Read only this entry first:
https://raw.githubusercontent.com/taomar/foldspace-orchestrator/main/protocol/BOOTSTRAP.md
Outcome: [specific result].
Acceptance: [observable criteria].
Allowed scope: [components/files and compatibility constraints].
Budget: [effort/cost/retry allowance].
Authority: [permitted actions]. Excluded effects: [publication/deployment/etc.].

Stay coordinator across messages/answers/events and continuation/compaction.
Before tools/skills, answer from held evidence/compact coordination state or
route to the existing owner, eligible executor or bounded sub-orchestrator.
No source/domain research or implementation, even a quick lookup/edit.
Ask only real decisions/control gaps; approval permits dispatch, not role change.
Follow BOOTSTRAP.md: reconcile intent/run mode and valid supplied answers.
Keep one unanswered question outstanding. After each delivered answer, including
a question-tool result, take the next admitted coordination read, question,
review/final approval request or dispatch. No status-only "recorded"
exit or extra "continue" between answers. For pending work use known compact
state/task records; ask only material selection or exact location/access gaps.
Yield only for a real wait with gap, owner and supported event/manual action,
following actual host question lifecycle. No scans, catalogs, polling or full-job waits.

Before any workers, including discovery/research, or direct external LLM calls,
ask me to approve exact supported models/role defaults/fallbacks, each model's
supported reasoning minimum/default/maximum, external consent (disabled is
valid), and run budgets/units, allocations, concurrency, retries and stop rules.
Do not silently use runtime defaults, assume missing budget is unlimited,
or treat Copilot authorization as direct external-call consent.

Preserve the current instructions, requirements, work, owners, operations,
pending steering, and existing authority. Reuse authoritative records.
Identify the current coordinator and verify the host capabilities required
for the first assignment. Record unsupported behavior honestly.
After approval and an available budget reservation, dispatch the next ready,
authorized bounded task through a demonstrated path,
or prepare a complete operator-carried packet without claiming it has started.
If not already localized, assign a setup worker to pin one source commit,
copy the needed linked references and license without overwriting instructions,
adapt active root/child/executor roles/core and supported tool profiles,
verify discovery and disclose instructional limits, then route the outcome.
Before relying on later coordinator messages, prove idle receipt/pickup and
arm independent observation or establish an accepted operator-carried handoff.
Publish durable intent/results before notifying; "sent" alone is not delivery.
```

Reference: [starting or upgrading a project](OPERATOR_GUIDE.md#1-start-a-new-project-or-upgrade-an-existing-one).

## Approve or decline run controls

Use the questionnaire rather than accepting a packet with unresolved fields.
These are decisions for the target run, not credentials or model guarantees.

```text
Conduct the mandatory interview with at most one unanswered question outstanding.
Reuse valid supplied/prestaged answers. On an answer or targeted read result,
reconcile and advance to the next missing question or review/final approval;
do not end at acknowledgement. Use supplied evidence or one known-short compact
coordination/capability read or needed approved bootstrap/configuration reference,
not source investigation or domain research. If unavailable, ask the exact
evidence/access question or advance an independently answerable field.
Follow actual host question lifecycle; yield only for a real wait with owner
and actual resume event/manual action, never invented self-wake.
Show only model IDs and reasoning choices supported by evidence for this host.
Ask my approved providers/models, role defaults/overrides and fallback list;
per-model reasoning minimum, maximum and selected default; explicit external
LLM consent; and aggregate budget with measurable units and stop policy.
Mark fixed reasoning N/A and ask me to accept that limitation.
Do not launch discovery workers or probe external endpoints while approval
is missing. Role-admitted interview preparation may continue.
```

To decline external calls:

```text
Direct external LLM API calls are disabled for this run.
This does not disable already-approved Copilot-managed sessions.
Record denied external consent and do not send repository data to an endpoint
to evaluate models, test credentials, or estimate costs.
```

To opt in, only after the interview has established the other run settings:

```text
I approve direct external LLM calls only to [provider and exact endpoint],
using [approved exact model IDs], for [purpose], with [permitted data categories].
Use credential reference [secure reference, never the key value].
External cap and units: [approved measurable bound], within [parent allocation].
All other endpoints, models, purposes, data, and expanded limits remain denied.
Record approval source/time and policy version; do not ask again for every
call already covered by this scope.
```

See [approved and blocked examples](../protocol/RUN_CONFIGURATION.md#dispatch-and-recovery-examples)
for invalid bounds, unsupported settings, exhausted budgets, and uncertain charges.

## Bootstrap transition examples

These are finite **documentation-level input/transition cases**, not executed
host traces or an executable evaluator. They exercise the
[advance-or-wait contract](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md#opening-turn-and-return-control-contract)
without workers, inference calls or invented controls. The fictional task IDs
below illustrate how recorded facts are reused, not a supplied live backlog.

| Case and input | Next permitted transition | Invalid exit or shortcut |
|---|---|---|
| Reported trajectory: new run selected; outcome question tool returns "continue the pendings"; known compact task index exists | Consume the answer; read that index or use supplied equivalent context. Derive recorded candidates and acceptance, then ask the next missing decision. Final new-run approval still gates dispatch. | "Recorded; blocked until scope, criteria, limits and approval" with no read or actual next question |
| Same answer; supplied index records `DOC-A` with accepted scope/criteria and no competing candidate | Reuse those facts; ask the next unresolved run decision, such as the allowed exact models. Do not ask the user to rewrite `DOC-A`. | Invent new tasks, infer permission to execute, or return only a checkpoint |
| Same answer; index has two materially different candidates `DOC-A` and `API-B` | Ask one focused selection: "Which recorded task should this run prioritize: DOC-A or API-B?" | Select silently or demand an entirely new objective |
| Pending record location unknown or named record inaccessible | Ask "Which task/state record or task ID identifies the pending work?" or request access to the named record; alternatively advance an independently answerable model/budget field while preserving the gap. | Broad scan, unapproved discovery worker, guessed backlog or indefinite global hold |
| Supported question tool returns an actual model/consent/budget answer synchronously | Reconcile against current evidence and prior answers, then ask the next unresolved field or show configuration review and request final approval. | Treat the answered tool as still waiting, demand "continue", or auto-approve |
| Operator asks to start the approval process; an exact model allowlist is then recorded; role default remains unset | Start/advance the interview and actually ask the next decision, for example "Which allowed model should be the default?" If already supplied, ask the next genuinely unresolved role override/reasoning field instead. | End with "Next is role assignment; workers remain blocked", or treat starting the approval process as final approval |
| Question is actually unanswered or tool is suspended | Keep just that question outstanding; identify operator and actual answer/cancel control or supported delivered-answer event. Follow the host lifecycle and reconcile when input arrives. | Claim the tool completed, queue more questions behind it, poll or invent self-wake |
| Required model-selection/accounting capability lacks evidence | Use supplied evidence or one known-short relevant metadata read; if insufficient request exact evidence/approved demonstrable assisted steps and continue independent questions. Hold affected dispatch. | Launch a discovery worker to satisfy its own approval gate, guess N/A, or research every provider |
| Partial prestaged answers | Validate/reuse valid answers and ask the next genuinely missing/conflicting/unsupported field. | Replay resolved questions or fill unknowns with defaults |
| Fully populated but unapproved prestaged inputs | Validate required evidence, summarize objective/scope/version/settings/limits and request final explicit approval. | Replay all sixteen questions or treat staged external consent as run approval |
| Same-run continuation with valid approval, current ownership/evidence and reservable allowance | Reconcile steering/effects/ledger, reserve and dispatch the next eligible bounded assignment through its verified path; reuse pinned references. | Re-interview without a changed scope, reset budgets/owners or stop at "ready" |
| Approved assignment delivered to an execution worker | Confirm identities/ownership/dependencies/settings/reservation and execute within the assigned scope; report a specific failed gate if any. | Adopt coordinator interview/one-read restrictions and acknowledge without execution |
| Worker delivery/completion/result event reaches coordinator | Reconcile actual launch/result evidence and IDs; acknowledge delivery only as delivery. Take next eligible review/acceptance/dispatch action, without waiting for unrelated workers or duplicating effects. | Mark delivery as completion, leave a cleared wait unchanged, or replay an already applied result |
| Hard budget/authority block with no eligible independent action | Hold affected effects; name the exact cap/reservation or missing grant, accountable approver/ledger owner, and required decision/evidence/manual action. Preserve live operations and uncertain charges. | Raise a cap, free uncertain reservations, cancel stateful work or claim indefinite automatic resumption |

For the reported trajectory, the finite path is:
`new run -> outcome answer received -> compact pending-state reconciliation ->
focused scope/next missing run question -> validated policy summary ->
final explicit approval -> reserved, owned dispatch`.
If a real input/evidence gap interrupts this path, expose its exact unblocker
and actor. A synchronous answer resumes the path in that request; a yielding
host resumes on its actual answer event. No generic continuation prompt is
part of the contract.

The screenshot reports a completed response after an answer, not a reproduced
host hang. These examples correct protocol behavior; they neither reproduce nor
repair the photographed host. A separate message-delivery/wake failure requires
independent evidence, not this same diagnosis.

## Prevent and recover missed idle delivery

Send this setup request only to a responsive coordinator. It configures the
[existing safety contract](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md#idle-delivery-safety-contract),
not an automatic grant to launch diagnostic workers or restart sessions:

```text
For this approved run, establish a recoverable delivery path before depending
on an idle coordinator. Use existing authoritative intent/result records,
preserving original payloads, IDs, candidates, owners and ledger references.
Verify actual receiver receipt and useful pickup after a response ends, not
only active-session delivery or a "sent immediately" acknowledgement.
Establish closed-session resumption only if that lifecycle is needed and safe.

Name the armed independent observer/runner or explicitly accepted operator,
finite receipt/pickup windows, cursor, alternate alert/control route, allowed
resume/replacement actions and inherited recovery reservation/attempt limits.
Register observation then recheck compact pending state before yielding.
If native automation cannot be demonstrated, provide exact observed manual
steps and obtain acceptance of that assisted mode; do not invent a supervisor.
No polling coordinator, repeated "continue", unapproved probe or new budget.
```

Use this recovery packet through the established **independent** route, never
as another message to the stalled recipient:

```text
Recover missed delivery for [session/intent/result IDs] within
[existing approved policy, recovery authority and remaining reservation].
Preserve accessible queued text/attachments and the authoritative records
before any disruptive action. Do not invent inaccessible messages.
Compare sender submission receipts with receiver events and application/
result-pickup state. Inspect actual jobs, effects, owners and held charges.
Use the verified state-appropriate open/resume/reattach control outside the
broken queue. If it fails, perform only the approved fenced ownership handoff;
do not create a competing coordinator or restart healthy jobs.
Reconcile newer steering and completed work before restoring valid unapplied
intent with original IDs. Consume existing results; deduplicate late delivery.
Confirm receipt and correct next action/disposition. Stop at the finite
recovery limit and alert the named operator by the alternate supported route.
```

These are finite documentation cases, not claims of live host fault injection:

| Case | Prevention or recovery outcome |
| --- | --- |
| Send while active succeeds; first post-idle send reports success but has no receiver event | Idle-resume activation fails; do not certify unattended delivery. Armed independent observation detects the missing receipt, opens one incident and uses the accepted resume/manual route. |
| Result arrives between the coordinator's last read and idle | Observation is registered before a final pending-state/cursor recheck; that read or the actual subscription covers the arrival. No uncovered yield or polling loop. |
| Worker finishes after coordinator idles or its CLI closes | The identified result remains accessible outside the queue. The independently supported observer/operator resumes pickup; no replacement worker repeats completed execution. Closure survival is not assumed from idle success. |
| UI queue is visible but persistence is unknown | Preserve accessible exact payloads and attachments before reload/clear/restart. Record uncaptured scope; no fabricated backup or blind drain. |
| Receiver applied intent but acknowledgement was lost | Reconcile task/effect evidence before retry; do not duplicate application, reservations or publication. |
| Same result arrives late at old and replacement coordinators | Current coordination ownership and logical candidate/effect identity gate acceptance; fence obsolete authority and consume once within the demonstrated boundary. |
| Observer fails or recovery allowance is exhausted | Alternate failure alert/manual owner takes over if demonstrated. Otherwise mark coverage unavailable, preserve existing jobs and hold new unattended dependent work; no recursive watcher agents or unlimited retries. |
| Real unanswered approval question | Wait on the operator's actual answer control; never synthesize approval or treat silence as a restart trigger. |
| No independent automatic resume/control exists | Use the explicitly accepted operator-carried packet and exact observed steps; do not claim self-recovery or block independently answerable interview questions. |
| Queued cancellation conflicts with an older apply | Reconcile captured cancellation before replay; hold affected effects across lanes, preserve live jobs and do not bulk-flush the queue. |

## Coordinator role routing cases

These finite cases specify **document-level expectations**, not executed host
proof, a runtime evaluator or claims about any adopter's loaded instructions.
Apply the [section 2 gate](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md#persistent-role-and-action-admission)
and [section 7 routes](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md#7-reconcile-steering-and-run-a-continuous-dispatch-cycle)
before tools/skills on each input. Relevant host exercises require existing
approval and non-destructive setup scope; no mandatory broad fan-out.

| Input or condition | Expected route and evidence | Invalid shortcut |
|---|---|---|
| User asks known status or a brief conceptual question | Short answer from held evidence/known concepts, with uncertainty; at most one truly compact coordination-state read if needed | Inspect source or start a docs-research chain to embellish the answer |
| User clarifies an authentication/UI requirement while its worker is active | Persist requirement/steering ID, assignment version and authority; use compact owner index and actual current-task control path to the existing worker/sub-orchestrator; distinguish sent, received and applied | Root runs Context7 research, reads source, plans Dockerfile edits or edits configuration; launch a duplicate worker |
| Question depends on source behavior or current external documentation | Route to existing responsible research/execution owner or admit a bounded research worker; consume its short evidence report | Treat one source read or one docs call as permitted "bounded coordination" |
| "Fix it" requests a new isolated feature with no suitable owner | Record scope/acceptance; admit an eligible versioned executor with owned resources and approved remaining allowance | Root becomes executor; unrelated task is disguised as steering or put in busy chat |
| Approved capability spans multiple dependent areas | Bound a sub-orchestrator by parent tasks/resources/allocation; it delegates real executors, inherits/tightens policy and reports concise evidence/handles; root keeps goal/status/acceptance | Child runs implementation because it is below the root; new project-wide ledger, arbitrary worker count or root whole-job wait |
| Owner is busy; a genuine answer/correction arrives | Use demonstrated current-task control or exact assisted route; do not suppress genuine steering | Append an independent assignment as "correction" or wait for an IDLE label as a delivery guarantee |
| Owner or dispatch is uncertain | Quarantine new assignments, retain reservations/ownership/effects, reconcile actual receiver/jobs/results before replacement or fencing | Missing ACK frees the lane or authorizes duplicate work |
| No verified nonblocking dispatcher | Exact approved operator-carried independent-worker packet and actual opening/return steps, or specific unavailable capability; launch is not receipt/start/completion | Coordinator executes as fallback or claims a prepared packet is a running worker |
| Interview question returns a model/reasoning/consent answer | Reconcile and ask the next missing question or request final approval; missing model evidence uses compact metadata/precise question, not an unapproved worker | Status-only "recorded", domain research, discovery before approval or approval inferred from an answer |
| Complete approved assignment reaches an executor | Validate assignment/ownership/settings/reservation then perform assigned execution and return evidence | Import coordinator interview/one-read restrictions and stop at acknowledgement |
| Reconnect, context compaction or "continue" reaches a coordinator | Recover role/authority from active core/packet and compact state, then apply the same gate; role change needs supported explicit handoff | Self-rename as executor while still owning coordination |
| Setup boundary probe finds no native allowlist, or a generic shell/write tool remains exposed | Record loaded role/core/profile and actual coverage in root/child/executor; label unscoped capability instructional, not enforced; record higher-priority conflict and supported route | Invent config/tool IDs, claim Markdown overrides the host or guarantees short reasoning/no stalls |
| Coordinator already owns a long operation | Stop new execution, preserve exact handle, effects, write owner and reservation; arrange accountable observation/recovery and supported safe worker transfer, or report exact transfer gap | Abandon the job, blindly cancel a stateful operation, restart/poll the coordinator or duplicate effects |

## Steer work without losing prior intent

Use when changing priorities or requirements while workers may still be active.
Do not assume a chat message instantly updates every worker.

```text
Record this steering change against [objective/requirement identity]:
[the new requirement, priority, constraint, or cancellation].

Retain coordinator role and apply action admission before tools/skills.
Preserve original intent with stable requirement/steering ID and new version.
Use the compact task/owner index, not source, to identify affected assignments,
shared resources and live effects. Route to the existing owner first through
demonstrated current-task controls, including when busy; retain uncertain
ownership and reservations. Independent future work stays in durable backlog.
Apply the change to future dispatch and reconcile affected owners before new
incompatible effects. Preserve useful prior work and unaffected assignments.
Use supported controls for cancellation or handover; a new record alone
does not stop an existing writer. Keep inherited budgets and prior authority.
Report what was captured, delivered, acknowledged, and actually applied,
plus any uncertainty and the accountable next action.
```

Reference: [operator guide](OPERATOR_GUIDE.md), particularly sections 4 and
6, and the [canonical queued-intent policy](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md#10-back-up-queued-intent-reconnect-and-apply-pending-work).

## Ask for status that distinguishes progress from activity

```text
Give a short evidence-based status for [objective].
Use held evidence or one known compact coordination-state read; be honest about
unknowns. Delegate source-dependent investigation or detailed evidence review.
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
Reference: [idle sessions and queues](OPERATOR_GUIDE.md#6-diagnose-idle-sessions-and-piled-up-queues).

## Triage a queued bootstrap outside its queue

Do **not** send this to the stalled session. Use it only with an already
responsive, appropriately authorized observer, or follow the steps manually
through verified host controls. A new observer does not acquire project ownership.

```text
Inspect [affected session/request] without posting messages into its queue.
Use only available independent read-only host controls. Identify accepted/
delivered input, current invocation/tool, last observation, surviving jobs,
and the producer/target of any schedule, timer, auto-continue mode, or hook.
If a route is inaccessible, say so rather than claiming the session is idle.

Preserve accessible queued intent, owners, handles, approvals and reservations.
Do not restart, cancel, clear messages, pause automation, or spend on diagnostic
workers/external calls without authority for that specific action.
Distinguish pausing future automated submissions from stopping live operations.
Return evidence, the narrowest supported next action and its required authority,
then end the response; do not poll or append another recovery prompt.
```

See [early-stall and automation triage](OPERATOR_GUIDE.md#early-bootstrap-with-little-or-no-worker-activity).
The bootstrap entry is prevention for a new interaction, not a command that can
interrupt an already blocked host.

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
Include the approved run-policy version, effective allowed model/reasoning,
external consent scope, and parent budget reservation. Descendants may only
inherit or tighten limits. An unapproved fallback is blocked, not a reason to
silently pick a different or more expensive model.

Use only [allowed scope]. Do not perform [excluded effects].
If a required fact is unknown, resolve it or mark the assignment blocked;
do not invent ownership, authority, environment state, or native tool names.

Reserve task/receiver/resources/budget and persist task_id, assignment_version,
dispatch_id and current coordinator authority before send. Admit no extra task
to a busy, dispatching, recovering, uncertain or resource-unavailable worker;
keep backlog in the ledger, not chat. Default one active assignment and at most
one unacknowledged assignment dispatch per worker, not a second pending task.
Answers/steering/cancellations use supported control routes, not this backlog.
READY/IDLE does not prove next delivery. If supported, session creation can carry
this complete approved packet without an extra readiness exchange.
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
Record acceptance tied to the exact current task/version/dispatch and authority
in your durable result/operation records before new effects; then execute.
ACK transport success is not ownership fencing. Preserve actual start/result
evidence even if ACK is lost; never restart on a duplicate delivery.
Inspect current work and surviving operations. Stop for incompatible ownership
or unknown effects rather than assuming they ended with the previous session.
Reuse the valid approved run policy; do not restart the coordinator interview
or apply its preparation limits as a one-tool execution cap. Once gates pass,
execute this assignment, not just acknowledge it. Return exact missing gates
to the coordinator when blocked; do not broaden authority or reset allowance.
Own your execution handles, checkpoints, and evidence. Return an identified
candidate and result through the packet's agreed channel.
Publish it in the agreed durable location before notification. Hand pickup
observation to the assigned independent owner before returning; preserve actual
receipt status without waiting for the coordinator's whole review. Don't send
repeated wake messages or become the coordinator.
```

References: [assignment contract](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md#8-give-every-assignment-a-complete-versioned-contract),
[worker launch](OPERATOR_GUIDE.md#5-launch-workers-with-an-explicit-task-and-job-handoff),
and [manual fallback](../docs/GETTING_STARTED.md#manual-worker-fallback).

## Safe assignment and uncertain delivery cases

These are finite **document-level scenarios**, not reproduced host failures or
executed runtime tests. Use existing task/assignment/dispatch/result identities
and the canonical [admission](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md#admit-new-assignments-not-chat-backlog)
and [uncertainty](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md#uncertain-dispatch-is-not-failed-execution)
rules, with the [independent pickup route](#prevent-and-recover-missed-idle-delivery).
Choose receipt windows from actual host/workload evidence within approved limits,
not constants from this table.

| Case and finite evidence | Required disposition | Unsafe shortcut |
|---|---|---|
| Worker owns task A and is busy; task B becomes ready; A also needs a genuine user answer or cancellation | Leave B in the authoritative ledger or use another eligible reserved worker. Deliver A's answer/control through demonstrated priority/control or exact assisted steps. Reconcile cancellation before affected effects. | Queue B, suppress the answer as a nudge, or assume stopping the chat stopped A's job |
| Worker replies READY, then its turn ends with UI IDLE | Record liveness for that interaction only. Check current ownership, jobs/resources, settings and actual delivery route before a new assignment; no readiness probe loop. | Infer next-message receipt/wake, workspace isolation, applied model or free resources |
| Host supports creation with one complete approved assignment | Persist task/version/dispatch and reserve receiver/resources/budget before creation; bind actual session ID. Worker validates current authority/workspace/settings, records exact acceptance before effects, then records start. | Count successful creation as execution or require READY followed by a second idle-message roundtrip |
| ACK window expires, but the worker's durable operation record and actual job handle show a current running task | Quarantine new assignments to the lane; keep reservation/owner, adopt or observe the same job through a supported route and reconcile receipt separately. | Mark task STALE, revoke in ledger, free budget and redispatch once |
| Send returns an error; receiver, transport and operation evidence establish no execution and no possible late start from the old attempt | Restore a valid route, reconcile newer controls/usage, then permit one justified attempt only within remaining approved history/limits; preserve task and assign a new dispatch ID/version as appropriate. | Treat the error string or absent incoming event alone as nonexecution proof; retry an unchanged failure indefinitely |
| Delivery remains unknown and the old actor cannot be stopped, safely surrender or be fenced at a shared target | Hold that conflicting scope and its resources/unknown charges; name the missing control/effect evidence. Permit only independently eligible isolated/read-only work. | Treat a new ledger epoch or a fresh chat as a fence; duplicate shared writes |
| Old assignment version ACK/start arrives after a safe transfer | Preserve the observation and reconcile effects, but reject obsolete ownership; enforce the actual write boundary. Current owner keeps the assignment. | Let a late receipt revive the old assignment |
| Same candidate/result arrives twice, including under a new transport/result-event ID | Check logical task/assignment/candidate/effect identity and current acceptance; consume only the missing disposition. Integrate each logical effect at most once within demonstrated controls. | Deduplicate only message IDs or integrate twice |
| A current completed candidate/result is reachable but its original ACK never arrived | Reconcile actual effects and identities, retrieve the existing result and proceed to review/acceptance; retain the receipt gap as unknown. | Wait forever for ACK or rerun the completed task |
| Parent/coordinator goes idle and misses a published result notification | Armed independent observer or accepted operator retrieves the durable result, uses the alternate supported pickup route and reconciles current coordination authority. | Assume sender success or a dormant sibling is observation; send repeated continue/resume/pings |
| Recovery allowance is exhausted, or usage/reservations remain unknown under a cap | Retain consumed/held amounts; stop new affected attempts and expose exact ledger evidence/approval or assisted action needed. Preserve live jobs; independent eligible work may continue. | Release reservations on timeout, invent a fresh replacement budget, kill stateful jobs or freeze unrelated work |

Results may arrive out of order. `dispatched` is not `running`, submitted results
are not acceptance/integration, and transport quarantine is not task failure.
If a required route cannot be demonstrated, report that specific limit and use
an accepted assisted handoff; this table installs no control.

## Return a worker result

```text
Submit the result for [task / assignment version / dispatch ID].
Include the coordinator association, a result ID, input/contract versions,
and the immutable candidate or accessible preserved snapshot.
Include approved/effective policy, actual model/reasoning evidence, usage and
reservation changes in their original native/external units, and unknown charges.

Map each acceptance criterion to the actual observation and outcome.
Identify changed artifacts, exact checks and their candidate/environment,
review limits, uncertainties, surviving operations and real handles,
remaining inherited budget, and the next action.
Link suitable evidence artifacts; do not include secrets or private logs.
Publish the identified result where coordinator/recovery owner can read it
without this chat, then notify. A send receipt is not receiver pickup.
Freeze this submitted candidate. If it changes, submit a new candidate identity.
Do not report integration, deployment, or acceptance that did not occur.
```

A branch label alone is not enough to identify what was checked.
Reference: [candidate verification](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md#15-verify-results-on-the-actual-candidate).

## Recover context without reclaiming ownership blindly

Use in a continuation or replacement session with access to the target
project's records and checkpoints.

```text
Recover context for [objective/assignment] from authoritative records.
Identify the intended role, coordinator/assignment identities, requirements,
active owners, pending steering, previous attempts, remaining budget/authority,
accepted candidates, and next action.
Restore run configuration, external consent, consumed/reserved allowance, and
uncertain in-flight charges. A replacement does not reset any of them.
Block new work that would violate the cap; reconcile charges before reallocation
and ask for approval before expanding scope or limits. Do not kill stateful jobs
merely because accounting reached a cap.

Recover actual tracked and untracked work bytes and accessible artifacts,
not only summaries or hashes. Inspect live operations and uncertain effects.
Preserve useful failed hypotheses and valid unaffected worker assignments.

Do not infer abandonment from silence or reset ownership by editing an epoch.
Before conflicting writes, require a supported fence/stop or confirmed handover
from the former owner. If unavailable, limit work to safe inspection or
isolated preparation and report the blocker.
Continue only the next role-admitted coordination action within current authority;
route execution to its existing responsible worker or an eligible new executor.
```

Reference: [context recovery](OPERATOR_GUIDE.md#7-recover-context-and-coordination-without-losing-work)
and [ownership restoration](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md#13-preserve-recoverable-work-and-restore-ownership-safely).

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
Reference: [assisted backup, reconnect, and restore](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md#assisted-backup-reconnect-and-restore).

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
Recheck the approved effective model/reasoning and external consent for replay;
retain reservations until usage and effects are reconciled.

Report recovered work, applied intent, suppressed actions, remaining unknowns,
and the next accountable action. Reconnect success alone does not close
the incident or replace the coordinator's ownership.
```

Reference: [queued-intent and connection recovery](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md#10-back-up-queued-intent-reconnect-and-apply-pending-work).
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

Reference: [candidate-specific verification](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md#15-verify-results-on-the-actual-candidate).
Required gates remain required even if a worker is unavailable.

## Prepare a release without implying permission

```text
Prepare the release path for [project / candidate / intended target].
This request authorizes [specific preparation scope] only.
It does not authorize publication, environment mutations, migrations,
credential changes, or other external effects unless already explicitly
covered by the project's recorded authority.

Assign bounded execution to an owner with the relevant workspace/resources.
Apply this run's approved model/reasoning, external-call consent, and reserved
budget to deployment workers and any external evaluation/research calls.
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

References: [deployment roles](OPERATOR_GUIDE.md#9-assign-deployment-coordination-and-execution-explicitly)
and [deployment/build reference](../protocol/DEPLOYMENT_BUILD_INSTRUCTIONS.md).

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

Reference: [release identity, authority, and state](../protocol/DEPLOYMENT_BUILD_INSTRUCTIONS.md#5-track-release-identity-authority-and-actual-state)
and [interrupted deployment recovery](../protocol/DEPLOYMENT_BUILD_INSTRUCTIONS.md#6-recover-interrupted-deployment-work-without-duplicate-effects).
