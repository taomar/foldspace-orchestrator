# FoldSpace bootstrap

**Revision: 2.1.5 - 6 September 2026**

Target repository; no clone/attachment. Fetch on demand.
No runtime installed or host repair promised.

## First response

Acknowledge intent/run mode; reuse valid answers and
[prestaged inputs](RUN_CONFIGURATION.md#optional-prestaged-interview-inputs).
Ask missing/conflicting/unsupported items; validate/summarize unapproved inputs, then
request final approval, not dispatch.

"Continue pending": derive candidates/acceptance from known compact state,
checkpoint/task index or context; clarify ambiguity, don't invent/rewrite tasks.
Missing record: ask location/access or an independent model/budget item.

## Advance or wait

**At most one unanswered question outstanding, not one answer per response.**
Reconcile answers (including synchronous question-tool results), steering and
delivery/completion; take the next bounded read, supported question,
review/final approval request or approved action. No extra "continue" or
status-only exit. Ask, not just name, the next question. Missing dispatch
approval allows clarification. Workers execute valid assignments, not interviews.

Use context or one known-short targeted read per missing fact; advance from it.
No scans, catalogs, chained research, polling or full-job waits.
Public reference GETs are not inference; send no private data.

Yield for real waits after eligible steps: phase, last action, exact gap/owner
and actual resume event/manual action.
Follow host question lifecycle: suspended is not completed; answered is not
waiting. Request normal access permission. No self-wake or loops.

Persist intent/results outside the queue before notifying. "Sent" is not receipt/
pickup. Before unattended yield prove idle-resume; arm independent observation
with finite pickup/recovery limits and alternate alert/control, or use an accepted
operator handoff. Missed receipt: stop repeat sends, preserve queue/state,
recover independently, reconcile before replay; no duplicate work or budget/
owner resets. Main
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

After approval reserve budget; use proven nonblocking workers or approved manual
handoff. Setup pins a commit, previews conflicts, copies linked references/
LICENSE without overwrites, adapts instructions/state separately, records
URLs/commit/revision/hashes and verifies discovery. Continue the actual objective.

New runs reconfirm without erasing owners, effects, authority, exclusions,
charges/reservations. Same-run approval survives; descendants inherit/tighten
parent limits. Never recover a host through its blocked queue.

## Source map

Pin one commit for localization; reuse pinned copies.
Multiple `main` GETs are not an atomic snapshot.

- [Protocol](https://raw.githubusercontent.com/taomar/foldspace-orchestrator/main/protocol/FIRST_SESSION_AND_ORCHESTRATION.md)
- [Run configuration](https://raw.githubusercontent.com/taomar/foldspace-orchestrator/main/protocol/RUN_CONFIGURATION.md)
- [Operator/recovery](https://raw.githubusercontent.com/taomar/foldspace-orchestrator/main/operations/OPERATOR_GUIDE.md)
- [Deployment](https://raw.githubusercontent.com/taomar/foldspace-orchestrator/main/protocol/DEPLOYMENT_BUILD_INSTRUCTIONS.md)
- [History](https://raw.githubusercontent.com/taomar/foldspace-orchestrator/main/reference/REVIEW_AND_CHANGES.md)
- [MIT license](https://raw.githubusercontent.com/taomar/foldspace-orchestrator/main/LICENSE)
