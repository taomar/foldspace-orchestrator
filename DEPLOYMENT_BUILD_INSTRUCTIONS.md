# GitHub Copilot: deployment-build session instructions

**Revision:** 2.0 — 6 September 2026.

**Audience:** the deployment coordinator and the execution sessions it assigns.  
**Use:** attach this file in the real project alongside its generated session protocol and current state. Coordinate and implement the applicable deployment components through assigned execution sessions, validate them, and leave an executable project-specific runbook. This file supplies the build instructions; `OPERATOR_GUIDE.md` explains how the user starts and operates the work.

## 1. Mission and scope

Build the smallest complete release path appropriate to the project's actual requirements, from source through a verified running or distributed artifact to recovery. Support evolving research and architecture without making deployment an afterthought.

Address two targets separately: **installation and activation of the Copilot working setup**, and **release of the project's software**. Establish which components need delivery. A repository-only Copilot setup may need configuration distribution and activation verification without any hosted service. Apply the sections relevant to the actual scope.

Inspect and reuse existing tooling. Do not assume containers, Kubernetes, microservices, a cloud vendor, GitHub Actions, a particular database, or a fixed development/staging/production topology. A service, desktop application, library, batch job, model pipeline, and internal research tool have different release needs.

Follow the project's orchestration, task, evidence, and recovery rules. If the first-session setup is absent, establish the minimal objective, authority, current state, and recoverable work records before proceeding. Do not build the entire orchestration system merely to start deployment work.

Distinguish:

- **Preparing deployment:** inspecting, implementing configuration and automation, building artifacts, writing the runbook, and conducting authorized rehearsals.
- **Applying deployment:** changing a named environment or publishing an artifact with external effects.

Use authority already granted for the actual scope. Do not require repeated permission for the same authorized action. Where authority is missing, complete the preparation and present the concrete candidate, destination, effects, evidence, and recovery procedure for the remaining decision. Never infer production access or publication authority merely from the request to build deployment.

### Keep coordinators available and give execution an owner

The main orchestrator and every deployment lead acting as a coordinator must remain available for routing, decisions, integration, and recovery. They must not launch, own, or monitor through long-running calls any build, test suite, packaging job, infrastructure plan/apply, migration, release, health-observation loop, heavy tool operation, or background job. Delegate these to real execution sessions through the project's orchestration mechanism. A delegated deployment executor may run a bounded assigned job; a deployment lead does not become an executor merely because it is a child of the main orchestrator. Do not evade this boundary by renaming the role or moving a shell command to background execution.

Coordinators may inspect small state records, review bounded summaries, check dependency and authority conditions, dispatch assignments, and consume completion evidence. Any inspection that becomes heavy or requires sustained waiting belongs to an execution or observation session. Monitoring must not keep the main conversation occupied by repeated waits, log streaming, polling, or repeated “continue” requests.

Use `FIRST_SESSION_AND_ORCHESTRATION.md` and the generated project protocol as the canonical source for task states, assignment ownership, fencing, dispatch, capacity, and recovery. Release phases and operation observations in this document describe deployment facts; they do not create a second scheduler or competing ownership system.

Before handing off a long job, consult and, through a bounded capability check, update the main protocol's capability record for the actual Copilot surface and environment. Delegation must return control to the coordinator promptly: a synchronous subagent call that holds the coordinator until the long job finishes does not satisfy this requirement. Use verified nonblocking dispatch to an independent execution session or runner, with a separate status route. If the available delegation only waits synchronously, use the prepared manual execution-session handoff instead. Record whether a worker, terminal process, workflow runner, or background mechanism can continue after its launching call, session return, disconnection, or restart. Do not assume a stateless subagent survives its return or that a terminal handle implies a durable process. An external job may outlive a session only if the supported mechanism and independently accessible status have been verified. A worker assigned to launch a durable job may hand observation to another assigned session only after recording the accepted handoff; launching it and disappearing is not ownership.

When suitable autonomous session creation or persistent execution is unavailable, prepare a complete worker launch packet for a separately opened execution session. Give the operator the exact supported steps to open that session and return its acknowledgement. Record requested delivery and missing acknowledgement in the canonical assignment record; do not mark the worker active until acceptance and actual execution are evidenced. Continue independent preparation through available workers. The coordinator must never run the job itself as a fallback, and it must not claim the manually opened session exists or is active before observing that evidence.

## 2. Discover the deployment contract

Create a concise deployment contract from inspected project facts and user requirements:

| Area | Establish before committing to a route |
| --- | --- |
| Deliverable | What is deployed or published, who uses it, and what observable behavior proves it works. |
| Targets | Actual accounts, projects, regions, clusters, hosts, registries, stores, or distribution channels, as applicable. |
| Architecture | Entry points, runtime dependencies, external integrations, state, scheduled work, and ownership boundaries. |
| Current system | Existing resources, build/release workflows, environments, identities, secrets references, and known drift. |
| Requirements | Availability, performance, security, supported clients, accessibility, data handling, cost, and recovery needs relevant to this project. |
| Release constraints | Downtime tolerance, compatibility window, maintenance windows, review or publication rules, and rollback limitations. |
| Authority | Allowed targets and mutations, source of authorization, any explicit limits, and the owner of a remaining decision. |
| Evidence | What must be checked before release, during exposure, and before declaring the release successful. |
| Execution | Verified worker/session/runner mechanisms, actual launch and status interfaces, survival limits, acknowledgements, observation ownership, and manual-session fallback. |
| Parallelism | Independent candidates and targets, dependency contracts, shared resource keys, measured contention, and conditions that require serial execution. |
| Recovery | Durable task and release records, job handles, queued intent, delivery evidence, and reconciliation after session or platform interruption. |

Mark unprovided facts unknown. Propose requirements or defaults explicitly when needed; do not quietly turn suggestions into user commitments. Verify provider features, commands, versions, and limits against current official documentation and the actual account configuration.

If the destination is undecided, investigate realistic options against the project's constraints and prepare a recommendation. Continue portable build and test work while a material destination decision is pending. Do not create paid resources merely to avoid asking that question.

Map every deployable component and its dependencies. Include configuration, data migrations, scheduled jobs, queues, indexes, models, prompts, and infrastructure where they affect runtime behavior. Identify which items can change independently and which must be released together.

### Release work as dependencies allow

Prefer useful parallel work whenever workers, interfaces, and isolation support it. There is no default two-worker ceiling or predetermined fan-out. Use the project's shared capacity and scheduling rules; do not start a deployment-specific capacity counter. Reassess assignments when a worker completes, a contract changes, a blocker clears, contention appears, or a critical-path task needs attention.

Packaging, configuration validation, infrastructure planning, migration preparation, health-check implementation, and runbook preparation can progress concurrently when each has adequate input contracts. Keep work narrow enough to have an owner, a concrete result, and a reconciliation route. A worker awaiting an infrastructure decision need not stop another worker from validating configuration or preparing an immutable artifact. Verify workspace isolation and write ownership as well as target isolation; another chat or fork is not evidence of a separate checkout. Use supported isolated workspaces or explicit disjoint write scopes under the main protocol. Do not create workers for work that cannot usefully start, or split tiny tasks whose coordination cost exceeds the benefit.

| Workstream | May start when | Coordination boundary |
| --- | --- | --- |
| Build and packaging | A pinned source snapshot and build-input contract exist. | Isolate output paths, caches where contention requires it, and candidate identities. |
| Configuration and identity validation | The intended configuration and identity interfaces are defined. | Separate read-only checks from credential or target mutations; respect external rate and capacity limits. |
| Infrastructure planning | The target and desired-resource contract are established. | Isolate plans and state; inspect actual backend locking requirements, including locks required by planning tools. |
| Migration preparation | Schema changes and compatibility requirements are defined. | Prepare scripts and rehearse against isolated state; serialize changes to shared data. |
| Health checks and recovery implementation | Acceptance behavior and operational interfaces are defined. | Develop against fixtures or isolated targets; bind release acceptance to checks actually run on the candidate and target. |
| Runbook and setup distribution | Commands, configuration paths, and supported surfaces are sufficiently defined. | Track unresolved inputs and integrate verified commands as workers finish. |

Use dependency edges and scoped resource ownership, not a wait-for-everyone phase barrier. Each candidate may move to its next eligible action once its own applicable gates pass. Keep immutable candidate preparation and checks concurrent; a global publication boundary does not require global serialization of all preceding work. A shared contract change invalidates affected checks explicitly; evidence for unrelated components remains usable only where its inputs still match.

Serialize conflicting destination applies, migrations, shared-state writes, mutable release aliases, and final publication under keys that identify the actual shared resource. Independent destinations may proceed concurrently when their identities, state, credentials, external effects, and rollback paths are sufficiently isolated. Do not assume different environment names imply isolation. Apply backpressure to the affected target, dependency, or constrained resource. Broaden the pause only when an observed shared risk warrants it.

## 3. Produce concrete project artifacts

Reuse existing locations and name the real paths in the final report. Otherwise choose clear project-native locations. Produce the applicable artifacts below; explain exclusions rather than filling the repository with unused templates.

| Deliverable | Required substance |
| --- | --- |
| Deployment architecture and decisions | Actual topology, dependencies, target choice, tradeoffs, and release boundaries. |
| Build and packaging implementation | Reproducible entry points, declared toolchain, locked dependencies where supported, artifact identity, and configuration boundaries. |
| Environment configuration | Validated configuration schema or equivalent, documented defaults, required values, and secret references without secret values. |
| Infrastructure or installation implementation | Versioned provisioning or installation steps appropriate to the target, including existing-resource handling. |
| Release automation | Real workflow definitions or scripts with target checks, verification, scoped concurrency controls, worker and operation tracking, durable launch records, queue reconciliation, and failure behavior. |
| Data and compatibility plan | Version transitions, migration ordering, mixed-version behavior, and recovery consequences where state or consumers are affected. |
| Observability and health checks | Signals tied to user outcomes, release identity, diagnostic access, and actionable failure thresholds. |
| Recovery implementation | The applicable rollback, roll-forward, restore, or reinstall procedures, including limits and authority. |
| Verification evidence | Commands or actions actually run, candidate and environment identity, results, and unverified areas. |
| Operator runbook | Exact prerequisites, commands or UI steps, normal release flow, interrupted-release recovery, and maintenance responsibilities. |

Also address deployment of the orchestration setup if it includes runtime components. Repository instructions and role files need distribution and activation checks. A real supervisor or shared coordination service additionally needs hosting, state persistence, identity, upgrades, monitoring, and recovery. Treat those as actual components only if the project has adopted them.

### Deliver the Copilot working setup

The first session establishes the project-specific workflow. This session makes its installation, updates, and recovery repeatable where deployment of that setup is needed. Coordinate changes through the existing integration owner.

1. **Inventory the package:** identify instruction entrypoints, project protocol, role configurations, prompt shortcuts, skill references, optional helper scripts, and any runtime services. Separate reusable assets from each project's facts, authority, and live state.
2. **Define compatibility and inputs:** record supported Copilot surfaces, verified configuration formats, required tools, instruction discovery scope, relevant skill prerequisites, and project-specific values. Do not hard-code unavailable model names or tool identifiers.
3. **Implement installation:** reuse the platform's native distribution mechanism where suitable. If repeated installation across projects needs a helper, implement a small installer with a preview of intended changes, explicit destination, preservation of existing instructions, and a clear conflict report. Repeated execution must not duplicate rules or replace user customization silently.
4. **Resolve dependencies:** enable or install relevant skills and tools through supported mechanisms within authority. Record their provenance and verification. Keep credentials and user-local settings out of a distributable repository package. Expose missing required dependencies as actionable installation failures; document optional fallbacks.
5. **Activate and verify:** use assigned execution sessions in a disposable project or isolated checkout to test installation, then confirm that a fresh intended session discovers the right instructions, roles, and relevant skills. Exercise dispatch, delivery acknowledgement, a bounded assignment, a recoverable long job where supported, and the recovery packet. Verify the actual execution and status interfaces for every supported Copilot surface; distinguish native delegation from manual session launch. Test the documented fallback when automatic delegation is absent.
6. **Implement updates:** give the package a version or source revision, show the changes before applying them, and preserve local policy and project state. If state formats change, provide a compatible transition or explicit migration. Active assignments must retain interpretable instructions, queued intent, ownership tokens, and job handles during the update; pause incompatible work before switching versions. Reconcile active workers and effects before changing any dispatch or state format.
7. **Provide rollback and removal:** preserve the previous usable configuration and identify exactly what installation owns. Restore only those assets. Do not erase project research, task history, unfinished work, unrelated instructions, or shared skills on removal. If a state migration is irreversible, document the actual recovery route instead of promising a simple downgrade.
8. **If a supervisor is actually included:** assign execution sessions to build its service definition, configuration, durable state, access control, health monitoring, and restart behavior. Test recovery of an interrupted coordinator and surviving workers, including queued messages that were not delivered and completed jobs whose results were not consumed. Do not label configuration files or an on-demand agent as a continuously running supervisor. Without a verified independent supervisor, document who can observe and resume work while Copilot is idle; do not promise automatic wake-up.

Deliver the package or configuration paths, installation and update commands or exact native steps, compatibility record, activation evidence, and recovery/removal instructions. Verify the actual setup in at least one representative project environment before calling its deployment proven. Keep any broader compatibility claims limited to environments that were checked.

## 4. Build a representative path and expand it in parallel

The areas below describe required engineering coverage and local dependencies, not global sequential phases. Assign eligible workstreams concurrently, integrate results as they arrive, and keep the coordinator out of all long executions. Only an action's actual prerequisites and shared-resource constraints should delay it.

### A. Establish a representative release slice

Choose a small, meaningful part of the workload that exercises its important deployment boundary. For example, a service slice may require its real authentication and data dependency; a package release may require installation and a consumer compatibility check. A successful empty page may prove too little.

Define its acceptance evidence before implementing the pipeline. Identify the earliest authorized isolated environment or distribution rehearsal. Record the gaps between this environment and the intended destination.

Use the slice to expose architecture or operational problems early. Feed material findings into the project decision and task records; do not keep deploying a design that the evidence has invalidated.

### B. Make the build and artifact identifiable

Implement the actual build entry points using the project's toolchain. Capture required versions and dependencies. Keep secret values out of source, logs, images, bundles, and artifacts.

Give each candidate an identity that links source revision or preserved snapshot, build configuration, dependency resolution, and artifact digest or platform equivalent. Retain build logs and applicable test results under the candidate identity. The packaging executor owns the real build process or runner handle and arranges observation independently of the coordinator.

Promote the same immutable artifact between environments where the platform permits it. If a target requires rebuilding or signing a different artifact, record each resulting identity and validate the relationship; do not claim byte-for-byte promotion where it did not occur.

Verify installation or startup from the produced artifact, not only from a developer's working directory. Include applicable supply-chain checks chosen from the project's actual exposure and requirements. Do not call a build reproducible merely because one local build succeeded.

### C. Implement configuration and identity

Separate build inputs, runtime configuration, and secrets. Validate required configuration early, with useful errors that do not reveal sensitive values. Document precedence and defaults so a session can determine the effective configuration.

Use the platform's supported identity and secret mechanisms. Prefer short-lived workload identity where supported and appropriate; document alternatives when it is unavailable. Scope build, deployment, and application permissions to their actual responsibilities.

Prevent untrusted changes from obtaining privileged release credentials. In CI, inspect trigger behavior, fork or external-contributor paths, dependency execution, and secret exposure. A protected deployment path must be enforced by real platform settings and permissions, not just a comment in a workflow file.

Record secret names, ownership, access requirements, and rotation procedures without storing values in session records. Verify that the deployed workload can reach required secrets and dependencies in its actual runtime identity.

### D. Implement provisioning or installation safely

Use appropriate versioned infrastructure or installation mechanisms. If resources already exist, inspect ownership and current state before importing, adopting, or changing them. Do not create duplicates because the local configuration is incomplete.

Implement explicit target selection and a visible preflight check of the account, project, environment, and destination. Avoid relying on whichever account or cluster happens to be the shell default.

Where the chosen tooling uses shared state and locks, configure their storage, access, concurrency, and recovery. Do not remove a lock or restart an apply solely because the chat or terminal timed out. First have an assigned execution or observation session establish whether an operation is still running and what it changed. An expired assignment does not prove a provider lock or remote apply is safe to clear.

Make reruns safe through supported idempotency, state reconciliation, or explicit preconditions. Document where these guarantees end. Provide the required network, certificates, storage, permissions, resource limits, and dependency wiring according to the real topology.

Preview consequential changes where supported, then compare the plan to intended resources. Keep destructive replacement, data deletion, and decommissioning explicit and within authority. Resource cleanup after a rehearsal is a separate effect that must preserve required evidence and useful data.

### E. Implement the release path

Use the existing CI/CD or release platform where suitable. Build the steps appropriate to the project: validate, package, publish or install, migrate when needed, expose the candidate, verify, and record the result. A library or desktop release may use different stages from an online service.

Configure concurrency around each target, publication channel, shared state, and shared migration boundary. Two sessions or workflows must not simultaneously apply conflicting changes to the same destination. Preserve the existing integration owner and canonical assignment ownership. Independent targets and immutable candidate checks may progress concurrently when verified isolation allows it. Do not cancel an in-flight stateful mutation casually to make room for a newer candidate or shorten a chat queue. Replacing a queued candidate requires reconciliation of whether the older intent was merely queued, accepted by a worker, or already launched.

Select an exposure strategy from actual risk and platform capability: a controlled replacement, rolling update, limited audience, canary, blue-green release, or channel promotion may be appropriate. Define stop signals and observation requirements before release. For live services, progressive exposure tied to health evidence is an established approach; adapt it to the workload rather than assuming every target supports it. [Microsoft safe deployment guidance](https://learn.microsoft.com/en-us/azure/well-architected/operational-excellence/safe-deployments).

Verify repository settings, environment protections, workflow permissions, required checks, triggers, and credential availability in the real platform when these are part of the design. Generating configuration does not prove those controls are enabled. If you cannot apply or inspect a required setting, prepare exact instructions for the authorized operator and label that gate unverified.

Make release jobs report candidate identity, target, task reference, worker identity, assignment ownership token, current phase, operation IDs, and links to independently inspectable status and evidence. Retain enough information for another execution session to resume observation or reconcile effects after interruption. Do not wait for unrelated worker completions when the candidate's applicable prerequisites are satisfied.

### F. Engineer state and compatibility transitions

For changes to persistent data or contracts, explicitly describe which old and new components can run together. Check clients, workers, scheduled jobs, event producers and consumers, cached data, and third-party integrations where applicable.

Choose a migration strategy that supports the required transition. An expand/migrate/contract approach may allow compatibility, but its suitability must be verified for the actual data and access patterns. Account for backfills, large data volumes, lock duration, retries, partial completion, and deployment ordering.

Keep irreversible transformations explicit. Reverting application code does not reverse a database migration. Restoring a backup may discard writes made after the backup or restore point. Establish the acceptable recovery consequences and authority before using that route.

Where backups are part of the recovery promise, verify a representative restore in an authorized isolated destination. Record its measured result and limits against actual recovery requirements. Do not invent recovery time or data-loss guarantees from the existence of a backup setting.

For asynchronous workloads, address draining or pausing consumers, in-flight work, duplicate processing, poison messages, and resumption as applicable. Reconcile external effects before replaying work.

For AI or research workloads, include the versions of models, prompts, datasets, indexes, evaluation sets, and relevant runtime settings in the release boundary when they affect results. Define representative quality, safety, latency, and cost evaluation appropriate to the use case. Report uncertainty and variation; do not promote a research prototype solely because it produced a favorable demonstration.

### G. Implement health, diagnosis, and recovery

Define success in terms of the deployed or installed system's useful behavior. A process starting or an HTTP endpoint returning a status code may be insufficient. Check the critical path through required dependencies and permissions.

Provide the logs, metrics, traces, job status, installation diagnostics, or other signals appropriate to the workload. Associate observations with the release identity and target. Make failures actionable: indicate the symptom, likely boundary, and next diagnostic or recovery step.

Assign sustained health observation to an execution/observation session or a verified monitoring mechanism with a named owner and an accessible status record. The coordinator consumes bounded updates and may continue dispatching independent work while observation runs. Set health thresholds and observation periods from requirements, baseline behavior, and representative traffic or work. Distinguish “no failures observed” from “the workload was meaningfully exercised.” Do not declare a quiet release healthy if the important path received no use.

Implement the applicable recovery route and verify it on a representative rehearsal. Specify when to stop exposure, roll back a compatible artifact, roll forward a fix, restore state, or request a decision. Avoid an automatic oscillation between deployment and rollback.

Connect deployment failures to the project task and decision records. Diagnose whether the cause is code, configuration, infrastructure, identity, data, capacity, or a wrong architectural assumption before assigning corrective work.

### H. Package the operator experience

The runbook must use the real project commands, paths, workflows, and environment selectors. Replace unresolved placeholders before calling a path runnable. A required secret reference may intentionally require secure provisioning; explain that prerequisite without embedding the secret.

Include both the normal flow and what to do when a session disappears, a job stays pending, a health check fails, or the platform reports an ambiguous result. Explain who coordinates the release, which execution session owns each operation, who observes it, and where a replacement finds its state. Document the queue-aware recovery in section 6, including what to preserve before a Copilot restart and how to distinguish a lost message from a still-running deployment.

List any remaining manual platform setup with exact navigation or API actions verified for the target. Keep these steps short and distinguish one-time installation from each-release operation. Do not hide missing implementation behind “configure your cloud” or “set up CI.”

## 5. Track release identity, authority, and actual state

Use an existing release record where possible. Otherwise create a compact record containing:

```yaml
release_id: <stable attempt or release identifier>
task_refs: <canonical orchestration task identifiers>
candidate: <source, build inputs, and immutable artifact identities>
configuration: <versioned configuration references; no secret values>
infrastructure_change: <plan or reviewed change identity when applicable>
data_change: <migration identities and compatibility conditions>
target: <explicit destination identity>
coordinator: <current release coordinator and canonical ownership reference>
authority: <source, scope, limits, and relevant validity conditions>
evidence: <checks and the exact candidate, inputs, and environment they cover>
phase: <observed deployment phase; not a separate orchestration task state>
resource_keys: <destination, shared state, migration, and publication scopes>
operations:
  - operation_id: <stable local intent identity, created before dispatch>
    task_ref: <canonical task identifier>
    ownership_token: <current canonical assignment ownership token>
    execution_session: <verified worker/session identity>
    runner: <actual supported runner or execution mechanism>
    candidate: <exact candidate affected by this operation>
    destination: <exact target and resource scope>
    resource_keys: <specific shared resources this operation may change>
    checkpoint: <durable pre-call work state and launch intent>
    delivery_ack: <observed worker acceptance or absent>
    launch_ack: <observed backend/process acceptance or absent>
    handle: <actual process/workflow/provider handle; unknown until observed>
    status_location: <independently inspectable status endpoint or record>
    evidence_location: <logs, output artifacts, and verification records>
    observer: <assigned session or verified monitor identity>
    progress: <last meaningful observation, timestamp, and source>
    next_observation: <responsible observer, trigger, and escalation condition>
    observed_outcome: <evidence-backed operation outcome or unknown>
    reconciliation: <last target inspection and safe next action>
queued_intent: <canonical durable intent/outbox references, backup identity, and delivery observations>
health: <observations, exposure, and remaining watch requirements>
recovery: <applicable procedure and its verified limits>
next_action: <bounded eligible action or explicit dependency/blocker>
```

Keep readiness separate from observed effects. “Approved,” “built,” “deployed,” and “healthy” mean different things. A candidate may be approved but never applied; an interrupted apply may have changed the target even if the job appears failed.

Define valid deployment-phase transitions and checks in the implementation while keeping orchestration tasks in the canonical task state model. At minimum distinguish preparation, validation, readiness under authority, active mutation, post-change verification, success, recovery, failure, and unknown outcome as deployment observations. A chat queue entry, worker acceptance, process launch, completed operation, and consumed result are separate facts. Neither a dispatch request nor a launch acknowledgement proves completion. Model parallel component operations explicitly; the record must show which candidate, target, resource key, and owner each observation concerns.

Before mutating the target, check that candidate identity, destination, relevant evidence, and authority still match. A replacement session may reuse valid authorization for the same scope. A changed candidate or material change in effects requires reevaluating the authority and the evidence it relied on; request a new decision only if the existing grant no longer covers it.

Do not let late edits silently replace a validated candidate. Rebuild or regenerate affected artifacts and rerun the checks invalidated by the change. Preserve the evidence chain for each candidate.

## 6. Recover interrupted deployment work without duplicate effects

### Make long jobs recoverable before launching them

The assigned executor must checkpoint before every long or consequential call and after observed phase changes. Preserve actual configuration and work, not just a description. Record the canonical task and assignment, candidate, exact command/action intent, destination, authority, resource keys, expected outputs, and reconciliation procedure before issuing the call. Capture the worker's delivery acknowledgement and actual launch acknowledgement separately. Record real process handles, workflow run IDs, and provider operation IDs as soon as observed; never substitute an invented identifier for a missing backend handle.

A handle without a usable inspection route is insufficient. Verify how another assigned session can inspect status and recover output, including after the original worker disappears. Set observation triggers and escalation conditions from the operation's actual behavior, configured platform limits, and project recovery requirements; do not invent fixed timeouts. A worker heartbeat alone does not prove job progress, and a quiet log does not prove the operation is stuck.

If the job itself requires a long-running synchronous tool, that call belongs inside an independent execution session with its pre-call checkpoint and recovery route. Its assignment must still be nonblocking for the coordinator; opening a synchronous child call from the coordinator is not an acceptable substitute. Do not claim it survives that session unless verified. If no supported mechanism can run and expose the operation adequately, preserve the prepared packet and state the exact missing execution capability. The coordinator continues coordination and does not take over the tool call.

### Reconcile after interruption

After a timeout, context failure, restart, or ownership transfer:

1. Have an assigned execution or observation session establish whether the former session, process, workflow, or provider operation is still active. Keep this investigation off the coordinator's long-running tool path.
2. Inspect the intended target and reconcile actual resources, artifact versions, migration status, exposure, and health with the release record.
3. Record each operation as intended, in progress, succeeded, failed, or outcome unknown. Do not treat missing output as proof of failure.
4. Verify current canonical ownership and resource exclusion before beginning a conflicting mutation. Revoke stale dispatch authority through the project protocol where supported; that alone does not stop an already-running external writer. Establish its actual completion or safely stop it under existing authority before replacement execution.
5. Assign observation of a surviving job, accept an evidenced completed result for the exact candidate and target, retry through a supported idempotent path, recover, or stop according to the reconciled state and authority. An unknown launch or apply outcome requires reconciliation before another attempt; missing acknowledgement must not trigger blind resubmission.
6. Update evidence and the next action before handing work onward.

Never repeat a resource creation, migration, publication, or traffic change merely because the chat has no completion message. Never bypass an authorization failure by weakening the policy or switching to a more privileged identity without authority.

Carry attempt limits and failure history across replacement sessions. If the same failure recurs, change the diagnostic hypothesis or stop the automated cycle. Do not make self-healing an unlimited loop of rebuild, redeploy, rollback, and retry.

### Recover idle sessions and accumulated queues

Store actionable release intent in the canonical durable task/dispatch records. The Copilot chat queue is a delivery channel, not the only record of outstanding work. Persist each intent's identity, scope, task reference, candidate, target, preconditions, assignment, and acknowledgement observations before relying on its delivery. Use the project's duplicate-prevention mechanism where available. Do not claim exactly-once dispatch merely because an intent has an ID.

When progress appears idle or messages pile up, delegate a bounded diagnosis that correlates the canonical records, current session state where inspectable, worker acknowledgements, process/workflow status, target effects, and unconsumed results. Report which condition is evidenced: useful long work is continuing, delivery is unacknowledged, a worker is awaiting input, capacity is exhausted, the backend job is pending, execution is stalled, a result is waiting to be integrated, or the cause is still unknown. Do not assign a timeout cause without evidence. Capture available errors and identifiers if the queue or transport itself fails.

Stop repeatedly sending the same intent into the affected channel. Preserve outstanding intent and restrict new delivery to that blocked lane until its condition is understood. Before treating other release work as independent or dispatching new effects, reconcile captured cancellations and changed constraints across all connections: pause the actual affected targets and resources, preserve live-job records, and reconcile running operations before attempting cancellation. Continue independent targets, runnable preparation, and result integration through functioning workers and supported channels. If workers finish but their messages are not consumed, retrieve their existing evidence before launching replacement work. If all useful work is waiting, record each dependency and the actual wake-up/observation owner; do not report normal progress or invent an automatic wake-up mechanism.

Before restarting the affected agent connection, restarting Copilot, or replacing a responsible session, use the main protocol's durable outbox and backup/reconnect/replay procedure. Preserve queued inputs with their original intent and ordering, release IDs, exact candidate identities, pending dispatch intent, current ownership, uncommitted work, checkpoints, actual operation and runner handles, observed backend queue entries, and evidence locations. Record and verify the recoverable backup before restarting the affected connection. Inspect actual job survival independently of the chat where supported. A restart is a transport/session recovery action; it neither proves that jobs stopped nor authorizes cancelling them. Restored chat history is not evidence of a surviving worker, terminal, runner, or host. Use actual job status and supported control handles to establish what is running; a queued stop/steer message, chat cancellation, or IDE reload is not proof that an external operation stopped. Do not delete platform queues, cancel workflows, terminate processes, or clear provider locks merely to empty the visible backlog.

After the connection handshake establishes the actual session identity and current canonical ownership, reopen the preserved state and reconcile each intent against worker acceptance, launch evidence, backend job state, and target effects. Apply only valid, unapplied queued intent through the main protocol's deduplication and ordering rules. Preserve steering, cancellation, and dependency ordering so an older queued apply cannot override a later stop or changed requirement. Never blindly replay create, migration, publish, or traffic-change actions from the backup; a connection restart is not cancellation or retry of a cloud apply. Reattach observation to surviving operations; integrate completed output under the current assignment identity without repeating target mutations. Re-dispatch only work shown not to have launched, or work whose retry is safe under verified idempotency and reconciled state. Keep uncertain effects blocked within their affected resource scope until reconciled while unrelated work proceeds. Reject stale-owner results or revalidate and integrate them through the current owner according to the main protocol; never let an old session resume conflicting writes automatically.

An independent recovery actor must own connection recovery; the main or deployment coordinator must not take on long reconnect tooling or recovery loops. Claim automatic backup/reconnect/replay only after verifying actual queue capture, connection restart, handshake, and recovery support in the installed surface. Otherwise provide the exact supported manual capture and reconnect steps plus the preserved recovery packet; do not invent controls or claim inaccessible queued input was backed up.

Document supported session recovery steps for the actual Copilot surface. If queue state cannot be inspected, say so and use durable intent plus independently inspectable operation evidence; do not manufacture queue APIs, automatically replay an unobservable backlog, or claim a restart will repair the cause. Where opening a fresh execution session is required, supply its complete recovery packet and request only that concrete operator action.

If an independent orchestration supervisor is included, test its behavior after its own restart: it must recover state, reconcile surviving workers and operations, reject stale ownership, preserve queued intent, and avoid duplicate dispatch. A process manager restarting it is only one part of that recovery.

## 7. Verify the implementation, including meaningful failures

Select checks that resolve concrete release risks. Exercise the supported end-to-end path using an authorized isolated target or distribution rehearsal. Where real infrastructure is unavailable, validate locally and state exactly what remains unproven.

Use the following scenarios as a coverage review, selecting those that apply:

| Scenario | Evidence sought |
| --- | --- |
| Clean build and fresh install/start | The produced artifact works with declared prerequisites. |
| Missing or invalid configuration | Early useful failure without leaking secrets or partially exposing a broken system. |
| Wrong account or target | Preflight prevents mutation of the unintended destination. |
| Unauthorized or untrusted release path | Real controls prevent privileged application or publication. |
| Concurrent releases | Conflicting target mutations are excluded while independent targets with isolated state can proceed. |
| Long build or tool call | The executor owns the job and actual handle; the main and deployment coordinators remain responsive and can route other eligible work. |
| Slow work with healthy progress | Evidence distinguishes legitimate duration from a stalled session without needless cancellation or duplicate dispatch. |
| Uneven worker completion | A ready candidate proceeds when its own dependencies pass; unrelated workers do not create a wait-all gate. |
| Worker return or disappearance | Actual survival semantics match the documented capability; another assigned observer can inspect surviving work or reconcile unknown effects. |
| Lost launch acknowledgement | Target and runner reconciliation prevents a second apply, migration, or publication. |
| Idle Copilot with queued intent | A bounded diagnosis preserves requirements and intent, identifies observed delivery/execution state, and keeps unaffected lanes progressing. |
| Queue loss or Copilot restart | Surviving operation handles are recovered, completed output is consumed, and a missing chat message does not relaunch an apply. |
| Backed-up queue after connection restart | An independent recovery actor verifies the backup and handshake, reconciles handles and ownership, applies only valid unapplied intent with steering/cancellation/dependency order and deduplication intact, and keeps uncertain effects scoped without replaying a live or completed apply. Automatic claims are limited to verified capture/reconnect support; exercise the documented manual path otherwise. |
| Interrupted or ambiguous operation | A new session reconciles state before retrying. |
| Partially completed migration | Resume or recovery follows the actual migration's semantics without corrupting data. |
| Mixed old and new versions | Required consumers and background work remain compatible through the transition. |
| Failed post-change health | Exposure stops and the defined recovery path is usable. |
| Changed candidate after validation | Stale evidence is not accepted for different artifacts or effects. |
| Backup restore, when promised | A representative restore produces usable state, with measured limits. |
| Supervisor failure, when implemented | Canonical ownership, queued intent, and pending effects survive restart without duplicate work. |
| No automatic worker capability | The documented manual execution-session path accepts the packet; the coordinator does not run the job itself or report an unlaunched worker. |

Run these checks through assigned execution sessions. Use fixtures, mocks, and simulation where appropriate to test failure handling, but distinguish those results from behavior verified on the real platform. For queue and interruption drills, verify the actual supported session and runner behavior in a safe representative setting; a simulated durable runner does not prove Copilot retains a session. Do not damage production to demonstrate recovery.

Record executed commands or workflow runs, source and artifact identity, environment, timestamps, outcomes, and relevant logs. Separate existing failures, introduced failures, skipped checks, and blocked checks. Do not say “deployment tested” when only configuration syntax was checked.

Once the relevant risks and required gates are sufficiently verified, stop optional testing and complete the handoff or authorized release.

## 8. Leave a runbook another session and the user can execute

The final project runbook must answer these questions with actual project details:

1. What is deployed, where, and how are instructions or runtime helpers activated if they are part of the system?
2. What accounts, tools, versions, permissions, configuration, and secret references are required?
3. How does an operator verify the selected target before making changes?
4. What exact commands, workflow actions, or UI steps build, provision or install, release, and verify the candidate?
5. How are candidate identity, authority, environment protections, and concurrency checked?
6. What happens to data, consumers, in-flight work, and backward compatibility during the transition?
7. What observations establish success, and how long must the relevant behavior be observed?
8. Which session executes each job, where are delivery and launch acknowledgements and actual handles recorded, and how does another assigned session inspect an interrupted operation, reconcile its outcome, and resume safely?
9. What recovery routes work, which have been exercised, and what data or service consequences remain?
10. Who owns routine operation, access and certificate renewal, secret rotation, dependency updates, backup checks, and incident response where applicable?
11. Which cost drivers, capacity limits, cleanup steps, and decommissioning obligations affect this design?
12. How are parallel preparation and independent targets released without a global wait-all barrier, and which precise shared-resource keys require exclusive mutation?
13. Who observes long jobs while the coordinator remains available, and what verified mechanism or operator action resumes observation when a session is idle or gone?
14. Who backs up queued inputs and release/job identities before restarting the affected connection, how are handshake and current ownership verified, and how is valid unapplied intent restored in order without duplicate apply/publication?
15. What is still blocked or unverified, what exactly resolves it, and what work can continue meanwhile?

Do not fabricate an owner, budget, service objective, provider feature, or result to fill this runbook. Propose unresolved operational decisions clearly. Use current sourced pricing only when cost figures are required; otherwise identify cost drivers and measurement methods.

Deliver a concise completion report with generated paths, implemented behavior, the strongest executed evidence, real environment effects, recovery coverage, unresolved limits, and the next exact action. Distinguish **files prepared**, **automation exercised**, **environment changed**, and **release verified**.

If deployment is authorized and its gates are satisfied, carry the release through assigned execution and observation sessions to verification, then update the runbook with observed results. If a final decision or unavailable credential is required, leave a concrete, reviewable release packet and exact remaining action. Do not stop with a generic plan when further authorized implementation or verification is possible.
