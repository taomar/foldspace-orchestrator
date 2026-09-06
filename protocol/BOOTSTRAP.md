# FoldSpace bootstrap

**Revision: 2.1.6 - 6 September 2026**

Target repository; no clone/attachment. No runtime/host repair.

## First response

Acknowledge intent/run mode; reuse valid answers and
[prestaged inputs](RUN_CONFIGURATION.md#optional-prestaged-interview-inputs).
Resolve gaps; validate/summarize unapproved inputs for final approval.

"Continue pending": derive tasks/acceptance from compact state/context; clarify
ambiguity, don't invent/rewrite tasks. Ask missing record access/location.

## Advance or wait

**At most one unanswered question outstanding, not one answer per response.**
Reconcile answers (including synchronous question-tool results), steering and
delivery/completion; take the next bounded read, supported question,
review/final approval request or approved action. No extra "continue" or
status-only exit. Ask the next question. Missing approval allows clarification.
Workers execute valid assignments, not interviews.

Use context or one known-short targeted read per missing fact; advance from it.
No scans, catalogs, chained research, polling or full-job waits.
Public reference GETs are not inference; send no private data.

Yield for real waits after eligible steps: phase, last action, gap/owner and
actual resume event/manual action. Host lifecycle: suspended isn't completed;
answered isn't waiting. Request normal permissions. No self-wake/loops.

Persist intent/results outside the queue before notifying. "Sent" is not receipt/
pickup. Before unattended yield prove idle-resume; arm independent observation
with finite pickup/recovery limits and alternate alert/control, or use an accepted
operator handoff. Preserve queue/state. Missing ACK/errors: quarantine new assignments, retain owners/
reservations; reconcile jobs/results before retry. No automatic revoke/reassign.
Backlog stays in ledger, not chat. Default one active assignment/worker, at most
one unacked dispatch. No new tasks to busy/uncertain lanes; allow supported
answers/controls. READY/IDLE isn't wake proof. See
[safety contract](FIRST_SESSION_AND_ORCHESTRATION.md#idle-delivery-safety-contract).

## Mandatory approval

Before any worker (including discovery/recovery) or direct external LLM call:
approve providers/families/exact IDs, role defaults/fallbacks; per-model
minimum/default/maximum in verified order or verified accepted N/A; external
consent; aggregate caps/units/allocations, concurrency, retries/stop; final approval.
External calls default denied. No silent defaults, conversions, unlimited
budget or guessed N/A. Uncapped scope needs explicit opt-in/risk acceptance.
Verify controls or hold affected work for an approved demonstrable alternative.

## Approved setup

Reserve task/resources/budget before send; use verified nonblocking workers or
approved manual handoff. Pin a commit, preview conflicts, copy linked references/
LICENSE without overwrites; adapt instructions/state separately, record
provenance/hashes, verify discovery. Continue the objective.

New runs reconfirm without erasing owners, effects, authority, exclusions,
charges/reservations. Same-run approval survives; descendants inherit/tighten
parent limits. Never recover through the blocked queue.

## Source map

Reuse pinned copies; multiple `main` GETs aren't an atomic snapshot.

- [Protocol](https://raw.githubusercontent.com/taomar/foldspace-orchestrator/main/protocol/FIRST_SESSION_AND_ORCHESTRATION.md)
- [Run configuration](https://raw.githubusercontent.com/taomar/foldspace-orchestrator/main/protocol/RUN_CONFIGURATION.md)
- [Operator/recovery](https://raw.githubusercontent.com/taomar/foldspace-orchestrator/main/operations/OPERATOR_GUIDE.md)
- [Deployment](https://raw.githubusercontent.com/taomar/foldspace-orchestrator/main/protocol/DEPLOYMENT_BUILD_INSTRUCTIONS.md)
- [History](https://raw.githubusercontent.com/taomar/foldspace-orchestrator/main/reference/REVIEW_AND_CHANGES.md)
- [MIT license](https://raw.githubusercontent.com/taomar/foldspace-orchestrator/main/LICENSE)
