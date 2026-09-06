# Your guide to running projects with GitHub Copilot

**Revision 2.0 · 6 September 2026**

This pack uses **GHCP** to mean **GitHub Copilot**. It supports projects in which research, implementation, and architecture evolve together. Apply it to the actual repository and installed Copilot environment; it does not assume your stack, deployment destination, or session controls.

The main orchestrator coordinates the project. Execution belongs to assigned worker sessions. Useful independent work should run in parallel as soon as its dependencies, resources, and available capacity permit.

| File | Who uses it | Result it should produce |
| --- | --- | --- |
| `FIRST_SESSION_AND_ORCHESTRATION.md` | The bootstrap coordinator and subsequent project orchestrators | Project-specific instructions, assignment and recovery mechanisms, durable state, and demonstrated capability limits. |
| `OPERATOR_GUIDE.md` | You | Prompts and practical steps for starting, directing, inspecting, recovering, and handing over work. |
| `DEPLOYMENT_BUILD_INSTRUCTIONS.md` | An assigned deployment coordinator and execution workers, or one bounded deployment executor | The actual build and release implementation, verification evidence, and operational runbook, reported to the main coordinator. |

These documents provide operating instructions. They do not install a running supervisor or prove that an IDE or provider can dispatch, resume, or recover sessions.

## 1. Start a new project or upgrade an existing one

Open the intended repository. Provide the current outcome, known constraints, existing authority, and any other active work. Leave unknown facts unknown. The bootstrap coordinator should delegate repository discovery and setup implementation to workers, then use their evidence to configure coordination.

For a new project, use:

> Apply revision 2.0 of `FIRST_SESSION_AND_ORCHESTRATION.md` to this project. Act as the main coordinator: use short bounded coordination reads and updates, dispatch, and status checks; delegate repository investigation, instruction implementation, research, coding, verification, and long operations to execution workers. Check the actual session capabilities before selecting a dispatch mechanism. Establish durable project state and demonstrate a worker assignment, a result handoff, and safe recovery. Proactively dispatch the useful ready work that capacity supports; do not start from an arbitrary worker count. If independent asynchronous execution is unavailable, prepare the exact packet for a manually opened worker session and identify the missing action. My outcome is: [outcome]. My known constraints and authority are: [details, or unknown].

For an existing project, use:

> Upgrade this project's orchestration to revision 2.0 using the attached instructions. Preserve the live project: reconcile its current objective, decisions, task IDs, assignment versions, active owners, branches and worktrees, incomplete changes, running operations, pending steering, attempt history, budgets, authority, and accepted evidence. Delegate inspection and migration edits to workers. Identify and replace conflicting active rules, including any initial two-worker cap, main-coordinator execution fallback, or wait-for-everyone barrier. Adapt the existing authoritative records instead of creating a competing tracker or resetting tasks. Apply new assignments prospectively; safely hand over existing execution before changing its owner. Demonstrate the changed behavior on bounded authorized work, then report what is verified and what remains unavailable.

An upgrade should produce a targeted migration, with obsolete active instructions corrected or clearly superseded. Keeping an old rule in an active entrypoint can undo the new behavior even when the replacement document is sound. Retain historical decisions as history, without presenting them as current instructions.

Do not declare a live worker abandoned because the new protocol uses different labels. Inspect its task and effects before transferring ownership. Give work that remains valid a route to completion.

## 2. Confirm activation in a fresh session

The setup should leave a short discoverable entrypoint, compact project state, task and operation records, and links to detailed evidence. The exact supported instruction and agent configuration depends on the installed environment. A configuration file existing on disk is not evidence that a new session loaded it. See [GitHub instruction support](https://docs.github.com/en/copilot/reference/custom-instructions-support) and [VS Code custom agents](https://code.visualstudio.com/docs/agent-customization/custom-agents).

Have an assigned setup or verification worker exercise discovery and handoffs. Then start a fresh coordinator and use:

> Load this project's current session instructions and compact state. Identify your coordination role, instruction revision, objective, selected route, active assignments and owners, latest accepted evidence, pending user steering, existing authority, and next ready work. Cite the records you used. State which dispatch, observation, cancellation, and replacement controls were demonstrated in this environment. Identify conflicting or missing state. Keep implementation and long execution assigned to workers.

Check that its answer matches the real project. If instructions exist only on an isolated branch, make the accepted version available through the project's normal workflow to the sessions that need it. Delegate any activation repair to a worker.

A useful setup demonstration establishes that:

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

For normal continuation, use:

> Continue toward [outcome] under the current project protocol. Reconcile actual work and pending steering, identify the critical path, and dispatch independent ready tasks as supported capacity becomes available. Keep the main coordinator available for coordination. Use real workers for execution, including review and integration. Replenish ready work when a slot becomes available; do not wait for an entire batch. Respect shared resources, dependency contracts, authority, task budgets, and result-processing capacity. Report achieved evidence, active work, bottlenecks, and the next useful action.

Useful concurrency may include implementation of independent components, an experiment that resolves a design uncertainty, preparation of a deployment environment, and review of an already completed component. These can overlap when their actual dependencies allow it.

To increase parallelism, use:

> Examine where independent work is waiting unnecessarily. Show the ready tasks, dependency edges, writable scopes, shared-resource reservations, verified worker capacity, and review or integration backlog. Dispatch additional useful workers where these permit it. Split a blocking assignment only when the split has a clear contract and acceptance result. Give the concrete reason for every ready task that remains undispatched. Do not increase concurrency by creating duplicate assignments, speculative rewrites, or outputs that cannot be reviewed and integrated.

There is no universal starting count or guaranteed speedup. Choose concurrency from the current project and measured conditions. A real provider limit, shared test environment, unstable interface, or full integration queue can justify a local limit. Record that reason and revisit it when the condition changes.

Isolated files are only one part of independence. Workers may still collide through a schema, lockfile, shared database, port, test identity, deployment target, or external side effect. Assign one owner for shared writes or use a verified coordination mechanism. Let read-only investigation or other independent work continue while a specific write is serialized.

When completed outputs are accumulating, prioritize the review and integration workers that release useful capacity. Pause only the work feeding the bottleneck where necessary. Do not block unrelated progress with a project-wide barrier.

For a quick status view, use:

> Show the current outcome, critical path, ready work, active assignments and owners, blocked dependencies, pending review and integration, latest verified evidence, and next action. Separate measured status from unknown status. Explain whether current capacity is constrained by dependencies, worker/session limits, provider throttling, shared resources, or result processing, and cite the evidence for that conclusion.

These are ordinary prompts, not built-in slash commands. Any generated shortcut must be verified in your installed environment before you rely on it.

## 5. Launch workers with an explicit task and job handoff

Avoid giving the same writable task to multiple conversations. If you open a worker manually, have the coordinator register the assignment and prepare its complete packet first. A prepared packet is not a started task.

Use this worker-session prompt with that packet:

> You are the execution worker for [task ID and assignment version], reporting to [coordinator or task registry]. Read the attached packet and applicable project instructions. Verify your workspace, ownership, inputs, dependencies, write scope, authority, budget, acceptance criteria, and return channel. Inspect existing work and operations before acting. Execute this bounded assignment and preserve recoverable evidence. For long operations, record the actual returned job handle, execution location, log or artifact locations, observation method, progress signals, and recovery actions. Report dispatch acknowledgement separately from execution; report running only when evidence establishes that execution actually began. Distinguish heartbeat from useful progress. Return evidence and unresolved effects, then follow the submission boundary; do not independently expand scope or integrate shared changes.

The coordinator should supply these fields, using the project's existing schema where available:

| Packet content | Why you need it |
| --- | --- |
| Stable task ID, assignment version, execution owner, coordinator identity | Prevents duplicate and stale ownership. |
| Objective, acceptance evidence, relevant decisions and contracts | Gives the worker an independently understandable result. |
| Dependencies, workspace, branch or worktree, permitted writes and reserved resources | Defines readiness and isolation. |
| Granted authority and its source; remaining task budget and attempts | Preserves limits across replacements. |
| Actual prior work, checkpoints, failed attempts, running jobs, uncertain effects | Prevents restarting completed or still-running work. |
| Result location, return path, checkpoint and observation triggers | Makes completion and interruption recoverable. |

For every long job, preserve a job record containing the task and assignment, worker owner, operation and target, actual execution identifier, start acknowledgement, logs or artifacts, last observed status and timestamp, latest progress evidence, expected progress signals, and verified cancellation or reconciliation method. If the job produces external effects, include the effect identifiers or idempotency mechanism where supported. Record missing fields as unknown; do not substitute an invented handle.

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

VS Code's **Add to Queue** waits for the current response to complete; **Steer** applies after the current tool execution finishes; **Stop and Send** cancels the current request and immediately submits the message. A stalled tool could therefore delay queued or steering input—an inference from those semantics, not a diagnosis of your incident. Use the verified controls in your installed surface. Stopping a chat request does not establish whether its subprocess, provider job, or external effects stopped; an execution worker must reconcile the actual operation before a retry. [Sending messages during a request](https://code.visualstudio.com/docs/chat/chat-overview#send-messages-while-a-request-is-running).

Keep these queues separate:

| Queue or wait | What to inspect | Appropriate response |
| --- | --- | --- |
| Project task backlog | Readiness, dependency states, resource ownership, available capacity | Fix a task dependency or dispatch ready work. |
| Copilot chat/message queue | Pending prompts, dispatch acknowledgements, session state, unsent steering | Preserve intent and reconcile which messages were accepted before retrying. |
| Worker/session scheduling queue | Accepted dispatch IDs, running-session count, observed scheduling limits | Adjust dispatch to verified capacity; investigate a stalled accepted assignment. |
| Provider or tool-job queue | Actual job handle, target status, logs, rate-limit or provider errors | Have an execution or diagnostic worker observe that job through supported controls. |
| Review/integration backlog | Submitted results, assigned evaluators, integration-resource availability | Assign capacity to evaluate and integrate useful output. |

To ask why work is idle, use:

> Diagnose the idle state using current evidence. Distinguish project backlog, Copilot queued messages, worker dispatch, provider/tool jobs, and review or integration backlog. Show the oldest actionable items, owners, last observations, expected next event, and unknowns. For each idle or blocked assignment, state its evidenced reason or explicitly mark the reason unknown, name the actor or condition that can unblock it, and identify the next concrete action and its owner. State why each ready task lacks a worker. Keep this coordinator available; delegate log inspection and long diagnostics. Preserve pending steering and current execution before recovery. Continue independent work and propose the smallest corrective action supported by evidence.

If the affected coordinator cannot receive that prompt, use a separate diagnostic session with the project records. Make its initial role read-only diagnosis; it does not become a second coordinator or acquire existing task ownership by being opened.

To back up the queued inputs, reconnect, and restore them, use this prompt in a healthy recovery session:

> Recover the affected agent connection and preserve its queued inputs. Before reconnecting or restarting it, back up the original pending messages using supported queue capture, export, or visible manual capture; preserve message IDs where available, local recovery IDs where needed, causal order, task references, acknowledgements, pending corrections, and cancellations. Preserve active job handles and actual work separately. Before dispatching work or issuing new effects, reconcile captured cancellations and constraints with current authoritative intent and identify affected tasks and resources across all connections; hold new affected effects while their status is unresolved. Do not automatically cancel live stateful jobs; handle them through verified recovery controls. Use a verified scoped reconnect or restart mechanism from this independent recovery session; delegate long diagnostics and execution to workers if you are coordinating recovery. Establish the current connection and coordination owner, then reconcile which messages were sent, acknowledged, applied, superseded, or still unknown and which jobs are active or complete. Restore only remaining valid intents in causal order, honoring newer constraints and cancellations. Drain bounded chunks with acknowledgements and reconcile their application before retrying an uncertain item. Release independent ready tasks in parallel as their state permits. Do not blindly flush the queue, rerun completed jobs, invent uncaptured text, or enter a repeated restart loop. If a required control is unavailable, preserve the bundle and provide the exact manual steps supported by this installed surface.

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

For worker replacement:

> Recover [task ID/session] using its actual artifacts and latest job state. Preserve partial work, pending steering, attempts, and remaining limits. Check whether the previous worker or operation can still produce effects. Establish safe ownership transfer, then prepare or launch a fresh worker with a compact packet. Continue independent assignments. Identify anything that could not be recovered or verified.

For a responsive but overwhelmed coordinator:

> Prepare a coordinator handoff now using bounded coordination updates. Index the objective, current route, authority, pending steering, ready tasks, active owners, worker sessions, operation handles, submitted results, blocked dependencies, attempts, uncertain effects, and next actions. Delegate any detailed artifact inspection needed. Produce the replacement packet and the exact supported steps for establishing one active coordinator without duplicating execution.

For a coordinator that is already inaccessible:

> Recover coordination from the project records and actual runtime evidence. First inspect safely; do not assume prior sessions or jobs stopped. Reconcile assignment ownership, queued instructions, workspaces, results, and uncertain effects. Establish one active coordinator before dispatching conflicting work. Delegate execution to workers and resume independent ready tasks whose state and authority are known. Carry forward the existing task history and granted authority.

There are three distinct capabilities: correction within a functioning session, replacement through an active actor, and unattended recovery through a verified independent supervisor. Record which the project has demonstrated. Do not present a manual replacement packet as automatic recovery.

## 8. Explore alternatives and change direction

For an alternative approach:

> Assign a bounded investigation of [alternative or question]. Identify the current assumptions it challenges, the smallest experiment that distinguishes the options, its budget, stopping condition, and decision. Run independent experiments in parallel where useful and capacity permits. Preserve the current implementation and evidence. Compare findings against our actual constraints, distinguish observations from hypotheses, and recommend whether the route should change.

For an intentional pivot:

> The objective or constraint has changed: [change]. Reconcile the effect on the design, contracts, active assignments, tests, data, deployment work, and accepted results. Preserve useful work. Revise or supersede affected assignments explicitly and prevent stale writes through supported ownership controls. Continue work that remains valid. Present a material commitment for my decision only if it exceeds existing authority.

For an idea that should remain outside current scope:

> Record [idea], its motivation, links to evidence, and the question needed to evaluate it. Identify whether it is a later enhancement, competing route, or separate project. Keep the current objective active unless evidence invalidates it.

Research progress can be a rejected hypothesis or resolved uncertainty. Repeating the same failed attempt across new workers is not fresh progress. Keep attempts and budgets attached to the task so replacement and parallelism do not silently reset them.

## 9. Assign deployment coordination and execution explicitly

Use `DEPLOYMENT_BUILD_INSTRUCTIONS.md` early enough for release requirements to influence architecture. The main coordinator assigns deployment work and manages project dependencies. For multiple deployment assignments, a deployment coordinator manages their contracts and handoffs while execution workers own all investigation, implementation, commands, and job monitoring. For one bounded assignment, the main coordinator may assign a deployment executor directly; that executor performs its task without taking on worker coordination.

Two destinations may need work: distribution and activation of the Copilot working setup, and deployment of the software itself. Keep their targets and authority explicit. An independent supervisor belongs in the deployment scope only if the project actually requires one.

Use this launch prompt for a deployment coordinator:

> You are the deployment coordinator for [task ID and assignment version], reporting to the main coordinator. Apply `DEPLOYMENT_BUILD_INSTRUCTIONS.md` using the current architecture, protocol, task contracts, and authority. Coordinate through short bounded state reads and updates, dispatch, and status checks. Assign discovery, build and release implementation, infrastructure changes, verification, integration, and recovery execution to workers. Dispatch independent ready work where verified capacity permits. Each executor owns its actual job handles, logs, progress, and effects. Delegate rehearsal in an authorized isolated environment and evaluate its evidence. Do not run long tooling, heavy investigation, or background jobs yourself. Use verified nonblocking dispatch or prepare manual worker-session packets. Distinguish prepared files, exercised automation, deployed resources, and unverified steps. My target and deployment authority are: [details, or not yet decided].

For one bounded deployment assignment, use this separate executor prompt:

> You are the deployment executor for [task ID and assignment version], reporting to [assigned coordinator]. Apply the relevant `DEPLOYMENT_BUILD_INSTRUCTIONS.md` requirements to the supplied bounded task packet. Verify its workspace, ownership, target, authority, dependencies, budget, and acceptance criteria. Execute this assignment, own its long operations and actual job handles, preserve checkpoints, and return evidence and unresolved effects. You are not coordinating other workers. If completing the assignment requires multiple workers, return a proposed decomposition to the coordinator for dispatch; do not combine worker coordination with long execution.

Expect actual commands or UI steps, prerequisites, target checks, promotion and recovery procedures, evidence locations, and unresolved items. A pipeline file alone does not establish a working release path.

Prepare the concrete candidate and release procedure before seeking any genuinely missing release authority. Existing authority persists across session handoffs. Permission to build release tooling does not automatically authorize a live deployment.

After an interrupted release, give the assigned deployment recovery executor:

> Reconcile the last release attempt with the platform and operation records before retrying. Identify actual changes, current health, pending effects, and remaining uncertainty. Resume or recover through the established runbook within existing authority. Keep the main coordinator informed through concise evidence and continue independent authorized work.

## 10. Maintain the workflow using observed results

After a material workflow change, new Copilot surface, relevant runtime upgrade, or failed recovery, delegate a focused activation or recovery rehearsal. Avoid rerunning unrelated setup checks for every small code change.

Use this improvement prompt:

> Review whether orchestration is improving delivery. Use actual assignment, job, and result records to identify avoidable idle time, undispatched ready work, queue growth, duplicate execution, stale instructions, repeated failed attempts, main-coordinator execution, integration congestion, and weak recovery. Distinguish missing observations from measured behavior. Implement small corrections tied to the evidence, preserve live project state and authority, and verify the changed mechanism with representative work.

Keep the current index compact and historical evidence discoverable. Store logs and large outputs outside the coordinator's working context. Use the project's normal access controls and keep secrets out of session memory files.

For a different project, reuse verified general procedures but establish its own objective, constraints, authority, capabilities, and task state. Do not carry over active task owners or project-specific assumptions.

Success is observable: the coordinator stays available, useful ready work reaches workers, execution and effects remain traceable, completed outputs reach integration, and a fresh authorized session can resume without duplicating work or rebuilding the entire history.
