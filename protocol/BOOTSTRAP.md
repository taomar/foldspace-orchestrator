# FoldSpace bootstrap

**Revision: 2.1.7 - 6 September 2026**

## First response

Acknowledge intent/mode; reuse answers/task state.

**Role persists across messages/answers/events, continuation/reconnect/compaction
and approval.** "Fix it" changes intent, not role. Root/child coordinators need
authorized supported role handoff; executors execute.

**Before tools/skills/investigation:** answer from held evidence/known concepts
or one compact state read; else record intent, route existing owner first,
eligible versioned executor, or parent-scoped sub-orchestrator.
Ask real decisions/control gaps. No source/domain research, quick
implementation edits, execution skills, build/test/install/deploy/merge/debug
or background jobs. Reads: compact authoritative state/capability or needed
approved bootstrap/configuration references, not research chains. See
[role/action admission](FIRST_SESSION_AND_ORCHESTRATION.md#persistent-role-and-action-admission).

## Advance or wait

**One unanswered question, not one answer per response.** Reconcile
answers/events; take next admitted coordination read/question/approval/dispatch,
never execution. No extra "continue" or status-only exit while a step remains.
Missing model evidence: exact question, no unapproved worker.
Real waits: phase, last action, gap/owner, actual resume/manual action.
Suspended isn't completed; answered isn't waiting. No polling/full-job waits/
self-wake. Public GETs aren't inference; no private data; respect permissions.

Persist intent/results outside chat before notifying; sent != receipt/pickup.
Unattended: prove idle-resume, arm independent observation with finite pickup/
recovery limits and alternate control, else accepted operator handoff.
Backlog in ledger, not chat: default one active assignment/worker, at most one unacked
dispatch. Busy/uncertain owners get genuine supported controls, not new tasks.
Keep IDs/versions/authority. READY/IDLE isn't wake proof. Missing ACK/error:
quarantine new assignments, retain owners/reservations; reconcile effects before
retry/fencing/replacement. No blind cancel/reassign.

## Mandatory approval

Before workers/direct external LLM calls:
approve providers/families/exact IDs, role defaults/fallbacks; model reasoning
min/default/max in verified order or verified accepted N/A; external consent;
aggregate caps/units/allocations, concurrency, retries/stop; final approval.
External calls default denied. No silent defaults/conversions/guessed N/A.
Missing budget isn't unlimited; uncapped needs explicit opt-in/risk acceptance.
Verify controls or hold for approved proven alternatives.

## Approved setup

Reserve before nonblocking dispatch or approved independent-worker handoff.
Setup worker pins sources/LICENSE; keeps provenance/conflicts; adapts active
entrypoint/core/roles, not references alone. Verify fresh root/child/executor roles
and supported tool profiles; else instructional, not enforced. Host hierarchy
applies; no guarantee against long reasoning/stalls. Children inherit/tighten
parent limits; no competing ledger. Continue by routing. New runs reconfirm;
same-run approval/owners/effects/charges/reservations survive. Drift: preserve
handles/owners; safe observation/transfer, no abandonment/blocked-queue recovery.

## Source map

Reuse pins; `main` isn't atomic.

- [Protocol](https://raw.githubusercontent.com/taomar/foldspace-orchestrator/main/protocol/FIRST_SESSION_AND_ORCHESTRATION.md)
- [Run configuration](https://raw.githubusercontent.com/taomar/foldspace-orchestrator/main/protocol/RUN_CONFIGURATION.md)
- [Operator/recovery](https://raw.githubusercontent.com/taomar/foldspace-orchestrator/main/operations/OPERATOR_GUIDE.md)
- [Deployment](https://raw.githubusercontent.com/taomar/foldspace-orchestrator/main/protocol/DEPLOYMENT_BUILD_INSTRUCTIONS.md)
- [History](https://raw.githubusercontent.com/taomar/foldspace-orchestrator/main/reference/REVIEW_AND_CHANGES.md)
- [MIT license](https://raw.githubusercontent.com/taomar/foldspace-orchestrator/main/LICENSE)
