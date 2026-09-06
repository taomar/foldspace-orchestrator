# Your guide to running projects with GitHub Copilot

**Revision 2.1.7 · 6 September 2026**

This pack uses **GHCP** to mean **GitHub Copilot**. It supports projects in which research, implementation, and architecture evolve together. Apply it to the actual repository and installed Copilot environment; it does not assume your stack, deployment destination, or session controls.

The main orchestrator coordinates the project. Execution belongs to assigned worker sessions. Its role persists across every user message, synchronous answer, event, continuation/reconnect/compaction and run approval. Before tools/skills or investigation apply the [role/action gate](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md#persistent-role-and-action-admission): answer from held evidence/compact coordination state or route existing-owner-first. This governs every prompt below; "continue", "act", "review" or "implement" asks the coordinator to route execution, not change role. Useful independent work should run in parallel as soon as approval, dependencies, resources, reserved budget and capacity permit.

| File | Who uses it | Result it should produce |
| --- | --- | --- |
| [FIRST_SESSION_AND_ORCHESTRATION.md](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md) | The bootstrap coordinator and subsequent project orchestrators | Project-specific instructions, approved run settings and budgets, assignment and recovery mechanisms, durable state, and demonstrated capability limits. |
| [OPERATOR_GUIDE.md](OPERATOR_GUIDE.md) | You | Prompts and practical steps for starting, directing, inspecting, recovering, and handing over work. |
| [DEPLOYMENT_BUILD_INSTRUCTIONS.md](../protocol/DEPLOYMENT_BUILD_INSTRUCTIONS.md) | An assigned deployment coordinator and execution workers, or one bounded deployment executor | The actual build and release implementation, verification evidence, and operational runbook, reported to the main coordinator. |

These documents provide operating instructions. They do not install a running supervisor or prove that an IDE or provider can dispatch, resume, or recover sessions.

For the coordinator's opening interaction, supply only [BOOTSTRAP.md](../protocol/BOOTSTRAP.md) and the compact project brief/state. This operator guide is for the operator and scoped follow-up reading, not another large mandatory opening attachment. Keep the full references accessible without automatically loading all of them.

You can supply the public [bootstrap URL](https://raw.githubusercontent.com/taomar/foldspace-orchestrator/main/protocol/BOOTSTRAP.md) directly in the target repository's chat. No local pack or clone is required. Use the [URL-first prompt](../docs/GETTING_STARTED.md#send-a-bootstrap-prompt); after approval, an assigned setup worker pins and copies the needed references, adapts existing project instructions, verifies discovery and continues the user's build task. The [localization contract](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md#localize-github-references-without-cloning) preserves existing state and prevents conflicting overwrites.

Revision 2.0 remains the historical public baseline at commit `38e9ce28964d8038333a2034a6ff02087b4652f9`. Its checks and archive statements are not 2.1 guarantees; see [release notes and provenance](../reference/REVIEW_AND_CHANGES.md). The [run-configuration guide](../protocol/RUN_CONFIGURATION.md) supplies a questionnaire, compact examples and reference, not generated live settings.

## 1. Start a new project or upgrade an existing one

Open the intended repository. Provide the current outcome, known constraints, existing authority, and any other active work. Leave unknown facts unknown. **Before launching any orchestrated worker, including discovery/research, or making any direct external LLM API call, complete the configuration interview and explicitly approve the recorded run.** The current coordinating chat may do safe local planning and bounded capability reads to ask the questions; it is not retroactively blocked. After approval and budget reservation, the bootstrap coordinator delegates repository discovery and setup implementation to workers and uses their evidence to configure coordination.

The coordinator acknowledges supplied intent/run mode and reuses valid answers, including [optional prestaged inputs](../protocol/RUN_CONFIGURATION.md#optional-prestaged-interview-inputs). **One question at a time means one outstanding unanswered question**, not one answered decision per response. When an answer arrives, including a synchronous question-tool result, reconcile it and take the next bounded read, focused question, configuration review/final approval request or approved action. No extra "continue" is needed. A status-only "recorded/blocked until..." exit is invalid while such a step is available.

Use supplied evidence or one named compact coordination/state/capability read or needed approved bootstrap/configuration reference, not source investigation, domain-docs research, catalogs, setup generation or drills. If insufficient, ask the exact evidence/access question or advance an independently answerable field; missing dispatch approval is not a global interview hold or permission to launch discovery. For "continue pending work", use known compact state/checkpoint/task records to derive candidates and acceptance, ask focused selection for material ambiguity, or request the exact unknown location/access. Do not demand a rewritten backlog or invent tasks.

For a real wait, show **phase, last completed action, exact gap/owner, supported resume event or manual action**. Follow the actual host question lifecycle: a suspended tool is not a completed response, and an answered tool is not waiting. Keep independent eligible steps moving before yielding; do not poll, auto-continue, claim self-wake or pretend unsupported controls exist. Valid same-run approval avoids re-interview; fully staged but unapproved inputs still need validation, summary and final approval. See the [owning transition contract](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md#opening-turn-and-return-control-contract).

For a new project, use:

```text
Use FoldSpace in this new target project; no pack clone or attachments.
Read only this compact entry first:
https://raw.githubusercontent.com/taomar/foldspace-orchestrator/main/protocol/BOOTSTRAP.md
Outcome and acceptance: [what to build and how to recognize it]
Scope and authority: [constraints, permitted actions, or explicitly unknown]

Stay coordinator across messages/answers/events and continuation; approval
changes authority, not role. Before tools/skills apply the entry's gate:
answer from held evidence/compact coordination state or route existing-owner-first,
then eligible executor/bounded child coordinator; ask real decisions/control gaps.
No source/domain research or implementation, including quick calls/edits.
Reconcile intent and supplied answers; keep only one unanswered question open.
After each answer/tool result, take the next bounded question/read/approval step,
not a status-only exit. Yield only for a real wait with gap, actor and actual
resume event/manual action; use the host's supported question lifecycle.
Use the entry's full-URL source map only as needed, not a full-pack preload.
Complete its mandatory model/reasoning, external-consent and budget interview
and obtain final approval before any worker or direct external LLM call.
Public reference GETs must not upload private data or use external inference.

After approval, reserve budget and assign a setup worker to pin one source
commit, preview conflicts, copy necessary linked references and LICENSE,
and adapt existing project-native instructions/state without overwrites.
Reuse POLICY/CAPABILITIES/PROJECT_STATE and the authoritative ledger.
Have the setup worker verify active root/child/executor roles and supported
tool profiles; generic execution tools mean instructional limits, not enforcement.
Verify discovery/handoff, then continue the build task by routing to its executor.
Keep useful independent work moving and return when only waits remain.
Before relying on later messages, establish durable intent/results and the
idle-delivery safety contract: actual receiver receipt/pickup, demonstrated
idle-resume, and armed independent observation or an accepted operator handoff.
Report unsupported tools/permissions instead of inventing fetched files or controls.
```

**Updating an existing FoldSpace setup?** Use the
[pinned in-place upgrade prompt](../docs/GETTING_STARTED.md#upgrade-without-resetting-live-work),
including its warning for sessions that only queue messages. That guide owns
source comparison, scoped active-instruction migration and rollback limits.
An upgrade alone is not a new run and retains valid same-run approval.

For first adoption in an existing project, or starting/continuing project work, use:

```text
Use FoldSpace in this existing target repository; no pack clone or attachments.
For first adoption, read this compact public entry; otherwise reuse the
current pinned local entry without automatically refreshing it:
https://raw.githubusercontent.com/taomar/foldspace-orchestrator/main/protocol/BOOTSTRAP.md
Mode: [new run / same-run continuation]
Outcome and constraints: [actual project goal and limits]

Preserve your coordinator role across answers/events and continuation.
Before tools/skills admit only coordination: answer from held evidence/compact
state or route to existing owner, eligible executor or bounded sub-orchestrator.
No source/domain investigation or quick implementation; ask exact control gaps.
Reconcile supplied state and answers, then take the next permitted bounded step:
read known compact pending-task state, ask a focused missing question,
request final approval or perform approved coordination. An answered tool is
not waiting; no status-only exit or extra "continue" between answers.
If the task record is unknown/unavailable, ask its exact location/access or
advance an independently answerable field. Yield only for a real wait with
gap, actor and supported resume event/manual action.
Preserve objectives, decisions, tasks/owners,
unfinished work, operations, steering, evidence, approvals and accounting.
A new run explicitly reconfirms settings; continuation retains valid approval
and pinned local references. Obtain missing approval before affected dispatch.

After approval, use an owned, budgeted setup worker to compare a pinned source
revision with existing localized references and instructions, preview conflicts,
and apply only authorized adaptations. Preserve source provenance and LICENSE.
Reuse POLICY/CAPABILITIES/PROJECT_STATE and the current ledger; no competing store.
Do not orphan workers, reset usage/reservations, or free unknown charges.
Have the setup worker adapt and verify active root/child/executor roles/core and
native profiles where supported; disclose instructional limits and host conflicts.
Correct conflicting active rules through review, verify the discovery/
handoff path, and route the implementation goal with unrelated
eligible work unblocked. No deployment/publication authority is implied.
Do not rely on "sent" as receiver delivery. Preserve results outside the queue
and establish verified idle pickup/recovery or an accepted operator-carried
handoff before work depends on it. No repeated wake messages or budget reset.
```

### The bootstrap questionnaire

Use the [complete reference, prestaging checklist and compact examples](../protocol/RUN_CONFIGURATION.md). Cover these decisions **before discovery dispatch**, asking only unresolved fields one at a time through the supported interaction. This is not a mandatory question replay; split unresolved compound fields, reuse valid supplied answers and request final approval separately:

1. **“Is this a new run, or continuation of which approved run ID and policy version?”** Reconcile earlier records first. A new run requires explicit reconfirmation; a new session continuing the same run does not require asking again at every tool call.
2. **“Which providers, model families, and exact supported model IDs are allowed?”** Record the explicit default, coordinator/execution/review/integration/deployment overrides as applicable, and approved fallback IDs. Family names alone are insufficient; no hardcoded versions or silent host defaults.
3. **“For each allowed model, what minimum, maximum, and default reasoning do you approve?”** Verify that provider/model's supported categorical order before checking `minimum <= default/effective <= maximum`. Fixed/unsupported reasoning must be explicitly `N/A / not configurable` and accepted by the operator. Do not invent scales or map labels across models.
4. **“Are direct external LLM calls disabled, or what exact scope do you approve?”** Require an explicit answer even if disabled; reuse valid supplied answers. Copilot-managed requests are separate. Direct endpoints default **DENIED** until provider/endpoint, exact model, purpose, permissible data categories, secure credential reference (never the key), and budget are approved. Unknown consent blocks affected calls, not safe local planning.
5. **“What aggregate run cap and measurable units do you approve, and how should native/external and worker/task/provider allocations divide it?”** Use an explicit amount in currency or measurable host credits/tokens/calls. Missing is not unlimited. Deliberately uncapped scope needs explicit opt-in naming its scope and acknowledging the risk.
6. **“What maximum concurrency, retry/replacement allowances, and stop/escalation rules do you approve?”** Record the authority needed for any increase and what uncertainty blocks new affected work.
7. **“Do you approve this resolved run configuration, consent scope, budget and enforcement limitations?”** Present run ID/version, operator, source, timestamp and evidence references. Record the explicit answer before starting workers or direct external LLM calls.

If the host cannot select or prove the actual model/reasoning, mark the control **unavailable** or **assisted** and block autonomous dispatch claiming it. Exact approved manual configuration is possible with evidence before effects. Never send secrets or private repository/user data to probe capability/pricing. Approved fallbacks must fit their own reasoning bounds, consent and remaining budgets; model costs may differ, so no silent more-expensive switch. A new provider/endpoint/scope, unapproved fallback, or expanded limit requires renewed explicit approval, not repeated per-call asking inside a valid scope. If no interactive answer or complete approved record is available, hold affected dispatch rather than inventing consent.

### Where approval and accounting live

`POLICY` is authoritative for approved settings/version, operator/source/time, consent, budgets and ledger ownership (or a link to the existing authoritative run ledger). `CAPABILITIES` supports those decisions with host/model/reasoning, pricing/usage evidence and limitations. `PROJECT_STATE` points to the active run, approval and ledger. Do not generate a competing `RUN_CONFIG` file from the reference guide.

The ledger preserves run ID, caps/units/allocations, reservations, actual usage, held unknown charges, remaining balances and reconciliation history. Reserve against the parent and aggregate run allowance **before parallel dispatch** with actual supported atomic coordination, or serialize coordinator/manual reservations. A Markdown file is not an atomic lock. Descendants inherit or tighten only; retries/replays/replacements do not reset consumption. Reconcile actual charges/effects before reallocation; in-flight unknown charges are not free budget.

Keep incomparable units in separate ledgers under the authoritative run view. Do not invent token/credit/currency equivalence or claim accurate monetary enforcement without price/usage evidence. Record known hard limits, estimates and uncertainty; if exposure cannot fit the approved policy, hold new affected work for explicit resolution. A cap, approval, support or uncertainty violation blocks **new affected work** and escalates under explicit authority; it does not automatically kill stateful operations. Written policy is not proof of enforced host controls.

An upgrade should produce a targeted migration, with obsolete active instructions corrected or clearly superseded. Keeping an old rule in an active entrypoint can undo the new behavior even when the replacement document is sound. Retain historical decisions as history, without presenting them as current instructions.

Do not declare a live worker abandoned because the new protocol uses different labels. Inspect its task and effects before transferring ownership. Give work that remains valid a route to completion.

## 2. Confirm activation in a fresh session

The setup should leave a short discoverable entrypoint, compact project state, task and operation records, and links to detailed evidence. The exact supported instruction and agent configuration depends on the installed environment. A configuration file existing on disk is not evidence that a new session loaded it. See [GitHub instruction support](https://docs.github.com/en/copilot/reference/custom-instructions-support) and [VS Code custom agents](https://code.visualstudio.com/docs/agent-customization/custom-agents).

After the run interview, explicit approval and reservation, have an assigned setup or verification worker exercise discovery and handoffs. Then start a fresh coordinator continuing that run and use:

> Load this project's current session instructions and compact state. Identify your coordination role, instruction revision, objective, selected route, active assignments and owners, latest accepted evidence, pending user steering, existing authority, and next ready work. Identify the active run ID, versioned run_policy_ref and approval source/time, applied effective_config and evidence, consent scope, budget_reservation and remaining balances/unknown charges. Confirm whether this is same-run continuation or a new run requiring explicit reconfirmation. Cite the records you used. State which model/reasoning, reservation, dispatch, observation, cancellation, and replacement controls were demonstrated, which are only instructional, and which require exact assisted steps. Identify conflicting or missing state. Keep implementation and long execution assigned to approved workers.

Check that its answer matches the real project. If instructions exist only on an isolated branch, make the accepted version available through the project's normal workflow to the sessions that need it. Delegate any activation repair to a worker.

A useful setup demonstration establishes that:

- Discovery/evaluation workers cannot bypass approval; actual model/reasoning settings and external consent match the approved scope, and supported atomic or serialized reservations prevent run-budget oversubscription.
- Fresh target root and child coordinators load the active sticky role/action gate and route clarifications rather than invoke execution tools; a spawned executor performs its harmless approved assignment. Inspect actual native tool profiles and state-write scope non-destructively. Unsupported allowlists or generic tools mean instructional limits, not enforcement; record higher-priority conflicts and supported assisted routes.
- A worker receives a real task and workspace, and returns discoverable evidence.
- Concurrent dispatch actually starts independent work; queued messages or role descriptions do not count as running workers.
- The coordinator remains available while worker execution continues, using a supported mechanism.
- A replacement can recover a checkpoint, identify existing work and jobs, and establish ownership safely.
- Unsupported controls and exact manual steps are recorded honestly.

If a delegation call holds the coordinator until a long worker operation finishes, separate model context alone has not met the responsiveness requirement. Use a verified asynchronous session mechanism or a separately opened worker session. Do not claim that the coordinator can respond while its runtime is blocking it.

VS Code documents session orchestration from Agent Host sessions. Verify availability and controls in the installed surface; honor any actual runtime confirmations. This capability is distinct from a stateless subagent invocation. [Agent Host session orchestration](https://code.visualstudio.com/docs/agents/run/sessions/manage-sessions#orchestrate-sessions-from-agent-host-sessions).

## 3. Keep the main orchestrator available

The coordinator owns the outcome, priorities, task dependencies, assignment ownership, acceptance decisions, and current coordination state. It should read compact evidence and make decisions. It should assign the work needed to produce that evidence.

| Activity | Responsible execution role |
| --- | --- |
| Read or update compact task state; assign work; inspect concise runtime status | Main coordinator, using bounded operations |
| Investigate the repository, research options, or diagnose failures | Assigned investigation worker |
| Edit code, instructions, infrastructure, or other project artifacts | Assigned implementation worker |
| Run builds, tests, benchmarks, migrations, or long commands | Assigned execution worker |
| Launch, monitor, cancel, and reconcile a tool or provider job | Its assigned execution worker, using verified controls |
| Examine detailed changes and validation evidence | Assigned review or verification worker |
| Resolve code conflicts, merge a candidate, and run combined checks | Assigned integration worker |
| Build and execute an authorized release path | Assigned deployment execution workers |

The coordinator may inspect a concise candidate-specific result and record acceptance. That does not make it the owner of source reads, domain-docs lookups, quick code/config/instruction edits, execution skills, merge commands, detailed review, tests or deployment. Action kind and ownership, not duration, define the boundary. It applies to nested and deployment coordinators; explicit supported ownership handoff is required to change role. A child gets parent tasks/scope/resources and inherited or tighter settings/authority/budget, not a competing ledger. The root retains goal/status/acceptance; child coordinators delegate to real executors without blocking the root on whole jobs.

Use this correction if a coordinator starts doing execution work:

> Retain your coordinator role on every message/answer/event, including this correction. Stop starting execution; before tools/skills answer from held evidence or compact coordination state, otherwise record intent and route. Inspect the task/owner index, not code: send current-task steering with stable ID/version/authority to the existing responsible worker or bounded sub-orchestrator through demonstrated controls. Do not disguise unrelated tasks as steering or duplicate busy/uncertain ownership. Admit a new versioned executor only when appropriate, isolated, approved and budgeted. Preserve any running operation's exact handle, observed/uncertain effects, write ownership and reservations. Arrange accountable observation/recovery; transfer only if supported and safely reconciled, never abandon or blindly cancel a stateful job. Continue eligible coordination. If nonblocking dispatch/control is unavailable, provide the exact approved independent-worker handoff or specific gap, not local execution, polling or self-restart.

Use the [single upgrade guide](../docs/GETTING_STARTED.md#upgrade-without-resetting-live-work)
to persist this correction in active roles/core, rather than repeatedly pasting
reminders. Prompt policy cannot guarantee short model reasoning or prevent
host stalls; it is enforced only to the extent demonstrated native restrictions
actually apply.

A worker may run a background operation when its environment supports it and the task permits it. The worker remains accountable for the handle, logs, observation, result retrieval, and effects. A detached process with no recoverable handle or owner is not a successful handoff.

Do not expect an idle or stopped coordinator to wake itself because a Markdown file tells it to. Recovery requires another active actor or a separately running supervisor whose observation and dispatch controls have been verified. If unattended supervision is required, assign its scoped design and implementation; do not claim it exists before it has been exercised.

## 4. Favor useful parallelism during ordinary work

Give an outcome, then let dependencies and capacity determine the assignments. A ready task should not wait for an unrelated task to finish merely because both were part of the same batch.

For normal continuation of an approved run, use:

> Continue toward [outcome] as coordinator under the current protocol and approved run_policy_ref. Apply role/action admission before tools/skills; continuation never permits implementation or domain investigation. Use held evidence/compact task-owner state to reconcile steering, applied settings, consent, usage and reservations. Route current-task changes to the existing owner through supported controls; preserve same-run authority. Reserve within aggregate/parent limits before eligible independent dispatch; do not queue new tasks to busy/uncertain owners. Use bounded sub-orchestrators only where the scope needs them and real executors for research, code, review and integration. Handle results without a whole-batch wait and report evidence, active work, bottlenecks and next coordination action.

Useful concurrency may include implementation of independent components, an experiment that resolves a design uncertainty, preparation of a deployment environment, and review of an already completed component. These can overlap when their actual dependencies allow it.

To increase parallelism, use:

> Examine where independent work is waiting unnecessarily. Show the ready tasks, dependency edges, writable scopes, shared-resource and budget reservations, approved concurrency, actual model/reasoning support, verified worker capacity, and review or integration backlog. Dispatch additional useful workers only where current approval and all remaining caps permit it; request explicit authority before expanding limits. Split a blocking assignment only when the split has a clear contract and acceptance result. Give the concrete reason for every ready task that remains undispatched. Do not increase concurrency by creating duplicate assignments, speculative rewrites, or outputs that cannot be reviewed and integrated.

There is no universal starting count or guaranteed speedup. Choose concurrency within the operator-approved maximum from the current project and measured conditions. A real provider limit, shared test environment, unstable interface, or full integration queue can justify a local limit. Record that reason and revisit it when the condition changes.

Isolated files are only one part of independence. Workers may still collide through a schema, lockfile, shared database, port, test identity, deployment target, or external side effect. Assign one owner for shared writes or use a verified coordination mechanism. Let read-only investigation or other independent work continue while a specific write is serialized.

When completed outputs are accumulating, prioritize the review and integration workers that release useful capacity. Pause only the work feeding the bottleneck where necessary. Do not block unrelated progress with a project-wide barrier.

For a quick status view, use:

> Show the current outcome, run ID/policy version, actual model/reasoning settings, consent scope, caps/units, usage, reserved/unknown charges and remaining budget, critical path, ready work, active assignments and owners, blocked dependencies, pending review and integration, latest verified evidence, and next action. Separate measured status from unknown status. Explain whether current capacity is constrained by dependencies, worker/session limits, provider throttling, shared resources, or result processing, and cite the evidence for that conclusion.

These are ordinary prompts, not built-in slash commands. Any generated shortcut must be verified in your installed environment before you rely on it.

## 5. Launch workers with an explicit task and job handoff

Avoid giving the same writable task to multiple conversations. If you open a worker manually, have the coordinator register the assignment and prepare its complete packet first, after run approval and atomic or serialized budget reservation. Manual launch is not an exemption: configure the exact approved model/reasoning and provide evidence before effects; if the host cannot prove those controls, block dispatch claiming them. A prepared packet is not a started task.

### Admission and readiness

Follow the canonical [admission rule](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md#admit-new-assignments-not-chat-backlog),
not the UI label. Default to one active assignment and at most one outstanding
unacknowledged assignment dispatch per worker, with zero pending task assignments
in chat. These are not two task slots. Keep backlog in the single authoritative
ledger. No additional task goes to a busy, dispatching, recovering, uncertain or
resource-unavailable lane. A completed turn/IDLE label does not prove jobs ended,
resources were released, or next-message delivery will work. Additional workers
require independent ready work, isolation, verified capacity and approved budget.

Answers, steering, cancellations/changed constraints, status/results and recovery
controls are not extra assignments. Use demonstrated control/priority routes or
exact assisted steps for busy sessions; do not suppress genuine answers or use a
queued stop as proof of control. A stopped chat request may leave jobs running.
Host tools can still queue internally; this policy does not promise they cannot.

`READY_CHECK`/`READY` are optional application markers, not built-in commands.
"READY, wait for IDLE, send" leaves a new delivery gap; neither marker proves
workspace exclusivity, model/limits, execution or the next wake. Where supported,
create the worker with its one complete approved packet after reserving
task/receiver/resources/budget and persisting task/version/dispatch identities.
The receiver validates current authority and records exact acceptance before
effects, then starts the assignment; creation/send success is not that evidence.
After reconnect/reload, reconcile current owners/jobs/results rather than loop
through readiness probes. Use the [finite cases](EXAMPLES.md#safe-assignment-and-uncertain-delivery-cases)
for the expected distinctions, not as claims of live-host behavior.

Use this worker-session prompt with that packet:

> You are the execution worker for [task ID and assignment version], reporting to [coordinator or task registry]. Read the attached packet and applicable project instructions. Before effects verify run_policy_ref, actual effective_config and evidence, external consent scope or denial, and budget_reservation against the authoritative parent/run ledger. Use only approved exact models, per-model reasoning and fallbacks; do not silently select defaults, expand consent or reset limits. Verify your workspace, ownership, inputs, dependencies, write scope, authority, budget, acceptance criteria, and return channel. Inspect existing work and operations before acting. Execute this bounded assignment and preserve recoverable evidence. For long operations, record the actual returned job handle, execution location, log or artifact locations, observation method, progress signals, and recovery actions. Report dispatch acknowledgement separately from execution; report running only when evidence establishes that execution actually began. Distinguish heartbeat from useful progress. Return evidence and unresolved effects, then follow the submission boundary; do not independently expand scope or integrate shared changes.

The coordinator should supply these fields, using the project's existing schema where available:

| Packet content | Why you need it |
| --- | --- |
| Stable task ID, assignment version, unique dispatch attempt ID, reserved receiver/actual execution owner, coordinator epoch | Correlates pre-send reservation, acceptance and execution without inventing duplicate assignment IDs; ACK alone is not fencing. |
| Objective, acceptance evidence, relevant decisions and contracts | Gives the worker an independently understandable result. |
| Dependencies, workspace, branch or worktree, permitted writes and reserved resources | Defines readiness and isolation. |
| Granted authority and its source; remaining task budget and attempts | Preserves limits across replacements. |
| `run_id`, `run_policy_ref`, operator/source/time approval, `effective_config` and actual model/reasoning evidence, external consent | Binds the worker to approved exact settings and data scope; same-run handoffs retain authority. |
| `budget_reservation`, authoritative ledger/parent references, allocation units, usage/remaining and held unknown charges | Prevents oversubscription, invented conversions, and consumption resets across children/retries/replays. |
| Actual prior work, checkpoints, failed attempts, running jobs, uncertain effects | Prevents restarting completed or still-running work. |
| Durable result/intent location, receiver receipt and pickup evidence, checkpoint | Makes completion recoverable even if its notification never reaches the coordinator. |
| `delivery_recovery_ref`: idle-resume evidence, observer/operator, alternate alert/control route, receipt/pickup windows and recovery allowance | Establishes who actually notices and resolves failed delivery; an idle sibling or successful send is not coverage. |

For every long job, preserve a job record containing the task and assignment, worker owner, operation and target, actual execution identifier, start acknowledgement, logs or artifacts, last observed status and timestamp, latest progress evidence, expected progress signals, and verified cancellation or reconciliation method. If the job produces external effects, include the effect identifiers or idempotency mechanism where supported. Record missing fields as unknown; do not substitute an invented handle.

Each worker result and operation record must also reference `run_policy_ref`, actual applied `effective_config` and supporting evidence, `budget_reservation`, measured usage/units/source/time, unknown or estimated charges, and authoritative remaining balances. Requested settings alone do not establish applied settings. Reconcile billing and effects before releasing reservations.

Observe these distinctions:

| Status claim | What it establishes |
| --- | --- |
| Packet prepared | An assignment is ready to be launched. |
| Transport submission acknowledged | The send/launch tool accepted the request; it may still be queued. This does not prove receiver receipt or execution. |
| Receiver receipt observed | A linked incoming event or receiver acknowledgement proves receipt of the identified intent; it does not prove application or transfer resource ownership. A lost ACK does not disprove execution. |
| Worker or job observed running | Runtime evidence identifies actual execution. |
| Heartbeat received | The observed component is responsive; useful progress is not yet established. |
| Progress observed | A milestone, useful finding, output, or state change advances the assignment. |
| Worker result published | Identified evidence is durably accessible outside the chat queue; notification delivery is separate. |
| Result picked up | The coordinator records review/acceptance/blocked disposition or its evidenced next step for that result. |
| Review passed | The required evaluation accepts the submitted result within its scope. |
| Integration verified | The combined candidate passed the relevant checks. |
| User outcome complete | All required work and delivery effects for the requested outcome are evidenced. |

An exit code alone does not establish every acceptance criterion. A worker saying “done” does not establish review, integration, or deployment. Equally, an ended conversation does not establish that its background job ended.

Keep logical task readiness, delivery observations and operation/results as
separate views in the existing tracker. A valid late start or completed result
can be reconciled without waiting forever for a missing ACK. Do not integrate
the same logical assignment/candidate/effect twice under new notification IDs,
and never let an obsolete ACK/start reclaim current ownership.

## 6. Diagnose idle sessions and piled-up queues

An idle session is a symptom. Task dependencies, runtime scheduling, a tool job, provider limits, session failure, or lost context can produce similar visible behavior. Capture evidence before attributing the cause.

Missing ACK, timeout, "Queued message was not sent", "Session not found", or
unexplained idle means a suspect/quarantined delivery lane, or unavailable
transport only to the extent known. Stop **new assignments** there; retain
operation outcome uncertainty, ownership and reservations. Do not mark the task
failed/stale, automatically revoke it, cancel its job, or redispatch even once.
Inspect receiver events, actual tools/jobs/effects, current assignment, newer
controls, usage and durable results. Observe running work and retrieve completed
results instead of duplicating them.

Retry/replacement must satisfy the canonical
[uncertain-dispatch contract](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md#uncertain-dispatch-is-not-failed-execution):
prove prior nonexecution and exclude obsolete late start, or safely stop/surrender/
fence the actual conflicting writer and reconcile effects/charges. A ledger-only
revocation is not a fence. Without that evidence, name the exact unresolved
boundary and permit only safe independent isolated/read-only work. Retain the
logical task, version/attempt history, consumed/held budget and finite remaining
allowance. The procedure below gives the independent pickup or accepted operator
route for both workers and their parent, not an automatic supervisor.

### Prevent stranded work and recover missed delivery

The [canonical safety contract](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md#idle-delivery-safety-contract)
requires more than a "message sent" acknowledgement. Before depending on an
idle coordinator, the approved setup must establish:

| Protection | What must actually exist |
| --- | --- |
| Durable handoff | Original intent/attachments and identified worker results in the project's existing journal/tracker/result store, readable by the coordinator and recovery owner without its chat |
| End-to-end evidence | Separate submission, receiver receipt and application/result-pickup evidence under the same IDs; a successful send or heartbeat is not enough |
| Idle-resume path | A harmless approved delivery after a response ends produces actual receipt and useful pickup; closed-session reattachment is tested only if claimed |
| Independent observation | An armed existing runner/observer or explicitly accepted operator with finite receipt/pickup windows, durable cursor, actual alternate alert/control route and scoped recovery allowance |
| Safe yield | Register observation, then recheck compact pending state so an arrival around the idle transition is not missed; no periodic "continue" prompts or coordinator polling |

Use existing mechanisms, not a permanently polling model agent. Automatic
coverage is unavailable if the observer also depends on waking the blocked chat,
does not survive the claimed lifecycle, or cannot alert outside it. If the host
cannot demonstrate the automatic path, explicitly agree an operator-carried
handoff and its exact UI/actions before relying on it. Do not leave new unattended
work waiting indefinitely for a capability that does not exist. Genuine unanswered
questions retain their actual operator/answer control; they are not recovery alarms.

When a receipt or pickup window expires, the **independent owner**, not the
blocked coordinator, performs this finite procedure within existing approval:

1. Stop redundant notifications to the affected lane and preserve the original
   queued text/attachments through supported capture or visible manual copying.
   Save accessible task/result records, owners, handles and ledger references.
   Do not clear the queue or reload/restart the app before confirming what is
   recoverable; do not claim uncaptured text was saved.
2. Compare receiver history with sender receipts and actual tools/jobs/effects.
   A completed response plus no incoming event is missed delivery, not a busy
   worker or missing run approval. Open one incident with its exact missing
   receipt/pickup, owner, current state and remaining recovery attempts.
3. Use the demonstrated independent open/resume/reattach action for that idle
   or closed session. A stuck active tool requires its own scoped diagnosis.
   If unavailable or unsuccessful, use an approved replacement packet only
   after establishing one current coordinator and fencing conflicting authority.
   Never rename ownership in records and assume the old writer stopped.
4. Reconcile each saved intent against actual application, completed results,
   newer steering/cancellations, live operations and charges. Restore only valid
   unapplied intent; consume the existing result instead of rerunning its task.
   Keep IDs, causal order, exclusions and uncertain reservations intact.
5. Confirm receiver receipt and correct disposition/next eligible action, not
   just an opened chat or another send receipt. Deduplicate late notifications
   and actual effects. Stop automatic attempts at the approved limit or repeated
   unchanged failure; preserve the packet and issue the exact manual action
   through the alternate operator-visible route.

The handoff must name observed host controls, not invented commands. If no safe
control exists, report that limitation without deleting state, killing unrelated
processes, raising budgets or repeatedly enqueuing wake-ups. This protocol can
make work recoverable and detect missed delivery; it cannot fix the app's
internal queue implementation or guarantee recovery from inaccessible state.

### Completed response versus an actual wait

First distinguish a **completed acknowledgement-only response** from a request
that is still waiting for input or cannot receive messages. In the reported
bootstrap trajectory, "new run" was selected and the outcome answer "continue
the pendings" had returned from the question tool. A final "recorded, execution
blocked until scope/settings/approval" response with no next question/read
violates the transition contract: those dispatch gates do not prohibit asking
the next question or reading known compact task state.

Use that state to derive scope/acceptance, ask focused candidate selection,
or ask the record's exact location/access if unknown. Then advance missing run
decisions and final approval; do not bypass them. A genuine unanswered question
instead waits on its operator and actual answer/cancel control. A hard authority,
capability or budget block names its exact unblocker and accountable actor;
it does not silently reset limits or grant permission.

This documentation fault is established from the old return rules; it does
not establish or repair a host defect. Separately, a completed publication
worker was reported not to receive later requests in its session history:
that is a delivery/wake boundary observation, not evidence it executed this
bootstrap and stopped. The underlying host cause remains unconfirmed.
Use the [finite transition examples](EXAMPLES.md#bootstrap-transition-examples)
for protocol behavior and the independent triage below for an actually blocked
message path; do not conflate the two.

### Early bootstrap with little or no worker activity

**Do not send a recovery prompt to the affected session if it will join the same blocked queue.** Its inability to consume messages is the problem, not an invitation to enqueue more. Use the operator's host UI, an independent read-only observation/control API, or an already healthy authorized observer. If no such route is available, report that limitation; a message, automation tick or instruction file is not an out-of-band control.

| Observed signal | What to establish outside the blocked message path |
| --- | --- |
| No first response and no tool shown | Request accepted/delivered state, supplied context size, selected model/reasoning and run mode, provider/host observations. Do not assume no activity or blame worker count. |
| An active tool invocation | Actual tool/request handle, start/last observation, expected bounded output and surviving process/job. One stuck tool can hold a turn without any worker load. |
| Phase says awaiting input/evidence | Check whether the answer/evidence was already delivered. If so, reconcile and advance instead of retaining a stale wait. If not, identify the exact missing item, owner and actual answer/evidence control; a suspended question is not a completed response. |
| Completed "recorded/blocked" after an answered question | Identify the next permitted read/question/review/approved action under the transition contract. A completed response alone is not a hung host, and a stale wait label does not justify recovery/restart. |
| A worker launch call remains open | Whether the mechanism waits for the entire job rather than returning a usable handle; preserve the existing operation before changing launch mode. |
| Automation or repeated continuation requests | Producer identity, target, trigger, overlap behavior, active invocation and queue acknowledgements; distinguish new work from repeated wake-ups for the same unresolved step. |

When the operator has authority/budget for a harmless native chat, compare a fresh minimal-context, no-FoldSpace-reference response-only request with the compact bootstrap entry. For the first comparison, request only "Reply READY and end your response. Do not use tools, start workers, or change project state." Record what host/repository instructions were still auto-loaded and observed send/first-response/end times. Do not automatically create diagnostic workers or external LLM probes. If even the minimal case stalls, investigate its host/request path before attributing the incident to FoldSpace. If only the full-context case is slow, input/turn work is a hypothesis supported by that comparison, not a measured universal cause.

Keep the incident evidence private: affected host/surface and observed version, session/request IDs, input/acknowledgement times, last useful output, reported model/reasoning and mode, reference-loading route, active tool/job handles, queue capture coverage, and any automation source/target/history. Unknown observations stay unknown. Do not publish prompts, credentials or raw private logs with an issue.

### Automation admission and out-of-band recovery

Automation is a hypothesis until its producer and target are observed. A scheduled workflow may start a new session; a session timer may append a turn; an auto-continue/autopilot mode or hook may keep the current turn active. These are different mechanisms. Verify the actual host's behavior rather than assuming all "automation" is one queue.

1. **Identify the producer without messaging the stalled session.** Inspect available schedules, session triggers, hooks and run mode through their own controls. Record what was checked and what was inaccessible. An empty workflow list in another project/session does not exclude automation in the affected one.
2. **Stop additional submissions only within authority.** Where specifically authorized, pause the identified producer's future triggers through a verified host/UI/API control. Preserve its configuration and already queued intent. Pausing an enqueueing automation is not cancelling a worker, migration, provider job, or all automations.
3. **Reconcile the active request and effects.** Capture accessible queued intent and real operation handles before an authorized interrupt/reconnect. A cancel/stop request must use an actual out-of-band control, not a queued chat message. Do not infer termination or free reservations merely because the chat or automation stops.
4. **Gate resumption at the producer.** Use supported no-overlap/admission controls for the same continuation identity; do not repeatedly enqueue an unchanged awaiting-input/evidence step. If those controls are absent, use an explicit assisted pause/resume rather than claiming prompt-level enforcement. Legitimate distinct intents must not be deduplicated by identical text. Independent authorized observation may continue without feeding the blocked queue.
5. **Resume only the valid pending action.** Preserve owners, budgets, original intent identity and current approval; reconcile unknown delivery, effects and charges first. Automation cannot approve its own missing configuration, select an unapproved fallback, expand limits, or bypass the external-call gate.

If the active session cannot consume input, a new prompt is not the recovery action. Do not clear its queue or replace its ownership to make it appear responsive. Without a supported independent control, leave a concrete operator action and preserved state rather than promising automatic recovery.

Check approval, actual model/reasoning support and budget uncertainty before interpreting a held dispatch as a stall. New diagnostic/recovery workers require approved settings and reservations too. An already active coordinating chat can do safe local reads needed to resolve missing configuration; another worker or direct external LLM call cannot bypass the gate as “diagnosis.”

VS Code's **Add to Queue** waits for the current response to complete; **Steer** applies after the current tool execution finishes; **Stop and Send** cancels the current request and immediately submits the message. A stalled tool could therefore delay queued or steering input—an inference from those semantics, not a diagnosis of your incident. Use the verified controls in your installed surface. Stopping a chat request does not establish whether its subprocess, provider job, or external effects stopped; an execution worker must reconcile the actual operation before a retry. [Sending messages during a request](https://code.visualstudio.com/docs/chat/chat-overview#send-messages-while-a-request-is-running).

Keep these queues separate:

| Queue or wait | What to inspect | Appropriate response |
| --- | --- | --- |
| Project task backlog | Readiness, dependency states, resource ownership, available capacity | Fix a task dependency or dispatch ready work. |
| Copilot chat/message queue | Pending prompts, dispatch acknowledgements, session state, unsent steering | Preserve intent and reconcile which messages were accepted before retrying. |
| Worker/session scheduling queue | Accepted dispatch IDs, running-session count, observed scheduling limits | Adjust dispatch to verified capacity; investigate a stalled accepted assignment. |
| Provider or tool-job queue | Actual job handle, target status, logs, rate-limit or provider errors | Have an execution or diagnostic worker observe that job through supported controls. |
| Review/integration backlog | Submitted results, assigned evaluators, integration-resource availability | Assign capacity to evaluate and integrate useful output. |

Only in a responsive coordinator or healthy authorized observer, use:

> Diagnose the idle state using current evidence. Distinguish project backlog, Copilot queued messages, worker dispatch, provider/tool jobs, and review or integration backlog. Show the oldest actionable items, owners, last observations, expected next event, and unknowns. For each idle or blocked assignment, state its evidenced reason or explicitly mark the reason unknown, name the actor or condition that can unblock it, and identify the next concrete action and its owner. State why each ready task lacks a worker. Keep this coordinator available; delegate log inspection and long diagnostics. Preserve pending steering and current execution before recovery. Continue independent work and propose the smallest corrective action supported by evidence.

If the affected coordinator cannot receive that prompt, use a separate diagnostic session with the project records. Make its initial role read-only diagnosis; it does not become a second coordinator or acquire existing task ownership by being opened.

To back up the queued inputs, reconnect, and restore them, use this prompt in a healthy recovery session within the approved run (or perform safe local inventory before obtaining missing approval):

> Recover the affected agent connection and preserve its queued inputs. Retain the same run_policy_ref, approved settings/consent, actual usage and outstanding reservations. Reconcile actual charges/effects before reallocation; gate any new recovery worker, replay or external LLM call on support and remaining reserved budget. Before reconnecting or restarting it, back up the original pending messages using supported queue capture, export, or visible manual capture; preserve message IDs where available, local recovery IDs where needed, causal order, task references, acknowledgements, pending corrections, and cancellations. Preserve active job handles and actual work separately. Before dispatching work or issuing new effects, reconcile captured cancellations and constraints with current authoritative intent and identify affected tasks and resources across all connections; hold new affected effects while their status is unresolved. Do not automatically cancel live stateful jobs; handle them through verified recovery controls. Use a verified scoped reconnect or restart mechanism from this independent recovery session; delegate long diagnostics and execution to workers if you are coordinating recovery. Establish the current connection and coordination owner, then reconcile which messages were sent, acknowledged, applied, superseded, or still unknown and which jobs are active or complete. Restore only remaining valid intents in causal order, honoring newer constraints and cancellations. Drain bounded chunks with acknowledgements and reconcile their application before retrying an uncertain item. Release independent ready tasks in parallel as their state permits. Do not blindly flush the queue, rerun completed jobs, invent uncaptured text, or enter a repeated restart loop. If a required control is unavailable, preserve the bundle and provide the exact manual steps supported by this installed surface.

Use the following staged procedure for that recovery. Stop when the affected work has a verified path forward.

1. **Capture the queue before disrupting the connection.** Stop adding duplicate prompts. Preserve the original text of each available pending input, its source session and message ID where available, capture order, task references, visible send or acknowledgement state, and any error or request identifiers. Assign a local recovery ID when a message has no exposed runtime ID; do not present that as a provider ID. Keep the original capture unchanged and record later reconciliation separately. Distinguish new instructions, corrections, cancellations, and repeated continuation prompts. Use only supported export, capture, or manual access; another session must not assume it can read a private queue. Identify uncaptured items or gaps explicitly.
2. **Preserve the work and execution state.** Record the affected connection and session, expected activity, last observation, active assignments, writable resources, checkpoints, branches, actual job handles, logs, and uncertain effects. Preserve unfinished work and make the queue backup accessible to the recovery actor before a reconnect, cancellation, replacement, or restart. Do not clear the only available queue copy as a recovery shortcut.
3. **Diagnose from an independent healthy actor.** An assigned diagnostic or recovery worker identifies the implicated session, connection, or job through available controls. Compare heartbeat, useful progress, and workload-specific expectations. A quiet log or elapsed time alone does not establish failure. Check dependencies if work cannot start. A diagnostic session initially has inspection scope; it does not automatically acquire coordination or write ownership.
4. **Reconcile captured control intent before independent dispatch.** Check captured cancellations, corrections, and new constraints against current authoritative intent before treating any lane as unaffected or issuing new effects. Map their actual dependency and effect scope across all connections; a stop-deployment instruction may affect work on a healthy connection. Hold new affected effects while their status is unresolved, without automatically cancelling live stateful jobs. Dispatch demonstrably independent ready work through healthy capacity and assign review or integration help where useful. This screening does not require replaying every queued task instruction first. Do not impose a global pause without an actual shared dependency or constraint.
5. **Reconnect or restart the affected connection through verified controls.** Have the recovery executor use the narrowest supported control that addresses the diagnosed or explicitly requested connection recovery. If the environment requires a manual action, provide its actual steps and the preserved recovery packet. Expand to restarting GHCP or its host only when the narrower scope is unavailable or insufficient. Do not invent a reconnect tool or shortcut, reset the repository, or discard task history. Record the attempt and result; if the same recovery fails without new evidence, stop that loop and identify the remaining blocker and next diagnostic action.
6. **Establish current connection and ownership.** Verify the recovered connection and its session identity. Confirm one active coordinator before new coordination dispatch. Determine whether the prior worker or coordinator can still write, and confirm or enforce loss of conflicting write authority through a supported mechanism before transferring ownership. Preserve coordinator and assignment versions on a simple transport reconnect; revise only affected records when ownership, scope, or contracts change, adopt valid surviving workers, and retain history, limits, and uncertain effects. If the old owner cannot be fenced or stopped, restrict replacement work to safe inspection or isolated preparation until ownership is resolved.
7. **Reconcile messages and jobs before replay.** Match the backup against supported runtime acknowledgements, durable task records, actual artifacts, and provider/job state. Distinguish never sent, sent but unacknowledged, acknowledged but not yet applied, applied, superseded, and unknown states according to available evidence. Delivery acknowledgement does not prove the requested work happened. Inspect a live or completed operation before deciding whether an input still requires action. A connection or UI restart is not proof the operation stopped.
8. **Restore remaining valid intent in causal order.** Preserve the original queue, then derive a restoration plan that respects newer cancellations, corrections, dependencies, and authority. Do not resend applied or superseded instructions as new work. Keep unresolved items visible and reconcile them before a potentially duplicate effect. Send a bounded chunk appropriate to actual connection capacity, record acknowledgements, and check resulting task state before advancing or retrying uncertain delivery. Queue replay is restoration of instructions, not permission to rerun a completed job. As restored prerequisites and constraints become known, dispatch independent ready tasks in parallel without waiting for unrelated queue items. Do not blindly bulk-flush the backup.
9. **Verify restored continuity.** Confirm the connection, current owners, active jobs, restored instructions, and remaining gaps. Record each original input's disposition and evidence while leaving unknown items explicitly unresolved. Do not reconstruct uncaptured text from a guess; identify the missing input for the user. Preserve the observed cause or mark it unknown, along with evidence for any reproducible runtime issue.

Fully automatic queue backup, reconnect, and restoration require supported queue access, recovery controls, durable records, and an independent actor that remains able to run. Verify each capability. Otherwise prepare the complete recoverable bundle and give the exact manual action for the missing capability; do not claim a file instruction itself can restart a disconnected agent or restore inaccessible messages.

A new prompt can itself join the blocked queue. Repeatedly submitting it is not a monitoring mechanism. A supervisor or alternate session can help only through controls it actually possesses.

These instructions can reduce duplicate launches, unsafe replacement, and avoidable idle work. They cannot repair an IDE or provider defect by themselves. Diagnosing such a defect requires the relevant runtime logs, errors, versions, and reproduction evidence. Do not report a particular root cause from the symptom alone.

## 7. Recover context and coordination without losing work

Checkpoint after meaningful progress, before long operations, before a handoff, and when context quality degrades. Use observed warning signs such as repeated rediscovery, forgotten constraints, contradictory status, and inability to identify the next action. Do not use conversation length as the sole diagnosis.

Checkpoint the active run/approval version, operator/source/time reference, actually applied settings/evidence, consent, reservation IDs, usage/remaining by unit and held unknown charges. Same-run handover/adoption preserves authority without a new interview for each action; verify settings on the receiving host before effects. A new run must reconcile and explicitly reconfirm settings. Existing workers are inventoried and migrated prospectively, not orphaned for having older packets.

For worker replacement:

> Recover [task ID/session] using its actual artifacts and latest job state. Preserve partial work, pending steering, attempts, run approval/settings/consent, actual usage, reservations including unknown charges, and remaining limits. Check whether the previous worker or operation can still produce effects. Establish safe ownership transfer, then prepare or launch a fresh worker with a compact packet. Continue independent assignments. Identify anything that could not be recovered or verified.

For a responsive but overwhelmed coordinator:

> Prepare a coordinator handoff now using bounded coordination updates. Index the objective, current route, authority, pending steering, ready tasks, active owners, worker sessions, operation handles, submitted results, blocked dependencies, attempts, uncertain effects, and next actions. Delegate any detailed artifact inspection needed. Produce the replacement packet and the exact supported steps for establishing one active coordinator without duplicating execution.

For a coordinator that is already inaccessible:

> Recover coordination from the project records and actual runtime evidence. First inspect safely; do not assume prior sessions or jobs stopped. Reconcile assignment ownership, queued instructions, workspaces, results, and uncertain effects. Establish one active coordinator before dispatching conflicting work. Delegate execution to workers and resume independent ready tasks whose state and authority are known. Carry forward the existing task history and granted authority.

There are three distinct capabilities: correction within a functioning session, replacement through an active actor, and unattended recovery through a verified independent supervisor. Record which the project has demonstrated. Do not present a manual replacement packet as automatic recovery.

## 8. Explore alternatives and change direction

For an alternative approach:

> Within the approved run, reserve budget and assign a bounded investigation of [alternative or question]. Use approved exact model IDs and per-model reasoning, with direct external LLM calls denied unless their endpoint/model/purpose/data/credential-reference/budget scope is explicitly approved. Do not probe with private data. Identify the current assumptions it challenges, the smallest experiment that distinguishes the options, its budget, stopping condition, and decision. Run independent experiments in parallel where useful and capacity permits. Preserve the current implementation and evidence. Compare findings against our actual constraints, distinguish observations from hypotheses, and recommend whether the route should change.

For an intentional pivot:

> The objective or constraint has changed: [change]. Reconcile the effect on the design, contracts, active assignments, tests, data, deployment work, and accepted results. Preserve useful work. Revise or supersede affected assignments explicitly and prevent stale writes through supported ownership controls. Continue work that remains valid. Present a material commitment for my decision only if it exceeds existing authority.

For an idea that should remain outside current scope:

> Record [idea], its motivation, links to evidence, and the question needed to evaluate it. Identify whether it is a later enhancement, competing route, or separate project. Keep the current objective active unless evidence invalidates it.

Research progress can be a rejected hypothesis or resolved uncertainty. Repeating the same failed attempt across new workers is not fresh progress. Keep attempts and budgets attached to the task so replacement and parallelism do not silently reset them.

Research/evaluation results must identify actual applied model/reasoning, policy/reservation references, usage evidence and uncertainty. New models/providers/data scope or higher limits require approval unless already explicitly covered; an approved fallback still has to fit its own reasoning bounds and every applicable remaining budget.

## 9. Assign deployment coordination and execution explicitly

Use [DEPLOYMENT_BUILD_INSTRUCTIONS.md](../protocol/DEPLOYMENT_BUILD_INSTRUCTIONS.md) early enough for release requirements to influence architecture. The main coordinator assigns deployment work and manages project dependencies. For multiple deployment assignments, a deployment coordinator manages their contracts and handoffs while execution workers own all investigation, implementation, commands, and job monitoring. For one bounded assignment, the main coordinator may assign a deployment executor directly; that executor performs its task without taking on worker coordination.

Two destinations may need work: distribution and activation of the Copilot working setup, and deployment of the software itself. Keep their targets and authority explicit. An independent supervisor belongs in the deployment scope only if the project actually requires one.

Deployment coordinators, executors, and external research/evaluation calls inherit the approved run gate. If starting independently without bootstrap records, complete the interview before discovery workers or direct external calls. Preparation authority is not a model/data-consent or budget exception. Reserve against the same parent/run ledger, not a new deployment allowance.

Use this launch prompt for a deployment coordinator:

> You are the deployment coordinator for [task ID/version], reporting to [parent] within [tasks/scope/resources/budget]. Retain coordinator role across all messages/answers/events and continuation; before tools/skills apply section 2 role/action admission. Use compact coordination state, not source or domain investigation, and route changes to existing owners first. No quick edits, execution skills or jobs; delegate discovery, implementation, review and operation observation to actual executors. Use the relevant `DEPLOYMENT_BUILD_INSTRUCTIONS.md` contracts and inherited run_policy_ref, effective_config, consent, authority and budget_reservation; tighten but never widen parent limits or create a competing ledger. Escalate genuinely missing decisions to the root/user without restarting approved interviews. Reserve before eligible dispatch through verified nonblocking controls or an approved independent-worker handoff. Return concise candidate-specific evidence/handles without blocking the parent on the whole job. Preserve ownership/effects on uncertain delivery or drift; do not duplicate/cancel blindly. Distinguish prepared, exercised, deployed and unverified outcomes. Target and deployment authority: [details, or unknown].

For one bounded deployment assignment, use this separate executor prompt:

> You are the deployment executor for [task ID and assignment version], reporting to [assigned coordinator]. Apply the relevant attached `DEPLOYMENT_BUILD_INSTRUCTIONS.md` requirements to the supplied bounded task packet. Verify run_policy_ref, actual effective_config and model/reasoning evidence, external consent and budget_reservation before effects, alongside workspace, ownership, target, authority, dependencies, budget, and acceptance criteria. Research/evaluation calls have the same gate; use no silent defaults/fallbacks. Return actual applied settings, usage/units/source/time, held uncertainty and remaining-ledger references with results. Execute this assignment, own its long operations and actual job handles, preserve checkpoints, and return evidence and unresolved effects. You are not coordinating other workers. If completing the assignment requires multiple workers, return a proposed decomposition to the coordinator for dispatch; do not combine worker coordination with long execution.

Expect actual commands or UI steps, prerequisites, target checks, promotion and recovery procedures, evidence locations, and unresolved items. A pipeline file alone does not establish a working release path.

Prepare the concrete candidate and release procedure before seeking any genuinely missing release authority. Existing authority persists across session handoffs. Permission to build release tooling does not automatically authorize a live deployment.

After an interrupted release, give the assigned deployment recovery executor:

> Reconcile the last release attempt with the platform, operation records and authoritative run ledger before retrying. Identify actual changes, current health, applied settings, usage, reservations, pending effects, and remaining uncertainty. Preserve same-run approval and held unknown charges; reserve any additional retry allowance before new affected effects. Resume or recover through the established runbook within existing authority. Keep the main coordinator informed through concise evidence and continue independent authorized work.

## 10. Maintain the workflow using observed results

After a material workflow change, new Copilot surface, relevant runtime upgrade, or failed recovery, recheck relevant model/reasoning and billing evidence and delegate a focused activation or recovery rehearsal within approved settings and reservations. Avoid rerunning unrelated setup checks for every small code change.

Use this improvement prompt:

> Coordinate a bounded review of whether orchestration is improving delivery. Route substantive inspection to the existing responsible worker or an eligible approved review assignment. Use its concise report on actual task/job/result evidence to identify idle time, queue growth, duplicate execution, stale instructions, role drift, integration congestion and weak recovery. Distinguish unknowns from observations. Delegate evidence-backed implementation and representative verification to owned workers; preserve live state and authority. Do not perform source investigation or edits in the coordinator.

Keep the current index compact and historical evidence discoverable. Store logs and large outputs outside the coordinator's working context. Use the project's normal access controls and keep secrets out of session memory files.

For a different project, reuse verified general procedures but establish that project's objective, constraints, authority, capabilities, and task state. Do not import unrelated project-specific assumptions or task owners. Reconcile any resources or operations actually shared with another project before conflicting work; a project boundary does not release their ownership or erase charges.

For a new run in the same project, reconcile earlier settings and explicitly reconfirm the run interview while retaining the authoritative project task state, active owners and assignments, operation handles, resource exclusions, accepted evidence, and outstanding budget reservations and charges. A new run ID or approval does not stop an old worker or make its resources available. Adopt valid assignments or change ownership only through the existing validity and safe-handover rules; preserve their prior authority and accounting records rather than silently extending consent to the new run. Block conflicting dispatch until the relevant ownership and effects are reconciled, but allow unrelated ready work once its own configuration, authority, dependencies, resources, and budget are satisfied.

Success is observable: the coordinator stays available, useful ready work reaches workers, execution and effects remain traceable, completed outputs reach integration, and a fresh authorized session can resume without duplicating work or rebuilding the entire history.
