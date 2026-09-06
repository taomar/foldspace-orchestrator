# Orchestration review and revision guide

**Revision:** 2.0 — 6 September 2026  
**Reviewed:** all three Markdown documents in the uploaded archive.  
**Scope:** a coordinated revision of the instructions, including the requested stronger parallelism, coordinator-only main sessions, and recovery from unexplained idling through queue preservation, agent-connection restart, and reconciliation before replay.

The original pack already covers evidence, durable checkpoints, stale assignments, architecture changes, permissions, and interrupted deployments. Its main weakness is that some desired behavior remains optional or loosely specified. In particular, it explicitly allows the orchestrator to execute work directly and starts concurrency at two workers. Those defaults conflict with the requested operating model.

The reported stalls have not been reproduced. The attachment contains instructions, not the installed Copilot configuration, runtime logs, task registry, or running-job records. The findings below establish weaknesses in the instructions; they do not establish which weakness or runtime failure caused a particular incident.

## 1. Findings and changes

Original section references below refer to the uploaded version.

| Priority | Finding in the original pack | How progress can slip | Revision |
| --- | --- | --- | --- |
| High | Main instructions §6 permit direct execution and combined roles; §8 offers sequential execution when delegation is unavailable. | The coordinator can become the long-running executor and stop attending to scheduling or steering. | Keep the main session on coordination. Execution belongs to worker sessions, including builds, tests, investigation, integration commands, deployment and background jobs. Prepare an explicit worker launch packet when native dispatch is unavailable. |
| High | Delegation capability is checked, but continued coordinator responsiveness is not an explicit gate. | A long delegated call can still occupy the coordinator if the runtime waits for its completion. | Verify nonblocking launch, independent status, and coordinator responsiveness for long jobs. A worker role name alone does not establish these capabilities. |
| High | Main instructions §11 begin with at most two concurrent workers. | Independent work can remain idle despite available capacity. | Remove the default two-worker cap. Choose concurrency from eligible work, verified runtime capacity, resource availability, integration demand, and existing task limits. |
| High | Main instructions §6 describe a cycle without an explicit obligation to refill capacity when individual results become available. | A slow worker can become an accidental barrier for unrelated work. | Reevaluate readiness on observed completions, dependency changes, steering, failures, and capacity changes. Release eligible dependents without waiting for unrelated workers. |
| High | No dedicated distinction between task backlog, queued chat messages, and execution jobs. | A queued prompt may be mistaken for dispatched work, or repeated prompting may produce duplicates. | Keep durable task intent separate from message delivery and actual execution. Track dispatch acknowledgement and job identity; reconcile uncertain starts before resubmission. |
| High | Main instructions §13 address recovery well, but queue congestion, connection restart, lost launch acknowledgement, and replay are not explicit operational cases. | Restarting can lose pending intent or duplicate a job that is still active. | Preserve original queued instructions, reconnect the affected agent through verified controls, reconcile delivery and actual execution, and replay only valid unapplied intent. Adopt valid surviving workers after coordinator takeover. |
| High | Main instructions §4 and §8 concentrate state management and integration in the orchestrator. | Implementers can produce results faster than one busy coordinator can investigate, validate, and integrate them. | Delegate review and integration execution. Keep exclusive ownership at each actual shared write boundary; allow preparation and independent validation to overlap. |
| Medium | Requirements, authority, and decisions appear throughout the records without a compact requirement-to-result contract. | A later correction or constraint can disappear during handoff or a change of direction. | Preserve requirement and steering identities, link assignments and acceptance evidence, and invalidate affected work explicitly. Keep independent work moving. |
| Medium | Main instructions §5 require loading the protocol but do not constrain how much generated operational guidance becomes always-on context. | Growing instructions can crowd out the current objective and evidence. | Generate a compact runtime core and load detailed procedures by task and event. These full documents remain bootstrap and operating references. |
| Medium | Assignment and result checks are largely expressed in prose. | Stale or incomplete output can pass if a session forgets a check. | Specify observable dispatch, submission, acceptance, and release checks; use verified native controls or small worker-built guards where justified. Label unenforced rules honestly. |
| Medium | Deployment instructions cover phases thoroughly but do not make concurrent preparation an explicit scheduling requirement. | Packaging, configuration, migration preparation, health checks, and runbook work can be serialized unnecessarily. | Split preparation by dependency and ownership; serialize conflicting application to a shared destination or data boundary. Bind results to the actual candidate. |

## 2. Intended operating model

| Participant | Owns | Required boundary |
| --- | --- | --- |
| Main orchestrator | Objective, current constraints, readiness, dispatch, priorities, ownership, evidence assessment, status and handover. | Short bounded coordination operations. No long execution, heavy investigation, build/test commands, deployment applies, or background jobs. |
| Execution worker | A bounded research or implementation assignment and the actual operations it starts. | Accessible artifacts, current assignment, actual process/provider identifiers, progress evidence and recovery method. |
| Review or integration worker | Candidate inspection, applicable checks, conflict resolution and authorized integration execution. | Validate the submitted candidate; coordinate writes to each shared branch or target. |
| Separate observer or supervisor, if adopted | Observe coordination liveness and initiate supported recovery. | Must actually run independently and use supported controls. It must not become a competing dispatcher. |

Long work needs both delegation and a verified way for coordination to continue. If a runtime cannot provide that, use independently opened worker sessions and the exact prepared handoff. This limitation does not permit the main coordinator to take over execution.

Concurrency should serve the dependency path to a verified result. Idle capacity is justified when no eligible work exists, a real shared limit binds, or the extra work would increase delay. It is not justified merely because another unrelated worker has not finished. When review accumulates, shift capacity to review and integration and throttle the contributing workstream; do not freeze independent work by default.

## 3. Queue and restart behavior

The revised guide distinguishes intent waiting in a durable backlog, a message waiting for delivery, a dispatch with uncertain acknowledgement, a running operation, and a result waiting for acceptance. Each needs a different action.

A useful diagnostic is: **Which task is waiting, what is it waiting for, which actor can release it, and what evidence was last observed?** A heartbeat demonstrates liveness. It does not demonstrate useful progress. A lack of new artifacts does not prove a legitimate long operation is dead.

Repeatedly adding the same prompt is not a recovery procedure. Capture unsent intent, stop duplicate dispatch, inspect existing handles and effects, and transfer ownership before allowing a replacement to issue conflicting work. When a job's outcome is unknown, monitoring and reconciliation precede replay.

The requested connection-recovery path is now explicit:

1. Preserve the original queued instructions and their IDs, causal order, target and known delivery state, alongside current task, candidate and job records. Reconcile captured cancellations and changed constraints before treating other work as unaffected or issuing new effects.
2. Isolate the affected connection and any tasks or resources affected by those controls, including work on other connections. Have an independent recovery owner use the verified reconnect or connection-restart control. Do not equate connection restart with cancellation of execution.
3. Establish the current connection generation and coordination ownership; inspect surviving jobs and results before redispatch.
4. Reconcile what was delivered, applied, superseded, started or completed. Apply newer cancellations and changed constraints to pending work before replaying an obsolete action.
5. Restore valid unapplied instructions in bounded chunks with acknowledgement and progress checks. Release newly eligible tasks in parallel. Reconcile an uncertain delivery rather than blindly sending it again.

Full automation requires actual access to pending input before it is lost, supported reconnect controls, and an independent recovery actor. If unsent UI text is inaccessible, the setup must provide the actual manual preservation and restore steps. It cannot reconstruct uncaptured messages or promise exactly-once execution merely by resending them. The main instructions specify the persistent journal and replay checks; the operator guide supplies the recovery prompt.

The operating guide includes the relevant distinctions from the [official Copilot chat queue documentation](https://code.visualstudio.com/docs/chat/chat-overview#send-messages-while-a-request-is-running). The revised capability check also distinguishes [persistent session orchestration](https://code.visualstudio.com/docs/agents/run/sessions/manage-sessions#orchestrate-sessions-from-agent-host-sessions) from [subagent invocation](https://code.visualstudio.com/docs/agents/run/subagents). These documentation references were checked on 6 September 2026; the actual installed environment still requires inspection.

An inactive coordinator cannot run its own monitoring loop. Unattended recovery requires another active session or a separately running, verified supervisor. A supported host or provider defect may still require runtime troubleshooting; the instruction revision cannot guarantee that restarting Copilot will never be necessary.

## 4. Apply the revision without resetting the project

1. Use the migration prompt in [OPERATOR_GUIDE.md](OPERATOR_GUIDE.md) in the existing project. Supply its current objective and these revised documents.
2. Have execution workers inspect and update the existing generated instructions and role configuration. Preserve task identities, current assignments, useful work, decisions, authority, failed-attempt history and job handles.
3. Remove conflicting generated rules: the default two-worker cap, main-session execution fallback, global wait-for-all behavior, and any assumption that queued chat equals dispatched work. Merge the new behavior into the authoritative locations; do not append a second competing protocol.
4. Reconcile live workers before switching coordination ownership. Adopt unaffected assignments explicitly; change only assignments invalidated by scope, ownership, contracts or evidence.
5. Exercise the relevant activation scenarios in the main and deployment instructions using harmless representative work. Keep productive independent work moving while workers establish additional capabilities.
6. Record whether each control is documented, configured, exercised, or verified in the intended runtime. Continue within existing authority, observing actual runtime permission requirements.

For a new project, use the first-session prompt in the operator guide. Do not load this review into every worker session; it explains the changes and is not a fourth runtime protocol.

## 5. Verification and limits

The deliverables are revised instructions. They do not include an installed Copilot configuration, running supervisor, deployed scheduler, or measured performance improvement in the user's environment.

Activation must demonstrate the practical outcomes: the coordinator remains responsive while a worker runs a long job; independent ready work starts without a global barrier; queue congestion receives a specific diagnosis; a lost launch acknowledgement does not cause duplicate execution; a backed-up queue can be restored after connection restart without blindly repeating applied work; stale results are rejected; and a replacement recovers actual work without resetting the budget or current requirements. Replay and deduplication results apply only to the actual adapter and scenarios exercised.

Evaluate improvement through elapsed time to accepted, integrated outcomes, time ready work waits, coordinator responsiveness, review backlog age, repeated failure signatures, and recovery incidents. Compare similar work where evidence permits. More active sessions alone is not evidence of faster delivery.

## 6. Files

| File | Use |
| --- | --- |
| [FIRST_SESSION_AND_ORCHESTRATION.md](FIRST_SESSION_AND_ORCHESTRATION.md) | Build or update the project-specific orchestration layer and its verified controls. |
| [OPERATOR_GUIDE.md](OPERATOR_GUIDE.md) | Start, steer, inspect, migrate and recover the working setup. |
| [DEPLOYMENT_BUILD_INSTRUCTIONS.md](DEPLOYMENT_BUILD_INSTRUCTIONS.md) | Delegate and implement the actual build, release and recovery path with parallel preparation. |
| [REVIEW_AND_CHANGES.md](REVIEW_AND_CHANGES.md) | Findings, rationale, migration overview and validation boundaries. |

### Local artifact verification

All four Markdown deliverables were checked for existence, UTF-8 readability, balanced fenced code blocks, resolving relative Markdown file links, revision 2.0 identification, and the presence of the three required core filenames. The superseded exact defaults “Begin with at most two concurrent workers” and “execute directly or delegate” are absent. The final ZIP was checked for CRC integrity, exactly these four files at its root, and byte-for-byte equality with the final Markdown files. No GitHub Copilot runtime, agent connection, queue replay, or deployment execution was tested; no runnable user environment was supplied.
