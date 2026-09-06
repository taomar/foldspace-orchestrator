# Getting started with FoldSpace Orchestrator

**Open your target project and paste the prompt below.** You do not need to
clone this repository, download a ZIP, attach documents, or run a copy script.
Copilot retrieves the public references and, after your run approval, assigns
a worker to localize them safely, then routes your actual build objective to
its responsible executor.

FoldSpace is a documentation protocol, not an installed runtime. Fetching and
writing depend on the tools and permissions available in your Copilot host.

**Already using FoldSpace?** Use the
[in-place upgrade prompt](#upgrade-without-resetting-live-work) instead of
starting over. It preserves existing work and valid same-run approval.

[Overview](README.md) | [Benefits](BENEFITS.md) |
[Operator guide](../operations/OPERATOR_GUIDE.md) | [Prompt examples](../operations/EXAMPLES.md)

## Contents

1. [Open the target project](#prerequisites).
2. [Paste one bootstrap prompt and approve the run](#send-a-bootstrap-prompt).
3. [Let Copilot localize what the project needs](#make-references-available-without-overwriting-instructions).
4. [Complete a real bounded task](#a-bounded-worked-example) and [continue safely](#fresh-session-discovery-and-continuation).
5. [Upgrade an existing setup without resetting live work](#upgrade-without-resetting-live-work).

## Prerequisites

Open the repository where you want to build in your Copilot host. Supply a
concrete outcome and its constraints. That is the **target repository**;
FoldSpace's GitHub repository is only the public reference source.

The supported automatic path needs public URL retrieval and authorized target
workspace writes. Use normal host permission prompts if required. No package,
FoldSpace checkout, or assumed instruction-entrypoint filename is required.

## Send a bootstrap prompt

Replace the bracketed fields and paste this **whole prompt** into the target
project's Copilot session. It is ordinary language, not a native slash command.
Optionally paste known interview answers underneath using the
[prestaging checklist and copy/paste template](../protocol/RUN_CONFIGURATION.md#optional-prestaged-interview-inputs).
Leave unknowns unknown; no attachment or extra file is needed, and these inputs
do not grant final run approval.

```text
Use FoldSpace Orchestrator in this target repository. Do not ask me to clone
the FoldSpace repo, download a ZIP, attach its files, or run a copy script.
Read only this compact public Markdown entry first:
https://raw.githubusercontent.com/taomar/foldspace-orchestrator/main/protocol/BOOTSTRAP.md
Use its source map to retrieve detailed references only when needed.

Project mode: [new project / new run in this project / same-run continuation]
Outcome: [what I want built or changed, or continue recorded pending work]
Acceptance or pending record: [criteria, known state/tracker path/IDs, or unknown]
Scope and authority: [allowed actions/files, compatibility, excluded effects]
Known ongoing work: [owners, changes, operations, or explicitly unknown]

Remain coordinator across every message, synchronous answer, event, continuation,
reconnect/compaction and approval. User intent does not change your role.
Before tools/skills or investigation, answer from held evidence/brief known
concepts or one compact coordination-state read, otherwise record and route
to the existing owner first, an eligible executor or a bounded sub-orchestrator.
No source/domain-docs research or implementation, even one quick call/edit.
Ask only a real decision or exact supported control gap; executors execute.
Acknowledge intent/run mode and reuse valid supplied/prestaged answers.
Keep at most one unanswered question outstanding. Reconcile each answer,
including one returned by a question tool, then take the next admitted coordination
read, question, configuration review/final approval request or dispatch.
Do not require "continue" between answers or end with only "recorded/blocked".
For pending work, derive candidates/acceptance from known compact records;
ask focused selection or exact record access/location if missing, not a new backlog.
Follow actual host question lifecycle. Yield for real waits with exact gap,
owner and supported event/manual action, not merely because a tool answered.
Use only compact authoritative coordination/capability metadata or needed
approved bootstrap/configuration references, not chained investigation.
Missing model choices mean exact questions/access gaps, not unapproved workers.
No private project/user data may be uploaded or sent to external inference.
If URL access or writes are unavailable, request normal host permission or
report the exact gap; never claim a file was fetched or localized when it was not.

Before any worker, including setup/localization/discovery, or direct external
LLM call, complete the mandatory interview and obtain my final approval:
exact supported providers/models, role defaults and fallbacks; per-model
minimum/maximum and default within supported bounds or accepted N/A;
external consent; aggregate budget/units, allocations, concurrency,
retries/replacements, reservations, and stopping/escalation rules.
No silent defaults: external calls begin denied; missing budget is not unlimited.
For same-run continuation retain valid approvals, owners, charges and reservations.

After approval, assign a bounded setup worker using demonstrated controls.
Resolve one source commit, preview local paths and conflicts, and fetch the
required reference files and LICENSE from that same revision without cloning.
Save versioned reference copies, preserve their layout and source provenance,
and reuse matching existing copies rather than overwrite them.
Have the setup worker adapt active host-supported root/child coordinator and
executor entrypoints, runtime core, role packets and native tool profiles only
where supported, separately from reference copies and policy/capability/state.
Verify loaded roles/profiles in fresh target root/child and spawned executor;
generic execution-capable tools mean instructional, not enforced boundaries.
Do not invent host config formats or override higher-priority instructions.
Preserve user edits, live owners/operations, queued intent and budget exposure.

Verify discovery and the handoff, then route my actual outcome to its existing
or eligible new owner with the project's tooling and acceptance criteria.
Do not stop at downloading documents or expand deployment/publication authority.
Keep the coordinator available; use an approved manual worker path if native
dispatch is unavailable. Reconcile unknown effects before retrying.
Before depending on later messages, publish durable intent/results outside
the chat queue and prove receiver receipt/pickup after the coordinator idles.
Arm independent observation with finite recovery authority/allowance and
alternate alert/control, or establish an accepted operator-carried handoff.
Do not count "sent" as receipt or recover by piling on "continue" messages.
```

### Answer the interview before dispatch

Expect one outstanding unanswered question, not a silent full-repository audit.
After you answer, the coordinator advances to the next useful question/read or
configuration review; you do not need to say "continue" after each answer.
It reuses valid prestaged answers rather than replaying the full questionnaire.
Complete unapproved inputs still require validation, summary and final approval.

A real missing input/evidence/capability has an exact unblocker and next actor.
A host question tool may suspend the request; use its actual answer/cancel
control rather than a message queued behind it. Once the tool returns your
answer, that question is no longer waiting. A completed "recorded, blocked
until..." acknowledgement without the next useful question is not correct
progression. No model IDs, reasoning levels or spending caps are preselected.

| The coordinator asks for... | You explicitly approve... |
|---|---|
| Models | Providers/families, exact supported IDs, default and role overrides, approved fallbacks |
| Reasoning, for each model | Minimum/maximum and a default within those bounds on that model's verified supported order; accepted N/A for fixed/nonconfigurable reasoning |
| Direct external LLM calls | Disabled, or provider/endpoint, models, purpose, permitted data, secure credential references (never keys), and budget |
| Budget and execution | Aggregate cap and real units, native/external allocations and relevant subcaps, concurrency, retries/replacements, stop/escalation policy |
| Later delivery and recovery, where needed | Unattended or operator-carried mode, observer/operator, finite receipt/pickup windows, permitted recovery actions/attempts and allocation within existing limits |
| Final confirmation | The resolved run policy/version, approval source/time, and disclosed capability limits |

Reading public GitHub documentation is not an external LLM inference call.
Native Copilot permission does not authorize direct external inference.
Missing settings block affected dispatch; uncapped scope requires deliberate
opt-in and risk acknowledgment. Do not invent conversions between tokens,
credits and money. Reserve before concurrent dispatch, and retain consumption
and reservations across children, retries and replacements.

The complete questionnaire is in the
[run-configuration reference](../protocol/RUN_CONFIGURATION.md), available to
Copilot through the entry's full-URL source map.

## Obtain the documentation pack

**Copilot obtains the needed references; you do not prepare a local pack.**
The first read is the small
[public bootstrap body](https://raw.githubusercontent.com/taomar/foldspace-orchestrator/main/protocol/BOOTSTRAP.md).
Its [source map](../protocol/BOOTSTRAP.md#source-map) contains the full public
Markdown URLs for the protocol, configuration, operator guide, deployment
reference, history and license. Retrieval is on demand, not one large opening
context load.

Before saving reference copies, the approved setup worker resolves one source
commit and retrieves all selected files at that revision. It records the
source identity and does not describe several moving `main` reads as an atomic
snapshot. If the host cannot establish a consistent revision, it reports that
limitation rather than silently mixing versions.

## Make references available without overwriting instructions

After approval, Copilot delegates the following work to a bounded setup worker:

1. **Preview the change.** Identify the target repository, existing instruction
   entrypoints, dirty files, active owners and proposed reference/adaptation
   paths. Reuse project conventions and report conflicts.
2. **Save necessary references.** Copy the linked reference closure and MIT
   license from one source revision, preserving their folder/link layout.
   A suggested target location is `docs\reference\foldspace\<commit>`.
   Verify and reuse matching copies; do not overwrite conflicting content.
3. **Localize the operating setup.** Merge persistent role/action admission into
   the active core, host-supported entrypoint and root/child/executor role
   packets; apply native tool profiles only where supported and verified.
   Generic tools require an instructional-boundary disclosure. Reuse existing
   requirements, policy, capabilities, state and task tracking. Reference files
   are not live project state and must not replace local customizations.
4. **Verify and continue.** Record source URLs/commit, document revision, local
   paths and hashes. Establish loaded roles/core/profiles in fresh target root
   and child coordinators and a spawned executor with non-destructive checks.
   Return the next ready assignment; the coordinator routes the build goal
   and executors perform it under existing approval and budget.

The suggested destination is inside **your target project**, not a new folder
in this documentation repository. Full mechanics and the standard reference
set are owned by the
[localization contract](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md#localize-github-references-without-cloning).

If network or workspace writes are blocked, use normal host permissions or
report the exact unavailable capability. Manual transfer is an exceptional
assisted fallback, not a prerequisite. Do not bypass access controls or claim
activation merely because a URL was mentioned or files were copied.

## Choose the project path

### New project

State the intended product, acceptance criteria and allowed actions. Establish
that project's own state without importing unrelated owners or assumptions.
Reconcile any genuinely shared resources before conflicting effects.

### Existing project

A **new run in the same project** explicitly reconfirms settings while
preserving requirements, tasks, owners, operations, resource exclusions,
pending steering, evidence and budget exposure. It does not stop old work.
"Continue pending work" tells the coordinator to use supplied context or a
known compact authoritative state/checkpoint/task index. It derives recorded
candidates and acceptance, asks only material selection/gaps, or asks where
the record is/access to it if unavailable. You need not rewrite recorded tasks;
no broad scan or discovery worker starts before approval.

A **same-run continuation** restores valid policy, pinned local references and
the ledger; it does not re-interview every call or silently refresh source
versions. Expanded scope/limits need approval. A fresh session is not
necessarily a new run.

## Record actual host capabilities

Record relevant controls as **Verified automatic**, **Assisted**,
**Unavailable**, or **Not checked**, with evidence. This includes reference
retrieval and writes, instruction discovery, actual model/reasoning selection,
budget accounting, nonblocking dispatch and result return.

The [role/action contract](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md#persistent-role-and-action-admission)
also needs active root/child/executor discovery and tool-profile evidence.
Unsupported allowlists or unscoped generic tools mean an instructional boundary,
not enforced prevention. Tool filtering cannot prevent all long reasoning or
host stalls. Record conflicting higher-priority defaults and supported assisted
steps instead of claiming Markdown overrides the host.

If required controls cannot be applied/proved, hold affected autonomous work
or use an explicitly approved demonstrable manual path. A document describing
a feature does not install it. See the [runtime checks](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md#4-verify-the-runtime-before-promising-orchestration).

### Establish idle pickup before unattended work

After run approval, the setup worker uses an approved manual return route if
automatic delivery is still unverified. It demonstrates an identified result
reaching the coordinator **after a response ends**, with receiver evidence and
useful pickup, not just a successful send while the coordinator is active.
Test closed-session reattachment only if needed and safe; no preapproval worker
or destructive host restart is required to begin the interview.

The coordinator must name an actually armed independent observer or explicitly
accepted operator, durable intent/result location, finite receipt/pickup windows,
alternate alert/resume controls and recovery allowance. Register observation,
then recheck compact pending state before yielding. If automatic coverage is
unavailable, disclose the gap and use the accepted operator-carried path rather
than leaving unattended dependent work stranded. No polling loop or extra model
agent is needed where an existing runner or manual route suffices.

If delivery fails, preserve accessible queue text before any disruptive UI action,
reconcile existing work/effects, and resume through independent controls or an
authorized ownership handoff. Follow the
[operator procedure](../operations/OPERATOR_GUIDE.md#prevent-stranded-work-and-recover-missed-delivery).
Reading these instructions does not install the observer or fix the host queue.

## Understand the project records

`POLICY` owns approvals/settings and the ledger or its owning reference;
`CAPABILITIES` owns supporting evidence; `PROJECT_STATE` points to the current
run, owners, ledger and next action. Existing equivalents remain authoritative.

Suggested `docs/ai/*` files are **target-project outputs, not preinstalled pack
assets**. Keep pinned reference copies separate from those adapted records.
Keep private operational material out of public commits and retain retrievable
work, not just summaries. See [project memory](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md#5-install-small-authoritative-project-memory).

## A bounded worked example

**Outcome:** correct one setup-guide section after a configuration option changed.

First, the approved setup assignment localizes the reference set and returns
its source commit, local paths, instruction-discovery evidence and limitations.
It does not claim the documentation change itself is complete.

The next assignment is the actual work:

| Contract item | Bounded example |
|---|---|
| Identity and owner | `DOC-SETUP-1`, version `1`, registered dispatch/coordinator, named worker and assigned workspace |
| Inputs and dependency | Current setup guide and agreed option behavior; wait if the behavior is unsettled |
| Write scope and authority | Only the identified guide section; no code edits, external inference, deployment or publication |
| Run controls | Approved policy/model/reasoning, parent budget reservation, operator-approved attempt and stop limits |
| Acceptance | Guidance matches the option, links resolve, unrelated content is preserved |
| Return and stop | Identified patch/commit, criterion-specific evidence, actual settings/usage, uncertainty and next action; return a blocker if code changes or conflicting ownership are needed |

Review the identified candidate and disclose review-independence limits.
An authorized integration worker checks the combined result; changed candidates
need renewed evidence. The coordinator records acceptance against the actual
criteria. Submission, integration, acceptance and publication are distinct.
Unrelated eligible work need not wait for this assignment.

## Manual worker fallback

If native nonblocking launch is unavailable, the coordinator prepares the
complete approved packet with source URLs or localized paths, effective
settings, reservation, workspace/scope, stop conditions and return channel.

The operator opens a separate worker through verified local steps. The worker
confirms ownership and dependencies, applies/proves approved settings, owns
its operations/checkpoints and returns an identified result. The operator
carries acknowledgements/results back only if the host requires it.

A prepared packet is not a running worker. If no adequate execution path
exists, hold affected work; do not have the coordinator silently absorb it.
See [worker launch and return fields](../operations/OPERATOR_GUIDE.md#5-launch-workers-with-an-explicit-task-and-job-handoff).

## Fresh-session discovery and continuation

Resume from compact project-native instructions/state and the explicit
assignment, not another full remote pack load. Identify persistent role, current
owners, approval, ledger and checkpoint before admitting the next action.
Coordinators answer from compact evidence or route existing-owner-first;
continuation never grants source investigation or implementation. Executors
continue their approved assignments without restarting the interview.

Preserve task ownership, exclusions, attempts, charges and reservations across
new sessions and runs. A surviving migration blocks conflicting writes, not
unrelated eligible work. Transfer ownership only through the existing safe
handover/fencing rules; silence does not prove termination.

Capture accessible pending intent before disruption. Reconcile uncertain
delivery, effects and charges before replay or reallocation; do not invent
inaccessible messages. Use the [recovery prompts](../operations/EXAMPLES.md#recover-context-without-reclaiming-ownership-blindly)
only through a responsive, authorized route.

## Upgrade without resetting live work

Open your **existing target project** in a responsive Copilot session. This is
an in-place instruction migration, not a new project or an automatic new run.
No FoldSpace clone, Git commands, ZIP, manual copy, attachments or new project
are needed in the supported URL-first path. This is a **Copilot upgrade prompt
only**, not an executable updater; no PowerShell/Bash script or runtime service
is supplied or required.

**If the current session only queues messages, do not paste this prompt into
that queue.** Preserve accessible pending text and attachments first. Use the
host's actual controls to open an independent, responsive session in the same
project. Start it **read-only** to reconcile existing owners and operations;
establish a safe ownership handoff before conflicting writes. Opening another
session does not fence the old actor or prove it stopped. Do not broadly
restart, kill jobs or clear queues. See the
[independent recovery procedure](../operations/OPERATOR_GUIDE.md#prevent-stranded-work-and-recover-missed-delivery).

Paste the **whole prompt** below into that responsive session. It targets
**revision 2.1.6 at commit `7fedb7129e9692b115daf2c4593456ed6abb1bbe`**,
not an evergreen "latest" release. The pinned bootstrap's source map contains
`/main/` URLs; every companion retrieval must use the same commit instead.

```text
Upgrade this project's existing FoldSpace setup in place to revision 2.1.6.
Read only this pinned compact public Markdown entry first:
https://raw.githubusercontent.com/taomar/foldspace-orchestrator/7fedb7129e9692b115daf2c4593456ed6abb1bbe/protocol/BOOTSTRAP.md
Use its source map on demand, replacing /main/ with
/7fedb7129e9692b115daf2c4593456ed6abb1bbe/ for EVERY companion download,
including linked references and LICENSE. Keep all source reads at that commit;
do not mix moving main content or preload the entire pack. No clone, Git
commands, ZIP, manual copy, attachments or new project are required.
Use this Copilot-only instruction migration; do not add an executable updater,
scripts, runtime enforcement, watchdogs, dependencies, CI or agent frameworks.

Treat this as instruction migration within the current run, not automatic
new-run approval. Begin with bounded public reads and safe known-state
preparation in this current chat. Do not send private project/user data to
public services. Identify the installed source revision and reference paths,
the actual host-supported project instruction entrypoint, generated runtime
core/session protocol, and authoritative policy, state, task records and ledger.
Use known compact records; ask for exact missing locations/access, not a broad
preapproval discovery scan. Do not assume a universal instruction filename.

Preserve requirements, task IDs, pending work, active owners/assignments,
operations and live write/resource exclusions, queued intent, customizations
and unrelated dirty edits. Preserve valid current approval, exact model/role/
fallback and per-model reasoning choices, external-call consent, usage,
reservations, unknown charges and remaining limits in their approved units.
A new revision does not stop old jobs, free resources, authorize external
calls, reset budgets or cancel anything. Do not assume coordination ownership;
reconcile old actors/operations read-only and safely hand off ownership before
conflicting writes. Do not create competing trackers or rewrite policy/state
wholesale.

Reuse valid same-run authority; do not repeat the interview for known approved
settings. Obtain only genuinely missing approval, materially changed policy/
scope or required new recovery-capability decisions. If I separately request
a new run, explicitly reconfirm its settings while preserving live state.
No worker, including setup/discovery/recovery, or direct external LLM call may
start before the applicable run approval; respect host permissions and scope.

Under valid approval and a reservation within remaining limits, assign a
bounded setup worker through demonstrated controls or an approved assisted
handoff. Compare installed sources and active instructions against the pinned
target before applying changes. Preview exact paths, changes and conflicts
within the approved write scope. Retain old reference bytes and prior active
instruction versions as rollback material/provenance; save new required
references separately, keeping their layout, LICENSE, URLs, revision, commit
and hashes. Reuse verified matching
copies and never silently overwrite conflicting references or instructions.
Deliberately merge/adapt the actual active project-native entrypoint, compact
runtime core/session protocol and conflicting live prompt/agent copies so old
rules do not override the upgrade. Preserve project conventions/customizations;
hold affected conflicting writes for resolution. Updating references alone
is not activation.

Apply the 2.1.6 rules at the existing policy boundaries. Supersede conflicting
old active rules, not merely append another policy or download new references:
Keep backlog in the durable authoritative task ledger under one current
coordinator or actual serialized writer; workers own operation/result records.
For NEW assignments, default one active assignment and at most one outstanding
unacknowledged assignment dispatch per worker, zero pending task backlog in chat.
Busy, dispatching, recovering, uncertain or resource-unavailable lanes receive
no additional task. Additional workers need independent ready work, isolation,
verified capacity and remaining approved aggregate budget, not unbounded spawning.
Answers, steering, cancellations/changed constraints, status/results and recovery
controls use demonstrated priority/control routes or exact assisted fallback.
Host tools may still queue internally; stopping chat does not prove jobs stopped.
READY_CHECK/READY are optional application markers, not built-in commands or
readiness guarantees. READY then IDLE is no proof of next receipt/wake, workspace
exclusivity or applied settings. A supported creation request may carry one
complete approved bounded assignment without a second readiness roundtrip.
Reconcile after reconnect/reload before new assignments; do not probe in loops.

Reuse task_id/assignment_version, coordinator_epoch, unique dispatch_id and
candidate/result identities. Reserve task/receiver/resources/budget and persist
the packet BEFORE send; worker validates current authority/workspace/settings
and records exact acceptance before effects. ACK receipt is observation, not
fencing. Keep task readiness, delivery and execution/results separate; accept
valid out-of-order start/result evidence without waiting for a missing ACK.
Missing ACK, errors or unexplained idle quarantine NEW assignments to the lane,
not task ownership/outcome. No automatic STALE/revoke, budget release, stateful
job cancellation, global freeze or redispatch once. Preserve original payloads,
attachments, work/checkpoints, receipts, handles, current controls and charges.
Inspect receiver events, actual jobs/effects/results and authoritative ownership.
Observe/adopt running work or consume completed results instead of duplicating.
Retry/replacement requires proven nonexecution with obsolete late start excluded,
or safe stop/surrender/fencing at the actual conflicting write boundary and
reconciled effects/charges. Ledger-only revocation is not fencing. Otherwise hold
that scope with its exact unresolved constraint; allow safe independent work.
Keep the logical task, recovered work, version/attempt history and consumed/held
reservations within approved remaining limits. Late obsolete ACK/start cannot
regain ownership; duplicate logical candidates/results/effects cannot integrate
twice under new notification IDs. No universal exactly-once claim.

Preserve the 2.1.4/2.1.5 progression and idle-pickup behavior:
After a received answer, including a question-tool result, reconcile it and
take the next permitted bounded read, focused question, approval request or
approved action; no status-only acknowledgement or extra "continue" is needed.
Keep at most one unanswered question open and respect actual host waits.
Derive pending tasks and acceptance from existing compact records, not a new
backlog. Reuse optional staged inputs; unapproved answers still need approval.
Persist intent and identified results outside the chat queue before notifying.
Successful sending is not receiver receipt/pickup. Before depending on later
delivery, require evidenced idle pickup and armed independent observation with
finite recovery authority/allowance and an alternate alert/control route, or
an explicitly accepted operator-carried handoff. Reconcile before replay;
do not append upgrade/recovery prompts to a stuck queue.
Apply pickup coverage to parent and workers. The observer must actually exist
outside the blocked path, or the operator must accept the exact handoff. Set
finite receipt/pickup windows from host/workload evidence and approved allowance,
not invented constants; genuine answers/new controls are not duplicate nudges.
Markdown does not install a watchdog or repair a host queue. Record incomplete
or unprovable controls and exact supported alternatives; no silent defaults,
permission bypass or global freeze of unrelated eligible work.

Report the source commit/revision, changed local paths and merged active rules.
Show that a fresh or continuing intended session discovers the updated
instructions without automatically acquiring ownership. Where feasible,
demonstrate the next bounded interview/worker transition under existing
approval and limits; label unsupported or unexercised controls honestly.
Keep old references and record rollback limits: restoring instruction files
does not undo external effects/data changes or reset task/budget state.
Then continue eligible pending project work under its existing authority.
Do not stop at downloading documents or imply deployment/publication consent.
```

For a future version, choose the intended release/commit, pin its full commit
ID and compare before applying. A newer remote source must not automatically
replace active local sources; retain the previous references and provenance.

Expect a concise migration report with the source identity, changed paths,
instruction-discovery evidence, next bounded transition, remaining capability
gaps and rollback limits. A downloaded pack alone is not a completed upgrade.
This guide supplies the prompt; it does not claim your Copilot host was
exercised. The [localization contract](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md#localize-github-references-without-cloning)
and [migration policy](../reference/REVIEW_AND_CHANGES.md#4-apply-the-revision-without-resetting-the-project)
own the detailed rules.

## If you get stuck

| Situation | Next action |
|---|---|
| Public URL retrieval or workspace writes are blocked | Request normal host permission or name the missing capability; manual transfer is exceptional, not a clone/attachment prerequisite |
| Copilot received page chrome, an error, or partial content | Retrieve the actual Markdown body through a supported route; do not save it as a successful reference copy |
| Existing references/instructions conflict | Compare and report the conflict, reuse only verified matches, and hold affected writes rather than overwrite |
| Reasoning or budget controls are unsupported | Disclose the limit; obtain accepted N/A where genuinely fixed or an approved measurable/explicitly uncapped budget choice as applicable; no invented settings or conversions |
| External inference is denied | Keep it blocked; this does not prohibit the user-approved public documentation GET or already-approved native work |
| Messages keep queuing after the coordinator goes idle | "Sent" is not receiver receipt. Use the established [independent pickup/recovery path](../operations/OPERATOR_GUIDE.md#prevent-stranded-work-and-recover-missed-delivery); preserve queued text before disruption, reconcile effects/results and do not append recovery prompts |

The canonical references own the detailed policy. This guide gets you from
one pasted URL-bearing prompt to a localized setup and actual project work.
