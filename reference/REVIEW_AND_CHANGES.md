# Orchestration review and revision guide

**Revision:** 2.1.7 — 6 September 2026

**Historical 2.0 review input:** all three Markdown documents in the uploaded archive.  
**Scope:** preserve orchestration, parallelism, bootstrap progression, approval and accounting while correcting persistent coordinator role and per-event action routing.

## Revision 2.1.7 persistent coordinator role and routing

Tracking: [issue #1](https://github.com/taomar/foldspace-orchestrator/issues/1).
The reported interaction shows a coordinator performing repeated domain
documentation research and planning after a user clarification. It does **not**
establish source edits, a stalled host, the adopter's loaded revision, or its
actual role/tool restrictions. This release does not inspect or recover that
project or diagnose a cloud/authentication implementation.

**Confirmed documentation gap:** at public main
`4b67471fb7224ddd13255b9b681d36f3a1114c31`, section 2 and the generated runtime
core already required coordinator-only roles, delegated execution and supported
tool allowlists. The compact bootstrap omitted persistent identity and a
pre-action role gate while allowing "one known-short targeted read per missing
fact", "approved action" and "Continue the objective". Section 7 reconciled
events without forcing a role/action decision before tools or research.
Several copied prompts repeated the unqualified continuation. This is an
active-text propagation/admission gap, not the absence of any role boundary.
Whether that text caused the reported adopter behavior remains unconfirmed.

**Correction at the existing boundary:** section 2 owns sticky role and action
admission by kind/ownership, not just duration; section 7 applies it on every
message/answer/event before tools/skills or substantive investigation. Root and
child coordinators answer from held evidence/brief known concepts or compact
coordination state, route genuine steering to the existing responsible owner,
admit a bounded executor when appropriate, or delegate a parent-scoped
multi-lane capability to a sub-orchestrator. Even one source investigation,
domain-docs lookup or implementation edit belongs to execution. Approval
permits dispatch, not coordinator role drift; approved workers actually execute.

The compact bootstrap, runtime core, role packets, configuration interview,
onboarding and operator/deployment prompts carry that contract. Setup workers
must adapt active host-supported entrypoints/cores/roles and native tool
profiles where verified, not only download reference files. Fresh target root,
child coordinator and spawned-executor activation checks distinguish loaded
instructions from enforced restrictions. Generic execution-capable tools remain
instructional exposure. Higher-priority host conflicts require supported
configuration or an explicit assisted route, not invented config/hooks/tools.
Tool filtering cannot guarantee short model reasoning or prevent host stalls.

**Compatibility and containment:** existing-owner-first routing preserves stable
requirement/steering IDs, versioned authority, busy-owner control delivery,
durable backlog and 2.1.6 uncertain-dispatch quarantine. No mandatory fan-out,
competing authority/ledger or default worker count is introduced. Descendants
inherit/tighten models/reasoning, consent, resources and remaining budgets.
Preapproval questions still advance; no discovery worker is required to find a
missing model choice. Detected drift stops further coordinator execution while
preserving live handles/effects/write ownership and arranging supported safe
observation/recovery handoff, not abandonment or blind cancellation.

The [finite routing cases](../operations/EXAMPLES.md#coordinator-role-routing-cases)
are document-level expectations, **not executed host proof**. Native document
checks cover links/anchors, fences, versions/source map, compact entry size and
the unchanged 14-file layout; published pinned bytes are checked separately.
No runtime, installer, watchdog, package, CI, extension or evaluation agent is
added. Broader host enforcement and the adopter's loaded configuration remain
unverified, not claimed repaired by this publication.

The single [Copilot-only upgrade prompt](../docs/GETTING_STARTED.md#upgrade-without-resetting-live-work)
is pinned in a follow-up to the actual published canonical 2.1.7 commit. Until
that follow-up it explicitly retains its prior 2.1.6 pin, not a guessed SHA.
Migration deliberately merges active root/child roles and executor distinctions,
retaining valid approvals/settings, owners, pending operations, usage/
reservations, local customizations and old references. It does not start a new
run or reapprove unchanged authorized choices. True material scope/capability
decisions still require approval. Restoring old instructions cannot undo live
effects or state/accounting. Do not paste migration into a blocked queue.

Publication now follows the existing
[contribution guide](../.github/CONTRIBUTING.md#issue-linked-publication):
one issue per distinct change, reused and updated for every related push with
commit identity, actual fix/evidence and remaining limits.

## Revision 2.1.6 safe admission and uncertain dispatch

This is a policy correction and containment of unreliable session delivery,
**not a fix for the host's internal idle-wake defect**. A successful send, READY
reply, UI IDLE label or missing ACK does not establish whether an assignment
can safely start, already ran, or may still produce effects.

The existing policy already separated backlog, delivery and operations, but
section 7 described persisting assignment identity after launch while section 8
required a pre-launch dispatch ID. General handshake/replay language also left
room to treat liveness as admission or restored chat as a task scheduler.
The correction belongs to the existing sections 3, 8-10 and 13, propagated to
the runtime core, optional enforcement contract and deployment/operator guidance:

| Policy correction | Boundary and consequence |
|---|---|
| Admit new assignments, not control traffic | Default one active assignment and at most one unacknowledged assignment dispatch per worker, zero pending task backlog in chat. Busy/dispatching/recovering/uncertain/resource-unavailable lanes receive no additional task. Answers, steering, cancellations and status/result/recovery controls use demonstrated priority/control or exact assisted routes. Host-internal queueing may still occur. |
| Optional readiness, not a wake guarantee | READY_CHECK/READY are application markers only. READY then IDLE then send leaves a time-of-check/time-of-use gap. A supported creation request may carry a complete approved bounded packet; reconcile receipt/start rather than require a second readiness roundtrip. Reconnect/reload still requires ownership/job reconciliation. |
| Reserve before send, observe states separately | Reuse task_id, assignment_version, dispatch_id, coordinator_epoch and candidate/result identities; no synonymous assignment ID or new scheduler. Reserve task/receiver/resources/budget and persist the packet before transport. Receiver validates and records exact acceptance before effects. Logical readiness, delivery and execution/results remain separate; valid out-of-order results need not wait for a lost ACK. |
| Quarantine ambiguity, do not revoke execution | Timeout, transport error or unexplained idle stops new assignments to the suspect lane, not existing jobs or ownership. Preserve payloads, checkpoints, handles, receipts, usage and reservations. Inspect receiver/jobs/effects/newer controls/results; observe running work or consume completed results. Even one redispatch is unsafe without reconciliation. |
| Fence actual conflicting effects before replacement | Prove nonexecution with no possible obsolete late start, or establish safe stop/surrender/fencing at the actual write boundary and reconcile effects/charges. Ledger-only revocation and ACK receipt are not fencing. Late obsolete ACK/start cannot regain ownership; duplicate logical results cannot integrate twice. Unknown exposure and attempt history survive replacement. |
| One authority and independent pickup | Reuse a durable authoritative ledger under one current coordinator/actual serialized writer; workers own operation/results. Apply 2.1.5 pickup/observer or accepted operator coverage to parent and workers. No automatic supervisor, global serialization or unbounded spawning is introduced. |

The [finite cases](../operations/EXAMPLES.md#safe-assignment-and-uncertain-delivery-cases)
define the intended outcomes for busy/control traffic, readiness gaps, complete
startup packets, running work with lost ACK, safely bounded undelivered retry,
unfenced writers, obsolete receipts, duplicate/current results, parent pickup
failure and exhausted or uncertain budgets. They are documentation scenarios,
not claimed host fault injection, universal exactly-once delivery or runtime
enforcement.

**Migration and compatibility:** keep the 14-file layout and URL-first/no-clone
entry. Preserve one outstanding unanswered question, immediate progression on
delivered answers/events, optional staged inputs, exact models/role/fallbacks,
model-specific reasoning or verified accepted N/A, scoped external consent
default-denied, final new-run approval, same-run authority and inherited limits.
Public reference GETs are not external inference. Keep existing task vocabulary
with an explicit evidence mapping; do not reset owners or accounting.

The single [Copilot-only in-place upgrade prompt](../docs/GETTING_STARTED.md#upgrade-without-resetting-live-work)
names its immutable source commit. Publication first commits canonical 2.1.6,
then pins that prompt to the actual published commit in a follow-up; all upgrade
companions use that same source, not moving main. The approved setup worker
compares and merges the policy into active entrypoint/runtime/prompt copies,
retaining prior references and customizations. Changing cached references alone
does not deactivate conflicting old rules. Restoring old instructions cannot
undo live effects, task state or charges. No executable updater, dependencies,
runtime enforcement, CI or agent framework is added.

## Revision 2.1.5 idle-delivery prevention and recovery

Investigation of a reported idle coordinator found a normal completed response
with no unfinished tools, followed by acknowledged "immediate" sends that never
appeared as receiver input. Delivery while active had worked; later routine
session shutdown occurred after delivery had already stopped. This establishes
an idle queue-to-session handoff failure boundary, not its internal app cause.
It is distinct from 2.1.4's answered-question stopping-rule correction.

The existing protocol already required durable intent and reconciliation, but
its yield/return contract did not require end-to-end **idle** receipt/pickup
evidence or an actually armed independent observer. The correction strengthens
the existing section 10 [safety contract](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md#idle-delivery-safety-contract),
not a second scheduler, state store or budget:

- Persist original intent and identified results outside the recipient queue
  before notification. Distinguish transport submission, receiver receipt,
  application/pickup and execution/acceptance.
- Prove active-to-idle delivery and required closure survival before claiming
  unattended pickup. Register independent observation and recheck pending
  state/cursor before yield so the handoff itself does not leave an arrival gap.
- Require an armed independent observer/runner, finite receipt/pickup windows,
  alternate alert/control route, scoped recovery authority and inherited
  allowance; otherwise explicitly accept an operator-carried handoff.
- On missed receipt, stop redundant sends, preserve accessible queued input,
  use an independent state-appropriate resume/reattach route or safe ownership
  transfer, reconcile actual effects/results/charges, and restore only valid
  unapplied intent. Late delivery must not duplicate acceptance or effects.
- Detect observer loss only through demonstrated coverage; otherwise disclose
  the gap. Stop at finite limits with preserved work and the actual manual
  unblocker, not repeated "continue", polling agents or recursive supervisors.

Bootstrap, generated runtime core, capability/dispatch/activation contracts,
operator and deployment guidance, adoption prompts and optional input fields
now refer to that boundary. The existing assignment shape gains a
`delivery_recovery_ref` to the owning policy/route; equivalent existing fields
remain valid. Adapt active project instructions/packets prospectively under
approval without silently changing pinned references, owners, authority or
ledger totals. No live record migration is performed by this publication.

The [finite cases](../operations/EXAMPLES.md#prevent-and-recover-missed-idle-delivery)
cover missed idle delivery, arrival during yield, closed receivers, unknown UI
queue durability, lost/late receipts, observer failure, genuine unanswered
approval, capped recovery and manual fallback. These are document-level
contracts, not executed host fault-injection or evidence that automatic
recovery is installed. The host's internal queue defect remains unconfirmed
and is not repaired here. Uncaptured private UI input cannot be reconstructed.

Model/reasoning evidence, external-call denial/consent, final approval, budgets,
ownership/fencing, resource exclusions, stateful jobs and uncertainty remain
protected. A requested recovery feature is not permission to start unapproved
diagnostic workers, spend beyond reservations, clear queues, restart unrelated
processes or rerun publication. The URL-first source map and folder layout stay
unchanged; this remains a documentation protocol, not an executable runtime.

## Revision 2.1.4 bootstrap progression and optional inputs

**Established protocol fault:** revision 2.1.3 at public commit
`89b1ea72aaa788e4d28c5d09a645524c0793c3fc` carried the 2.1.2 instruction to
resolve one interview decision per response and return after a targeted lookup.
The compact entry, main section 3, generated runtime core, questionnaire and
copied prompts could therefore end after an answer even when the next
clarification was permitted. Missing dispatch approval was conflated with a
reason to stop interview preparation.

The reported example selected a new run, answered the outcome question with
"continue the pendings", and received only a completed acknowledgement that
scope, criteria, limits and approval remained unresolved. The answer had
already returned; it was not an outstanding question. That trajectory exposes
the faulty terminal transition, not evidence of a photographed host hang.
A second screenshot shows the same pattern after a model allowlist was
recorded: "Next is role assignment" described but did not ask the next question.
Requesting the approval process must advance the interview, not silently grant
final approval or produce another acknowledgement-only stop.

**Owning correction:** the main section 3
[transition contract](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md#opening-turn-and-return-control-contract)
now requires reconciliation of delivered answers/tool results/steering/
acknowledgements/completions and the next permitted bounded step. One question
at a time means one outstanding unanswered question, not one answered decision
per response. Safe reads, focused questions, policy review/final approval and
already-authorized actions prevent a status-only unfinished-work exit.
Real waits name the exact input/dependency, actor and supported resume event or
manual action. Actual host question lifecycle remains authoritative; no forced
tool completion, polling, automatic "continue" loop or invented self-wake.

"Continue pending" uses supplied context or known compact authoritative
state/checkpoint/task records to derive candidates and acceptance. Ask focused
selection or the exact missing record/access, not a rewritten backlog or broad
discovery. Capability evidence must not require an unapproved worker to unlock
its own gate; safe bounded evidence and independent interview decisions remain
possible. Approved execution workers consume their assignments rather than
inherit coordinator-only interview/preparation limits as execution stops.

The [optional checklist and placeholder template](../protocol/RUN_CONFIGURATION.md#optional-prestaged-interview-inputs)
separate operator choices from agent-verified facts and required from
conditional/optional fields. Paste known answers under the URL-first prompt;
no attachment, new live store or public disclosure of private inputs is needed.
Partial inputs lead to the next missing question. Complete unapproved inputs
lead to validation/summary/final approval, not question replay or auto-dispatch.

**Preserved boundaries:** exact models/fallbacks and per-model verified
reasoning bounds/default or explicitly accepted verified N/A; external calls
default denied with separate consent; explicit units/caps/allocations,
concurrency/retries, reservations and separate incomparable ledgers; final
new-run approval; same-run authority; existing owners, effects, resource
exclusions, usage and uncertainty. Public reference GETs are not external
inference. URL-first adoption, pinned safe localization, final folder layout
and preparation-versus-release authority remain unchanged.

**Compatibility and limits:** deliberately update conflicting active prompt/
runtime copies in an approved target adaptation; do not silently replace pinned
references or reset live records. The
[finite transition cases](../operations/EXAMPLES.md#bootstrap-transition-examples)
cover answered versus unanswered tools, the reported pending-work path,
unknown records, missing capability, staged inputs, approved continuation/
assignment/result, and hard budget/authority blocks. They are document-level
cases, not executed host evaluations or proof of enforced controls. This
publication does not claim to reproduce or repair the photographed host.

Separately, observation of a completed publication worker found later requests
absent from its receiving session history. That supports a delivery/wake
boundary gap, not evidence that worker ran this bootstrap and dead-ended.
The underlying host/application cause remains unconfirmed; no platform
workaround, runtime, package, worker framework or supervisor is introduced.

## Revision 2.1.3 URL-first adoption

This is historical context. The 2.1.4 transition contract supersedes earlier
per-response decision/return wording; the URL-first localization contract stays.

The standard onboarding now starts with one pasted prompt containing the full
public raw Markdown bootstrap URL. The operator opens the actual target project
and supplies the outcome/decisions; no FoldSpace clone, ZIP, attachment or copy
script is a prerequisite. The compact entry owns the companion full-URL map
and still returns the first question/checkpoint before bulk work.

Bounded reads of user-approved public reference text are distinguished from
direct external LLM inference. They do not authorize private-data uploads,
workers or bulk setup before approval. Model/reasoning, consent, budgets and
the final operator approval remain mandatory.

After approval, a bounded setup worker pins one source commit, previews
destinations/conflicts, copies the required linked references and MIT license,
records provenance, and adapts existing project-native instructions/state
without overwriting live work. Discovery and handoff evidence precede reliance
on the new setup; the user outcome continues beyond downloading documents.
Same-run continuation reuses valid policy and pinned copies instead of silently
upgrading them from moving `main`.

Hosts without usable network/write/dispatch tools must report the exact gap
and use normal permissions or an exceptional assisted transfer. This is an
agent workflow specification, not a new downloader, installer, SDK or
guarantee that every Copilot host can execute it.

## Revision 2.1.2 bootstrap responsiveness

The per-response stop rules described below are historical and superseded by
2.1.4's advance-or-real-wait contract, not active instructions to stop after an
answered question.

An early queued/silent bootstrap was reported with little worker activity.
The affected host, session/request trace, and automation producer were not
available to establish its runtime cause. Low worker activity does not exclude
context processing, a long model turn, one stuck tool, or an automation loop.

The documentation did expose a startup gap: it recommended loading three
large references before the first interaction and required "short, bounded"
coordination without explicit opening-response or return-control boundaries.

- [BOOTSTRAP.md](../protocol/BOOTSTRAP.md) is now the small first entry; detailed
  references remain authoritative and are loaded for the current decision.
- The coordinator acknowledges supplied context, asks one unresolved question,
  and returns. Preapproval evidence work is one known-short targeted lookup
  for that question, not catalogs, bulk scans or setup generation.
- Missing input/evidence becomes a visible hold with an owner and next action.
  After approved dispatch, unrelated eligible work continues; full-job waits,
  polling and a wait-for-all reporting barrier do not occupy the coordinator.
- Early no-worker interaction and wait-return drills complement the existing
  post-dispatch responsiveness checks. These are required observations, not
  claims that this publication reproduced or repaired a live queue.
- A stalled session cannot be recovered by feeding its blocked message path.
  Operator guidance now separates independent observation/control from queued
  prompts and identifies possible automation producers, overlap and admission.
  Pausing future triggers requires authority and does not cancel live jobs or
  delete existing intent. No automation is installed or altered by this pack.

The mandatory model/reasoning/consent/budget interview, exact-setting evidence,
final approval, scoped ownership, inherited reservations, candidate acceptance,
and recovery-before-replay rules remain in force. Returning a response is not
declaring project completion; a short entry cannot guarantee host latency,
message delivery, self-wake, cancellation, or producer-side admission.

## Revision 2.1.1 principles correction

The review against the original 2.0 policy found one localized regression:
operator guide section 10 had extended the instruction not to import another
project's active owners to a new run of the **same** project. That could hide a
surviving worker or migration just when the next run checks for conflicts.

Revision 2.1.1 separates those cases. A different project does not import
unrelated ownership; a new run in the same project reconfirms configuration
without discarding authoritative task state, owners, assignments, operation
handles, resource exclusions, evidence, reservations, or charges. Ownership
changes still require the established validity and safe-handover rules.

The representative case is a new run with a surviving migration and an
unrelated ready documentation task: retain the migration's owner, handle,
resource exclusion and budget reservation, block conflicting work until
reconciliation, and allow the unrelated task once its own gates are satisfied.
The operator guide, adoption guide and run-configuration examples now agree
on that outcome.

The review found no other significant semantic regression in coordinator and
execution separation, dependency-driven parallelism, candidate-bound evidence,
scoped recovery, inherited budgets, or preparation versus release authority.
The mandatory model/reasoning, external-consent and budget interview remains
the intentional enhancement. It does not replace those original principles.
This is a document-level finding and correction, not proof of live host
enforcement, cost control, or successful runtime recovery.

## Revision 2.1 release notes — 6 September 2026

Revision **2.0** was publicly committed at `38e9ce28964d8038333a2034a6ff02087b4652f9`. It remains the historical source baseline; the source ZIP is immutable. Revision 2.1 is a follow-up documentation revision, not a rewrite of that archive or a claim that its historical tests establish current runtime behavior. The original review findings below are retained as provenance and continue to explain the unrelated policies preserved in 2.1.

| Change in 2.1 | Publication contract |
| --- | --- |
| Bootstrap before dispatch | An explicit configuration interview/approval now precedes every orchestrated worker, including discovery/research, and every direct external LLM API call. The current coordinating chat may perform safe local planning/capability reads needed to ask, without being retroactively blocked. Ask one question at a time where supported. New runs reconcile then explicitly reconfirm prior settings; same-run continuation/handoff retains valid authority without per-tool-call questioning. |
| Exact model and reasoning choices | Ask allowed providers/families and exact supported model IDs, defaults and coordinator/execution/review/integration/deployment overrides as applicable, and approved fallbacks. Ask minimum/default/maximum reasoning for each model and validate only on that provider/model's verified categorical order. Fixed/unsupported reasoning is explicitly operator-accepted `N/A / not configurable`; no fabricated scales, hardcoded model versions or silent defaults. Unselectable/unprovable actual settings block autonomous dispatch claiming those controls; exact approved assisted configuration needs evidence before effects. |
| Explicit external consent | Ask even when disabled; distinguish Copilot-managed requests from direct endpoints. Direct external LLM calls default **DENIED** until provider/endpoint, model, purpose, permissible data categories, secure credential reference (never key value), and budget are approved. Unknown consent blocks affected calls, not safe local planning. Never send secret/private repository/user data merely to probe capability/pricing. New provider/scope or expanded limits requires renewed approval, not repeated per-call asking within valid scope. |
| Aggregate budget and measured limits | Require an explicit aggregate run cap/units, native/external allocations and appropriate worker/task/provider subcaps, concurrency, retries/replacements and stop/escalation policy. Missing is not unlimited; deliberately uncapped scope needs explicit opt-in with risk acknowledgment. Keep incomparable unit ledgers separate under the authoritative run view; do not invent credit/token/currency equivalence or accurate money enforcement without price/usage evidence. Approved fallbacks must fit reasoning, consent and remaining budgets, with no silent more-expensive switch. |
| One authority, safe reservations | `POLICY` owns approved settings/version, operator/source/time and ledger ownership (or the linked authoritative existing ledger); `CAPABILITIES` supplies host/model/reasoning/price/usage evidence; `PROJECT_STATE` points to the active run/approval/ledger. Descendants inherit/tighten only. Reserve atomically through actual supported coordination, or serialize coordinator/manual reservations before dispatch. Markdown is not an atomic lock. Preserve usage, held unknown charges and remaining amounts through retries/replay/replacements; reconcile actual charges/effects before reallocation. |
| Lifecycle integration | `run_policy_ref`, `effective_config`, and `budget_reservation` appear in bootstrap, runtime core, capability discovery, assignment YAML/readiness/dispatch, worker results/operations, manual launch, deployment/evaluation, recovery and handoff. Existing workers are inventoried and migrated prospectively, not orphaned or given fresh budgets. Cap, approval, support or uncertainty violations block new affected work; they do not automatically kill stateful operations. Escalation needs explicit authority. |
| Documentation paths and reference | The current layout keeps only the README, benefits and getting-started guide in `docs/`. Protocol references live in root-level `protocol/`, operating guidance in `operations/`, and this review in `reference/`. [RUN_CONFIGURATION.md](../protocol/RUN_CONFIGURATION.md) supplies questionnaire/examples/reference, not a competing generated `RUN_CONFIG` store. Source launch prompts now obtain approval before discovery workers. |

These changes specify required policy and evidence. They do not install host controls, a live configuration, a ledger, a scheduler or an orchestration setup. Capability status and verified enforcement must remain distinct from instructional gates.

The original pack already covers evidence, durable checkpoints, stale assignments, architecture changes, permissions, and interrupted deployments. Its main weakness is that some desired behavior remains optional or loosely specified. In particular, it explicitly allows the orchestrator to execute work directly and starts concurrency at two workers. Those defaults conflict with the requested operating model.

The reported stalls have not been reproduced. The attachment contains instructions, not the installed Copilot configuration, runtime logs, task registry, or running-job records. The findings below establish weaknesses in the instructions; they do not establish which weakness or runtime failure caused a particular incident.

## 1. Findings and changes

Original section references below refer to the uploaded version reviewed for 2.0, not to the relocated 2.1 section numbering. The 2.1 additions above apply alongside these retained policies.

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
| Main orchestrator | Objective, current constraints, approved run/settings/ledger pointers, readiness, budget reservation, dispatch, priorities, ownership, evidence assessment, status and handover. | Safe local interview preparation before approval; then short bounded coordination operations within approved scope. No long execution, heavy investigation, build/test commands, deployment applies, or background jobs. |
| Execution worker | A bounded research or implementation assignment and the actual operations it starts. | Approved `run_policy_ref`, actual evidenced `effective_config`, `budget_reservation`, usage/uncertainty, accessible artifacts, current assignment, actual process/provider identifiers, progress evidence and recovery method. |
| Review or integration worker | Candidate inspection, applicable checks, conflict resolution and authorized integration execution. | Validate the submitted candidate; coordinate writes to each shared branch or target. |
| Separate observer or supervisor, if adopted | Observe coordination liveness and initiate supported recovery. | Must actually run independently and use supported controls. It must not become a competing dispatcher. |

Long work needs both delegation and a verified way for coordination to continue. If a runtime cannot provide that, use independently opened worker sessions and the exact prepared handoff. This limitation does not permit the main coordinator to take over execution.

Concurrency should serve the dependency path to a verified result within approved settings, consent, concurrency and aggregate reserved budget. Idle capacity is justified when no eligible work exists, an approval/support/budget gate or real shared limit binds, or the extra work would increase delay. It is not justified merely because another unrelated worker has not finished. When review accumulates, shift capacity to review and integration and throttle the contributing workstream; do not freeze independent work by default.

## 3. Queue and restart behavior

The revised guide distinguishes intent waiting in a durable backlog, a message waiting for delivery, a dispatch with uncertain acknowledgement, a running operation, and a result waiting for acceptance. Each needs a different action.

A useful diagnostic is: **Which task is waiting, what is it waiting for, which actor can release it, and what evidence was last observed?** A heartbeat demonstrates liveness. It does not demonstrate useful progress. A lack of new artifacts does not prove a legitimate long operation is dead.

Repeatedly adding the same prompt is not a recovery procedure. Capture unsent intent, stop duplicate dispatch, inspect existing handles and effects, and transfer ownership before allowing a replacement to issue conflicting work. When a job's outcome is unknown, monitoring and reconciliation precede replay.

The requested connection-recovery path is now explicit:

1. Preserve the original queued instructions and their IDs, causal order, target and known delivery state, alongside current task, candidate and job records. Reconcile captured cancellations and changed constraints before treating other work as unaffected or issuing new effects.
2. Isolate the affected connection and any tasks or resources affected by those controls, including work on other connections. Have an independent recovery owner use the verified reconnect or connection-restart control. Do not equate connection restart with cancellation of execution.
3. Establish the current connection generation and coordination ownership; inspect surviving jobs, results, approved run/settings/consent, actual charges and outstanding reservations before redispatch.
4. Reconcile what was delivered, applied, superseded, started or completed. Apply newer cancellations and changed constraints to pending work before replaying an obsolete action.
5. Restore valid unapplied instructions in bounded chunks with acknowledgement and progress checks. Release newly eligible tasks in parallel only under valid run approval and reservations; replay retains consumption and held unknown charges. Reconcile an uncertain delivery rather than blindly sending it again.

Full automation requires actual access to pending input before it is lost, supported reconnect controls, and an independent recovery actor. If unsent UI text is inaccessible, the setup must provide the actual manual preservation and restore steps. It cannot reconstruct uncaptured messages or promise exactly-once execution merely by resending them. The main instructions specify the persistent journal and replay checks; the operator guide supplies the recovery prompt.

The operating guide includes the relevant distinctions from the [official Copilot chat queue documentation](https://code.visualstudio.com/docs/chat/chat-overview#send-messages-while-a-request-is-running). The revised capability check also distinguishes [persistent session orchestration](https://code.visualstudio.com/docs/agents/run/sessions/manage-sessions#orchestrate-sessions-from-agent-host-sessions) from [subagent invocation](https://code.visualstudio.com/docs/agents/run/subagents). The 2.0 review records these documentation references as checked on 6 September 2026; this is historical evidence, not a fresh external verification for 2.1. The actual installed environment still requires inspection within the approved run scope.

An inactive coordinator cannot run its own monitoring loop. Unattended recovery requires another active session or a separately running, verified supervisor. A supported host or provider defect may still require runtime troubleshooting; the instruction revision cannot guarantee that restarting Copilot will never be necessary.

## 4. Apply the revision without resetting the project

1. Use the single [pinned in-place upgrade prompt](../docs/GETTING_STARTED.md#upgrade-without-resetting-live-work) in the existing project; follow its independent read-only recovery warning before using a new session when the old path only queues. Start with known compact state and public references, not a clone/attachment prerequisite or broad preapproval inventory. This is not an automatic new run: retain valid same-run approval and obtain only genuinely missing/changed decisions. An explicitly requested new run reconciles/reconfirms settings under the [configuration interview](../protocol/RUN_CONFIGURATION.md).
2. Only after approval and atomic or serialized reservation, have execution workers inspect and update the existing generated instructions and role configuration. Preserve task identities, current assignments, useful work, decisions, authority, failed-attempt history, job handles, actual usage and outstanding/unknown charges.
3. Compare and merge the changes into active host-supported entrypoints, generated runtime/session protocol and live prompt/agent copies, not just cached references. Remove conflicting rules: discovery before approval, silent settings/consent/budget defaults, resets, default two-worker cap, coordinator execution fallback, wait-for-all barriers, chat scheduling, mandatory READY/IDLE handshakes, persistence after send, and timeout-driven stale/revoke/redispatch. Preserve valid customizations and old versions/provenance; hold only unresolved conflicting writes. Reuse POLICY/CAPABILITIES/PROJECT_STATE and ledger boundaries; do not append a competing protocol or RUN_CONFIG store.
4. Reconcile live workers before switching coordination ownership. Adopt unaffected assignments explicitly; change only assignments invalidated by scope, ownership, contracts or evidence.
5. Exercise the relevant activation scenarios in the main and deployment instructions using harmless representative work within approved settings, consent and budget. Include exact model/reasoning or accepted fixed `N/A`, external-denial, reservation/oversubscription, same-run recovery and manual-setting evidence cases. Harmless discovery/drills do not waive the approval gate.
6. Record whether each control is documented, configured, exercised, or verified in the intended runtime. Continue within existing authority and known limits, observing actual runtime permissions. Hold new affected work on approval/support/cap/uncertainty violations and escalate only under explicit authority, without automatically killing stateful operations.

For a new project, use the first-session prompt in the operator guide. Do not load this review into every worker session; it explains the changes and is not a fourth runtime protocol.

## 5. Verification and limits

The deliverables are revised instructions. They do not include an installed Copilot configuration, running supervisor, deployed scheduler, or measured performance improvement in the user's environment.

Activation must demonstrate the practical outcomes: the coordinator remains responsive while a worker runs a long job; independent ready work starts without a global barrier; queue congestion receives a specific diagnosis; a lost launch acknowledgement does not cause duplicate execution; a backed-up queue can be restored after connection restart without blindly repeating applied work; stale results are rejected; and a replacement recovers actual work without resetting the budget or current requirements. Replay and deduplication results apply only to the actual adapter and scenarios exercised.

For 2.1, activation must also demonstrate approval before discovery/research workers, evidenced actual model/reasoning controls or truthful assisted/unavailable status, explicit external consent boundaries, and run-budget reservations that cannot oversubscribe the supported ledger. Results and operations must carry the applied settings, usage and uncertainty rather than requested values alone. Recovery must retain charges/reservations and reconcile them before reallocation. These are required future runtime checks, not claims that publication of this document executed them.

Evaluate improvement through elapsed time to accepted, integrated outcomes, time ready work waits, coordinator responsiveness, review backlog age, repeated failure signatures, and recovery incidents. Compare similar work where evidence permits. More active sessions alone is not evidence of faster delivery.

## 6. Files

| File | Use |
| --- | --- |
| [BOOTSTRAP.md](../protocol/BOOTSTRAP.md) | Small coordinator opening entry with first-response, bounded interview and return-control rules. |
| [FIRST_SESSION_AND_ORCHESTRATION.md](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md) | Build or update the project-specific orchestration layer and its verified controls. |
| [OPERATOR_GUIDE.md](../operations/OPERATOR_GUIDE.md) | Start, interview/approve, steer, inspect, migrate and recover the working setup. |
| [DEPLOYMENT_BUILD_INSTRUCTIONS.md](../protocol/DEPLOYMENT_BUILD_INSTRUCTIONS.md) | Delegate and implement the actual build, release and recovery path with parallel preparation under the same approved run. |
| [REVIEW_AND_CHANGES.md](REVIEW_AND_CHANGES.md) | Findings, rationale, migration overview and validation boundaries. |
| [RUN_CONFIGURATION.md](../protocol/RUN_CONFIGURATION.md) | Questionnaire, compact examples and field reference; not a generated live configuration or separate authority store. |

### Historical 2.0 local artifact verification

All four Markdown deliverables were checked for existence, UTF-8 readability, balanced fenced code blocks, resolving relative Markdown file links, revision 2.0 identification, and the presence of the three required core filenames. The superseded exact defaults “Begin with at most two concurrent workers” and “execute directly or delegate” are absent. The final ZIP was checked for CRC integrity, exactly these four files at its root, and byte-for-byte equality with the final Markdown files. No GitHub Copilot runtime, agent connection, queue replay, or deployment execution was tested; no runnable user environment was supplied.

The preceding paragraph is the **preserved historical 2.0 verification statement**. Its “final ZIP” and byte-equality claims concern the 2.0 artifacts only. The immutable source ZIP does not contain the relocated, revised 2.1 files and must not be described as byte-identical to them.

### Revision 2.1 verification boundary

This follow-up changes publication documents and specifies activation checks; it does not make external LLM calls, install tools, set up orchestration, or execute deployment. Document-level checks cannot establish enforced host controls, accurate cost limits, or runtime model/reasoning selection. Retain any future activation evidence with its actual run, host, settings and usage limitations rather than carrying 2.0 claims forward as 2.1 guarantees.
