# Your guide to running projects with GitHub Copilot

**Revision 2.1.2 · 6 September 2026**

This pack uses **GHCP** to mean **GitHub Copilot**. It supports projects in which research, implementation, and architecture evolve together. Apply it to the actual repository and installed Copilot environment; it does not assume your stack, deployment destination, or session controls.

The main orchestrator coordinates the project. Execution belongs to assigned worker sessions. Useful independent work should run in parallel as soon as the approved run configuration, dependencies, resources, reserved budget and available capacity permit.

| File | Who uses it | Result it should produce |
| --- | --- | --- |
| [FIRST_SESSION_AND_ORCHESTRATION.md](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md) | The bootstrap coordinator and subsequent project orchestrators | Project-specific instructions, approved run settings and budgets, assignment and recovery mechanisms, durable state, and demonstrated capability limits. |
| [OPERATOR_GUIDE.md](OPERATOR_GUIDE.md) | You | Prompts and practical steps for starting, directing, inspecting, recovering, and handing over work. |
| [DEPLOYMENT_BUILD_INSTRUCTIONS.md](../protocol/DEPLOYMENT_BUILD_INSTRUCTIONS.md) | An assigned deployment coordinator and execution workers, or one bounded deployment executor | The actual build and release implementation, verification evidence, and operational runbook, reported to the main coordinator. |

These documents provide operating instructions. They do not install a running supervisor or prove that an IDE or provider can dispatch, resume, or recover sessions.

For the coordinator's opening interaction, supply only [BOOTSTRAP.md](../protocol/BOOTSTRAP.md) and the compact project brief/state. This operator guide is for the operator and scoped follow-up reading, not another large mandatory opening attachment. Keep the full references accessible without automatically loading all of them.

Revision 2.0 remains the historical public baseline at commit `38e9ce28964d8038333a2034a6ff02087b4652f9`. Its checks and archive statements are not 2.1 guarantees; see [release notes and provenance](../reference/REVIEW_AND_CHANGES.md). The [run-configuration guide](../protocol/RUN_CONFIGURATION.md) supplies a questionnaire, compact examples and reference, not generated live settings.

## 1. Start a new project or upgrade an existing one

Open the intended repository. Provide the current outcome, known constraints, existing authority, and any other active work. Leave unknown facts unknown. **Before launching any orchestrated worker, including discovery/research, or making any direct external LLM API call, complete the configuration interview and explicitly approve the recorded run.** The current coordinating chat may do safe local planning and bounded capability reads to ask the questions; it is not retroactively blocked. After approval and budget reservation, the bootstrap coordinator delegates repository discovery and setup implementation to workers and uses their evidence to configure coordination.

The first response should acknowledge supplied intent/run mode and ask one next unresolved question, then end. Do not wait for a repository scan, complete model catalog, setup generation, or recovery drill. Before approval, each follow-up resolves one question using supplied evidence or one named known-short local lookup. If evidence is unavailable, report the exact missing item, owner and next action and return; do not loop or silently choose a default. Valid continuation records avoid re-asking settled questions.

When input or external progress is needed, end with **phase, last completed action, waiting on/owner, next action or actual trigger**. Returning control does not declare the project complete or stop surviving workers. After approval, keep unrelated eligible work moving before yielding. These are conversational instructions, not guarantees that a host will deliver queued input or preempt a stuck call.

For a new project, use:

> Start with `BOOTSTRAP.md` for this new project; keep `FIRST_SESSION_AND_ORCHESTRATION.md` available by section instead of preloading the full pack. Act as the main coordinator. Your first response acknowledges supplied intent, asks one next unresolved question, and ends before further investigation. Conduct the mandatory interview one decision per response: allowed providers/families and exact supported model IDs, defaults and role overrides, approved fallbacks, each model's minimum/default/maximum reasoning or accepted fixed N/A, direct external LLM consent even if disabled, aggregate cap/units and allocations, concurrency/retries/replacements and stop/escalation rules. Use supplied evidence or one known-short targeted local lookup for that question; return with a precise gap if unresolved. Obtain final explicit approval before workers or direct external calls. Persist approval/settings in existing POLICY, evidence in CAPABILITIES, and active run/approval/ledger pointers in PROJECT_STATE. Then reserve budget and delegate substantive discovery, implementation and verification under those settings. Check actual launch and model/reasoning controls; unsupported controls block autonomous claims, with exact evidenced manual configuration where possible. Demonstrate the relevant handoff/recovery path within approved scope, without making every future drill a first-task barrier. Keep useful independent work moving and end the response when only waits remain. My outcome is: [outcome]. My known constraints and authority are: [details, or unknown].

For an existing project, use:

> Enter this project's upgrade through `BOOTSTRAP.md` and compact current state, not a full-pack opening load. First acknowledge supplied intent/run mode and ask one unresolved question, or identify the next bounded action when same-run approval/state are complete; then return control. Inventory the live objective, decisions, assignments/owners, workspaces, unfinished changes, running effects, pending steering, attempts, approvals, usage, reservations and evidence through the bounded preapproval path. A new run reconciles and explicitly reconfirms settings before workers or direct external calls; continuation retains valid authority and obtains missing approvals before the next affected dispatch. Return on input/evidence holds, without chained scans or polling. Do not orphan or automatically kill workers, reset consumption, or free unknown charges. After approval reserve budget and delegate migration edits. Replace conflicting active rules, including discovery before approval, silent model/reasoning/budget defaults, main-coordinator execution, arbitrary worker counts and wait-for-everyone barriers. Reuse POLICY/CAPABILITIES/PROJECT_STATE and the authoritative ledger. Preserve history and use safe handover before changing owners. Demonstrate the affected behavior within approved scope, report limitations, and let unrelated eligible work proceed.

### The bootstrap questionnaire

Use the [complete reference and compact examples](../protocol/RUN_CONFIGURATION.md). These are exact short prompts to ask **before discovery dispatch**, one at a time where supported:

1. **“Is this a new run, or continuation of which approved run ID and policy version?”** Reconcile earlier records first. A new run requires explicit reconfirmation; a new session continuing the same run does not require asking again at every tool call.
2. **“Which providers, model families, and exact supported model IDs are allowed?”** Record the explicit default, coordinator/execution/review/integration/deployment overrides as applicable, and approved fallback IDs. Family names alone are insufficient; no hardcoded versions or silent host defaults.
3. **“For each allowed model, what minimum, maximum, and default reasoning do you approve?”** Verify that provider/model's supported categorical order before checking `minimum <= default/effective <= maximum`. Fixed/unsupported reasoning must be explicitly `N/A / not configurable` and accepted by the operator. Do not invent scales or map labels across models.
4. **“Are direct external LLM calls disabled, or what exact scope do you approve?”** Ask even if disabled. Copilot-managed requests are separate. Direct endpoints default **DENIED** until provider/endpoint, exact model, purpose, permissible data categories, secure credential reference (never the key), and budget are approved. Unknown consent blocks affected calls, not safe local planning.
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

The coordinator may inspect a concise result and record acceptance. That does not make it the owner of merge commands, detailed review, test runs, or deployment execution. This boundary applies to every session coordinating other workers, including a deployment coordinator. Calling that session an executor or execution lead does not permit it to run long jobs while retaining coordination responsibilities.

Use this correction if a coordinator starts doing execution work:

> Keep the main coordinator on coordination. Preserve any operation you already started, including its actual handle and uncertain effects; do not launch a duplicate. Prepare a safe transfer to a worker if the environment supports it. Assign further investigation, implementation, verification, integration, and job monitoring to real worker sessions. Continue coordinating independent work. If asynchronous dispatch is unavailable, provide the manual launch packet and the exact session action needed.

A worker may run a background operation when its environment supports it and the task permits it. The worker remains accountable for the handle, logs, observation, result retrieval, and effects. A detached process with no recoverable handle or owner is not a successful handoff.

Do not expect an idle or stopped coordinator to wake itself because a Markdown file tells it to. Recovery requires another active actor or a separately running supervisor whose observation and dispatch controls have been verified. If unattended supervision is required, assign its scoped design and implementation; do not claim it exists before it has been exercised.

## 4. Favor useful parallelism during ordinary work

Give an outcome, then let dependencies and capacity determine the assignments. A ready task should not wait for an unrelated task to finish merely because both were part of the same batch.

For normal continuation of an approved run, use:

> Continue toward [outcome] under the current project protocol and approved run_policy_ref. Reconcile actual work, pending steering, applied model/reasoning evidence, consent, usage and held reservations; preserve same-run authority without per-call asking. Reserve within the aggregate run and parent limits before dispatch. Identify the critical path, and dispatch independent ready tasks as approved supported capacity becomes available. Keep the main coordinator available for coordination. Use real workers for execution, including review and integration. Replenish ready work when a slot becomes available; do not wait for an entire batch. Respect shared resources, dependency contracts, authority, task budgets, and result-processing capacity. Report achieved evidence, active work, bottlenecks, and the next useful action.

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

Use this worker-session prompt with that packet:

> You are the execution worker for [task ID and assignment version], reporting to [coordinator or task registry]. Read the attached packet and applicable project instructions. Before effects verify run_policy_ref, actual effective_config and evidence, external consent scope or denial, and budget_reservation against the authoritative parent/run ledger. Use only approved exact models, per-model reasoning and fallbacks; do not silently select defaults, expand consent or reset limits. Verify your workspace, ownership, inputs, dependencies, write scope, authority, budget, acceptance criteria, and return channel. Inspect existing work and operations before acting. Execute this bounded assignment and preserve recoverable evidence. For long operations, record the actual returned job handle, execution location, log or artifact locations, observation method, progress signals, and recovery actions. Report dispatch acknowledgement separately from execution; report running only when evidence establishes that execution actually began. Distinguish heartbeat from useful progress. Return evidence and unresolved effects, then follow the submission boundary; do not independently expand scope or integrate shared changes.

The coordinator should supply these fields, using the project's existing schema where available:

| Packet content | Why you need it |
| --- | --- |
| Stable task ID, assignment version, execution owner, coordinator identity | Prevents duplicate and stale ownership. |
| Objective, acceptance evidence, relevant decisions and contracts | Gives the worker an independently understandable result. |
| Dependencies, workspace, branch or worktree, permitted writes and reserved resources | Defines readiness and isolation. |
| Granted authority and its source; remaining task budget and attempts | Preserves limits across replacements. |
| `run_id`, `run_policy_ref`, operator/source/time approval, `effective_config` and actual model/reasoning evidence, external consent | Binds the worker to approved exact settings and data scope; same-run handoffs retain authority. |
| `budget_reservation`, authoritative ledger/parent references, allocation units, usage/remaining and held unknown charges | Prevents oversubscription, invented conversions, and consumption resets across children/retries/replays. |
| Actual prior work, checkpoints, failed attempts, running jobs, uncertain effects | Prevents restarting completed or still-running work. |
| Result location, return path, checkpoint and observation triggers | Makes completion and interruption recoverable. |

For every long job, preserve a job record containing the task and assignment, worker owner, operation and target, actual execution identifier, start acknowledgement, logs or artifacts, last observed status and timestamp, latest progress evidence, expected progress signals, and verified cancellation or reconciliation method. If the job produces external effects, include the effect identifiers or idempotency mechanism where supported. Record missing fields as unknown; do not substitute an invented handle.

Each worker result and operation record must also reference `run_policy_ref`, actual applied `effective_config` and supporting evidence, `budget_reservation`, measured usage/units/source/time, unknown or estimated charges, and authoritative remaining balances. Requested settings alone do not establish applied settings. Reconcile billing and effects before releasing reservations.

Observe these distinctions:

| Status claim | What it establishes |
| --- | --- |
| Packet prepared | An assignment is ready to be launched. |
| Dispatch acknowledged | The runtime accepted the launch request; execution may still be queued. |
| Worker or job observed running | Runtime evidence identifies actual execution. |
| Heartbeat received | The observed component is responsive; useful progress is not yet established. |
| Progress observed | A milestone, useful finding, output, or state change advances the assignment. |
| Worker result submitted | The worker has delivered evidence for evaluation. |
| Review passed | The required evaluation accepts the submitted result within its scope. |
| Integration verified | The combined candidate passed the relevant checks. |
| User outcome complete | All required work and delivery effects for the requested outcome are evidenced. |

An exit code alone does not establish every acceptance criterion. A worker saying “done” does not establish review, integration, or deployment. Equally, an ended conversation does not establish that its background job ended.

## 6. Diagnose idle sessions and piled-up queues

An idle session is a symptom. Task dependencies, runtime scheduling, a tool job, provider limits, session failure, or lost context can produce similar visible behavior. Capture evidence before attributing the cause.

### Early bootstrap with little or no worker activity

**Do not send a recovery prompt to the affected session if it will join the same blocked queue.** Its inability to consume messages is the problem, not an invitation to enqueue more. Use the operator's host UI, an independent read-only observation/control API, or an already healthy authorized observer. If no such route is available, report that limitation; a message, automation tick or instruction file is not an out-of-band control.

| Observed signal | What to establish outside the blocked message path |
| --- | --- |
| No first response and no tool shown | Request accepted/delivered state, supplied context size, selected model/reasoning and run mode, provider/host observations. Do not assume no activity or blame worker count. |
| An active tool invocation | Actual tool/request handle, start/last observation, expected bounded output and surviving process/job. One stuck tool can hold a turn without any worker load. |
| Phase says awaiting input/evidence | The unresolved field, operator/evidence owner, delivery evidence and whether a question tool is suspending the active request. A visible question is not proof the turn ended; use its actual answer/cancel control, not an ordinary message queued behind it. |
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

> You are the deployment coordinator for [task ID and assignment version], reporting to the main coordinator. Apply the attached `DEPLOYMENT_BUILD_INSTRUCTIONS.md` using the current architecture, protocol, task contracts, and authority. Before any discovery or execution worker dispatch, verify the approved run_policy_ref, exact effective_config and model/reasoning evidence, external consent, and budget_reservation. Obtain missing approval through the interview using safe local planning only; do not launch workers first. Inherit/tighten parent limits and reserve before parallel dispatch. Coordinate through short bounded state reads and updates, dispatch, and status checks. Assign discovery, build and release implementation, infrastructure changes, verification, integration, and recovery execution to workers. Dispatch independent ready work where verified capacity permits. Each executor owns its actual job handles, logs, progress, and effects. Delegate rehearsal in an authorized isolated environment and evaluate its evidence. Do not run long tooling, heavy investigation, or background jobs yourself. Use verified nonblocking dispatch or prepare manual worker-session packets. Distinguish prepared files, exercised automation, deployed resources, and unverified steps. My target and deployment authority are: [details, or not yet decided].

For one bounded deployment assignment, use this separate executor prompt:

> You are the deployment executor for [task ID and assignment version], reporting to [assigned coordinator]. Apply the relevant attached `DEPLOYMENT_BUILD_INSTRUCTIONS.md` requirements to the supplied bounded task packet. Verify run_policy_ref, actual effective_config and model/reasoning evidence, external consent and budget_reservation before effects, alongside workspace, ownership, target, authority, dependencies, budget, and acceptance criteria. Research/evaluation calls have the same gate; use no silent defaults/fallbacks. Return actual applied settings, usage/units/source/time, held uncertainty and remaining-ledger references with results. Execute this assignment, own its long operations and actual job handles, preserve checkpoints, and return evidence and unresolved effects. You are not coordinating other workers. If completing the assignment requires multiple workers, return a proposed decomposition to the coordinator for dispatch; do not combine worker coordination with long execution.

Expect actual commands or UI steps, prerequisites, target checks, promotion and recovery procedures, evidence locations, and unresolved items. A pipeline file alone does not establish a working release path.

Prepare the concrete candidate and release procedure before seeking any genuinely missing release authority. Existing authority persists across session handoffs. Permission to build release tooling does not automatically authorize a live deployment.

After an interrupted release, give the assigned deployment recovery executor:

> Reconcile the last release attempt with the platform, operation records and authoritative run ledger before retrying. Identify actual changes, current health, applied settings, usage, reservations, pending effects, and remaining uncertainty. Preserve same-run approval and held unknown charges; reserve any additional retry allowance before new affected effects. Resume or recover through the established runbook within existing authority. Keep the main coordinator informed through concise evidence and continue independent authorized work.

## 10. Maintain the workflow using observed results

After a material workflow change, new Copilot surface, relevant runtime upgrade, or failed recovery, recheck relevant model/reasoning and billing evidence and delegate a focused activation or recovery rehearsal within approved settings and reservations. Avoid rerunning unrelated setup checks for every small code change.

Use this improvement prompt:

> Review whether orchestration is improving delivery. Use actual assignment, job, and result records to identify avoidable idle time, undispatched ready work, queue growth, duplicate execution, stale instructions, repeated failed attempts, main-coordinator execution, integration congestion, and weak recovery. Distinguish missing observations from measured behavior. Implement small corrections tied to the evidence, preserve live project state and authority, and verify the changed mechanism with representative work.

Keep the current index compact and historical evidence discoverable. Store logs and large outputs outside the coordinator's working context. Use the project's normal access controls and keep secrets out of session memory files.

For a different project, reuse verified general procedures but establish that project's objective, constraints, authority, capabilities, and task state. Do not import unrelated project-specific assumptions or task owners. Reconcile any resources or operations actually shared with another project before conflicting work; a project boundary does not release their ownership or erase charges.

For a new run in the same project, reconcile earlier settings and explicitly reconfirm the run interview while retaining the authoritative project task state, active owners and assignments, operation handles, resource exclusions, accepted evidence, and outstanding budget reservations and charges. A new run ID or approval does not stop an old worker or make its resources available. Adopt valid assignments or change ownership only through the existing validity and safe-handover rules; preserve their prior authority and accounting records rather than silently extending consent to the new run. Block conflicting dispatch until the relevant ownership and effects are reconciled, but allow unrelated ready work once its own configuration, authority, dependencies, resources, and budget are satisfied.

Success is observable: the coordinator stays available, useful ready work reaches workers, execution and effects remain traceable, completed outputs reach integration, and a fresh authorized session can resume without duplicating work or rebuilding the entire history.
