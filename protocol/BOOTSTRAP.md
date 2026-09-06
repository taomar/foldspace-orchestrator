# FoldSpace bootstrap

**Revision: 2.1.2 - 6 September 2026**

Use this small coordinator entry first. Keep the
[detailed protocol](FIRST_SESSION_AND_ORCHESTRATION.md),
[questionnaire](RUN_CONFIGURATION.md), and
[operator guide](../operations/OPERATOR_GUIDE.md) accessible by path; do not
preload them all into the opening turn. This is an instruction, not a scheduler
or a guarantee that the host will deliver input or finish a model/tool call.

## First response

After reading this entry, use supplied context to acknowledge the outcome and
state whether this is a new run, a continuation, or unknown. Ask **one next
unresolved question**, starting with run identity when needed, and end the
response. Do not first scan the repository, enumerate model catalogs/prices,
generate setup files, launch workers, or run recovery drills.

If a complete same-run approval and compact state are already supplied, identify
the next bounded coordination action instead of repeating the interview.
Missing evidence is a visible hold, not permission to invent facts.

## Advance without monopolizing the session

- Handle delivered steering first. Do not claim to read inaccessible UI queues.
- Before approval, resolve one interview decision at a time. If necessary, read
  one named compact record or known-short local metadata result for that
  question, then return. Do not chain searches or poll. Retain answers through
  an existing authorized record or recoverable conversation; no second ledger.
- If evidence or operator input is unavailable, identify the exact missing
  item and owner/action, then end the response. Do not repeatedly ask the same
  question, silently research every option, or keep a waiting turn alive.
- Include a short checkpoint when the state changes: **phase, last completed
  action, waiting on/owner, next action or actual resume trigger**. Use
  `awaiting_input`, `awaiting_evidence`, `ready_to_dispatch`, `waiting_external`,
  or `blocked` truthfully. Ending a response is not completing the project.
- After approval, use the ordinary dependency-driven dispatch cycle. Do not
  wait inside a full-job call, sleep, or poll for workers. Use demonstrated
  nonblocking dispatch or an approved independent manual session. Continue
  unrelated eligible work; return control when only waits remain.

## Approval is still mandatory

Before any orchestrated worker, including discovery/recovery, or direct
external LLM call, complete the [interview](RUN_CONFIGURATION.md):
approved providers/families and exact model IDs, role defaults and fallbacks;
each model's minimum/maximum and default within its verified supported order
(or explicitly accepted nonconfigurable N/A); external consent; aggregate
budget/units, allocations, concurrency, retries and stop policy; final approval.

Direct external calls default denied. No silent models, reasoning, cost-unit
conversions, unlimited budget, or approval bypass. Uncapped scope needs explicit
opt-in. Unknown settings are not evidence of fixed N/A. If required controls
cannot be applied/proved, hold affected work or obtain an approved demonstrable
manual path. Do not probe external endpoints with private data.

New runs reconfirm settings without discarding existing owners, assignments,
operations, authority records, resource exclusions, charges or reservations.
Same-run continuation retains valid approval. Reserve parent budget before
dispatch; descendants inherit/tighten, never reset it. Reconcile uncertain
effects/charges before replay or reallocation. Never restart or duplicate a
live operation merely to make bootstrap appear active.

For a silent or queued session, use the
[early-stall triage](../operations/OPERATOR_GUIDE.md#early-bootstrap-with-little-or-no-worker-activity).
Do not send this entry as a recovery message into that same blocked queue.
Inspect any automation producer through independent host controls; do not
claim that this entry can interrupt a stuck host, suppress triggers, or wake it.
