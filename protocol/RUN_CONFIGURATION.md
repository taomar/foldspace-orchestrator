# Configure the run before dispatch

**Revision: 2.1.4 - 6 September 2026**

This is the bootstrap questionnaire and configuration reference for FoldSpace
Orchestrator, not an executable configuration loader. The canonical
[orchestration protocol](FIRST_SESSION_AND_ORCHESTRATION.md) and
[operator guide](../operations/OPERATOR_GUIDE.md) define the surrounding workflow.

## Mandatory gate

Before a new run launches **any orchestrated workers, including discovery
workers**, or makes direct external LLM API calls, explicitly ask the operator
to approve models, reasoning, external-call consent, and budget controls.
Reconcile any prior configuration and reconfirm it for the new run.

The current bootstrap chat may continue safe local planning and read available
capability documentation to prepare the interview. It is not retroactively
blocked. Do not spend money or send private repository/user data to an external
endpoint merely to discover models, reasoning options, pricing, or credentials.

A bounded read of a user-approved public FoldSpace GitHub reference is allowed;
it is not an external LLM inference call. Bulk downloading/localization remains
an approved setup-worker task after the interview, not a preapproval bypass.

Within-run continuation, replay, or handoff carries the approved scope forward
without asking on every tool call. New providers, expanded data/purpose scopes,
unapproved fallbacks, wider reasoning bounds, or expanded limits need renewed
explicit approval. A fresh session is not necessarily a new run.

## Bootstrap questionnaire

Start the coordinator with [BOOTSTRAP.md](BOOTSTRAP.md), not a bulk load of all
references. Reconcile supplied intent/run mode and valid answers first,
including the optional inputs below. The table is a coverage checklist, not a
requirement to replay all sixteen questions.

**One question at a time means at most one outstanding unanswered question.**
Use the supported question mechanism. When an answer arrives, including a
synchronous question-tool result, reconcile it and take the next bounded read,
missing/conflicting/unsupported question, review/final approval request, or
approved action. Do not end with only "recorded/blocked until..." when one of
those steps is available. No extra "continue" is required. Complete unapproved
answers go to validation and a resolved summary for explicit final approval;
same-run valid approval is retained, not requested again by habit.

Use supplied evidence or one known-short targeted read for a missing fact;
consume its result and advance, rather than returning solely because a lookup
finished. If evidence is unavailable, request the exact item/location/access
from its owner or advance an independently answerable field. "Continue pending
work" uses supplied context or a known compact authoritative checkpoint/task
index to derive candidates and acceptance; ask focused selection if needed,
not a rewritten backlog. Unknown facts stay unknown and block affected dispatch,
not all interview progress. Do not launch discovery workers to unlock approval.

Follow the [canonical transition contract](FIRST_SESSION_AND_ORCHESTRATION.md#opening-turn-and-return-control-contract):
yield for real unanswered input/evidence/capability dependencies with exact
gap, owner and supported resume event/manual action. A suspended question is
not a completed response; an answered question is not waiting. No broad scans,
catalogs, chained research, polling, invented defaults/N/A or self-wake.

| Order | Question to ask |
|---|---|
| 1 | "Is this a new run, or a continuation of an existing approved run? Which objective and current run record apply?" |
| 2 | "Which providers, model families, and exact supported model IDs may this run use?" |
| 3 | "Which approved model should be the default, and which role-specific overrides should apply to coordinator, execution, review, integration, and deployment?" |
| 4 | "Which exact fallback models, if any, are approved? What conditions may select each fallback?" |
| 5 | For each model: "From this model's verified supported reasoning choices, what minimum is permitted?" |
| 6 | For that model: "What maximum is permitted?" |
| 7 | For that model: "Which default should be selected within those bounds?" |
| 8 | For fixed/unsupported reasoning: "This model's reasoning is not configurable/N/A in this host. Do you accept that limitation for this role?" |
| 9 | "Are direct external LLM API calls disabled, or do you explicitly consent to a defined scope?" |
| 10 | If enabled, ask separately for provider/endpoint, approved models, purpose, permissible data categories, and secure credential references. Never ask for key values in project records. |
| 11 | "What aggregate run cap and measurable units do you approve, or do you explicitly opt into an uncapped scope and its cost risk?" |
| 12 | "How should allowance be allocated between Copilot-managed sessions and direct external calls, with worker/task/provider subcaps where needed?" |
| 13 | "What maximum concurrency is allowed?" |
| 14 | "What retry/replacement limits apply within that same allowance?" |
| 15 | "At a cap, unsupported setting, or uncertain charge, what stopping and escalation policy should apply?" |
| 16 | "Do you approve this complete versioned policy, including any explicitly uncapped or assisted limitations, before affected dispatch begins?" |

Split unresolved compound fields into individual questions. Summarize existing
explicit answers for final new-run reconfirmation; do not force the operator
to recreate them. Final approval must cover the resolved objective/acceptance,
scope/authority, policy version, settings, accounting and capability limitations.

## Optional prestaged interview inputs

You may paste any known answers **under the bootstrap prompt** to reduce
back-and-forth. No file, attachment, new tracker or state store is required.
This is optional preparation, not a demand to research models, reconstruct
tasks or manufacture unknown facts. Leave unknown/unset fields explicit.
Keep sensitive/private answers in the authorized target conversation or
existing private records, **not in this public documentation repository**.

**Operator choices** establish desired scope, limits and consent.
**Agent-verified evidence** establishes recorded project facts and actual host
support; an operator's proposed setting is not proof that the host applies it.
The agent derives/reconciles available facts from supplied context or known
compact authoritative records and verifies only the controls needed next.
It asks only missing, conflicting or unsupported items.

| Input | When needed | Operator can prestage | Agent reconciles or verifies |
|---|---|---|---|
| Project and run | Required | Target; new project/new run/same-run continuation; existing run/policy reference if known | Actual run/version and approval source; a new session need not mean a new run |
| Outcome and acceptance | Required | Desired result/criteria **or** "continue recorded pending work" plus known tracker/state/checkpoint path or task IDs | Recorded candidate tasks, acceptance and current dependencies; focused selection only for material ambiguity |
| Scope and authority | Required for intended effects; deadlines conditional | Allowed actions/files, compatibility constraints, exclusions, relevant deadline; known authority references | Existing grants and limits; setup/preparation is not deployment/publication permission |
| Ongoing work | Existing projects/shared resources | Known owners, jobs, operations, resources/exclusions and record references, or unknown | Current ownership/effects, pending steering and conflicts; do not orphan old work or infer it stopped |
| Host and surface | Optional hints; required control evidence before affected execution | Host/surface/version and known limitations or evidence references | Available interaction, model/reasoning selection and observation, dispatch/return, accounting and assisted controls |
| Models | Required for applicable roles | Providers/families/exact IDs, default model, role overrides, exact fallbacks and selection conditions | Actual support and application evidence; families or silent defaults are insufficient |
| Reasoning per model | Required | Minimum/default/maximum, or proposed nonconfigurable N/A acceptance | Provider/model-specific supported order and in-range default; verify N/A and obtain explicit acceptance, never infer it from unknown support |
| Direct external LLM calls | Required disabled/enabled decision; details conditional on opt-in | Disabled, or provider/endpoint/exact models/purpose/permitted data categories and **secure credential reference only** | Distinct from native Copilot; no key values, private-data probes or calls before scoped consent and final approval |
| Budgets and allocations | Required; subcaps conditional | Explicit caps **and units**, native/external allocations, applicable task/worker/provider subcaps | Observable/boundable units, separate incomparable ledgers, price/usage evidence where needed; no invented numbers or conversions |
| Concurrency, retries and stop | Required | Maximum concurrency, retry/replacement limits, stop/escalation rules and accountable authority | Feasibility within parent caps, uncertainty and reservation controls; no automatic budget increase |
| Existing accounting | Existing runs/work where applicable | Known ledger reference, usage, reservations and uncertain charges, or unknown | Authoritative balances and surviving exposure before replay/reallocation; staging does not reset budgets |
| Final run approval | Required for a new run; not granted by staging | Preparation only; final approval pending | Validate and summarize the versioned policy, evidence/limits and scope, then request explicit approval; retain valid same-run approval |

Missing caps are not unlimited. A deliberately uncapped scope is exceptional:
explicitly identify that scope, opt in and acknowledge unbounded-cost risk.
Other scoped limits still apply. Native/external allocations with incomparable
units stay separate; do not add them or silently convert them to money.

### Copy and paste preparation template

This is an **illustrative text template**, not an executable schema, live
configuration, permission grant or approved launch packet. All bracketed values
are placeholders; replace only what you know. Repeat the model line as needed.
Any staged external consent is scoped input, **not overall run authorization**.

```text
Preparation only; final approval pending.
Project/target: <known reference or unknown>
Mode: <new project / new run / same-run continuation / unknown>
Existing run/policy/approval reference: <known reference or unknown>
Outcome/acceptance: <desired result and criteria OR continue recorded pending work>
Pending tracker/state/checkpoint and task IDs: <known references or unknown>
Scope/compatibility/allowed actions/exclusions: <choices or unset>
Deadline if relevant: <constraint or unknown>
Existing authority references: <known references or unknown>
Ongoing owners/jobs/operations/resources/exclusions: <known facts/refs or unknown>
Host/surface/version/known limits/evidence: <known hints/refs or unknown>
Providers/families/exact model IDs: <choices or unset>
Default model and role overrides: <coordinator/execution/review/integration/deployment choices or unset>
Exact fallbacks and selection conditions: <choices, explicitly none, or unset>
Per model: <exact ID>; reasoning min/default/max: <choices or unset>;
  supported-order evidence: <reference or unknown>;
  nonconfigurable N/A evidence and explicit acceptance: <if applicable or unset>
Direct external calls: <disabled OR proposed conditional scope OR unset>
If enabled: <provider/endpoint/exact models/purpose/permitted data categories>
Secure credential REFERENCE only, never a key: <if enabled, reference or unknown>
Aggregate native cap + units: <explicit choices or unset>
Aggregate external cap + units: <if applicable, explicit choices or unset>
Native/external allocations and applicable subcaps + units: <choices or unset>
Exceptional uncapped scope + explicit risk acknowledgment: <if chosen or unset>
Maximum concurrency: <choice or unset>
Retry/replacement limits: <choices or unset>
Stop/escalation policy and authority: <choices or unset>
Existing ledger/usage/reservations/uncertain charges: <known facts/refs or unknown>
Remaining decisions/evidence gaps: <known gaps or unknown>
```

Partial input advances to the next real missing question. Fully populated but
unapproved input advances to verification, summary and final explicit approval,
not automatic setup/dispatch. Reconcile changed facts against existing records;
do not create duplicate authority or ledger totals from the pasted template.
Same-run valid approval, owners, effects, resource exclusions and reservations
survive. A new-run approval remains separate even if all choices were prestaged.

## Model and reasoning validation

Record the provider and exact supported ID, selected model for each applicable
role, allowed fallbacks, and the mechanism that applies and reports settings.
An allowlisted family alone is not an exact model selection.

Reasoning labels are **provider/model-specific categorical values**, not
universal numbers. Obtain their supported ordering from adequate host/provider
evidence. Check `minimum <= default/effective <= maximum` in that ordering,
not lexical order or a mapping from another model's labels.

If evidence establishes that reasoning is fixed or nonconfigurable in this
host, record **not configurable / N/A** with explicit operator acceptance.
Unknown support is not verified N/A. Do not fabricate a min/max range; if
ordering cannot be established, bounds are not validated.

If the host cannot select or prove the actual applied model/reasoning, record
**Unavailable** or **Assisted**. Block autonomous dispatch that would claim to
honor the unsupported controls. An assisted alternative requires exact,
operator-approved local configuration steps and evidence of the applied
settings before execution. Markdown itself is not enforcement.

## External calls default denied

Copilot-managed session/agent requests and direct requests to external LLM
endpoints are different consent and accounting paths. Authorization for the
former does not imply permission for the latter.

Require an explicit external-call answer, even when **disabled**; reuse a valid
supplied answer or same-run consent rather than asking it again. Without
consent, external calls are **denied**. An enabled grant must identify
provider/endpoint, allowed models, purpose, permitted data categories, secure
credential references, and budget. Repository access is not blanket consent
to send repository contents externally.

A valid recorded scope can cover multiple calls without repeated prompts.
Anything outside it remains blocked. Unknown consent blocks those calls, not
safe local planning or already-approved native session work.

## Budget and accounting

Require an aggregate run cap in units the host can actually observe or bound:
currency, host credits, tokens, calls, or another explicitly supported unit.
Do not silently choose a cap, treat missing as unlimited, or translate between
units without justified, approved accounting.

Where native and external paths use incomparable units, the authoritative run
view contains **separate aggregate bounds and ledgers** for each unit/path.
Do not report their sum as money. Accurate monetary enforcement needs actual
pricing/usage information and controls adequate to the approved limit.

Record allocations/subcaps, concurrency, retry/replacement limits, and the
stopping/escalation policy. Explicitly uncapped scope requires deliberate
opt-in and acknowledgment that total cost is not bounded; other scoped limits
still apply.

Before concurrent dispatch, reserve against all applicable parent limits using
a demonstrated atomic ledger mechanism, or serialize reservations through one
accountable coordinator/operator if no such mechanism exists. Files copied
across branches are not atomic reservations.

Keep consumed usage, outstanding reservations, reconciled refunds/unused
allowance, and uncertain in-flight charges distinct. A replacement or replay
does not obtain a new budget. Do not release an uncertain reservation because
the chat disappeared. Reconcile actual usage and surviving effects before
reallocation.

At a cap, missing approval, unsupported setting, or usage uncertainty that
would violate bounds, block **new affected work** and report the exact
constraint. Do not automatically kill stateful operations. Any safe observation
or recovery must remain within its own approved scope and allowance; escalation
requires permission, not an automatic more expensive model.

## One authoritative policy

Use the target project's existing record arrangement:

| Record | Owns |
|---|---|
| `POLICY` or its established equivalent | Approved run ID/version, operator/source/time, models/reasoning, consent, limits, and the authoritative ledger or its single owning reference |
| `CAPABILITIES` | Evidence of supported models/reasoning, actual selection/observation, accounting and reservation controls, limitations, assisted steps |
| `PROJECT_STATE` | Active run, policy version, ledger references, current ownership, blockers, and next action |
| Assignments and dispatch packets | `run_policy_ref`, effective role/model/reasoning/consent scope, and `budget_reservation` references |
| Results, operations, checkpoints | Actual applied settings/evidence, consumption and reservation changes, unknown charges/effects, and next action |

These names describe target-project records, often under `docs/ai`, **not
preinstalled files in this repository**. This reference guide is not a second
live policy store. Descendants inherit or tighten the approved scope; they
cannot broaden it by writing a new packet.

## Compact configuration example

This is an **illustrative record shape with placeholders**, not a runnable
schema, valid launch packet, credential, supported model list, or approved cap.
Replace every placeholder with operator-approved facts. Supported ordering
below is specific to the chosen model, not a universal reasoning scale.

```yaml
run_id: "<existing authoritative run identity>"
policy_version: "<approved version>"
approval:
  operator: "<operator identity>"
  source_ref: "<recoverable approval record>"
  approved_at: "<approval timestamp>"
models:
  - provider: "<approved provider>"
    family: "<approved family>"
    exact_id: "<supported and approved model ID>"
    capability_evidence_ref: "<selection and observation evidence>"
    reasoning:
      configurable: "<true, or false with explicit N/A acceptance>"
      supported_order: ["<verified first value>", "<verified next value>"]
      minimum: "<approved supported value, or N/A>"
      default: "<approved value within bounds, or N/A>"
      maximum: "<approved supported value, or N/A>"
role_defaults:
  coordinator: "<approved model ID and reasoning>"
  execution: "<approved model ID and reasoning>"
  review: "<approved model ID and reasoning>"
  integration: "<approved model ID and reasoning>"
  deployment: "<approved model ID and reasoning, or unused>"
approved_fallbacks: []
external_llm:
  consent: denied
  approved_scopes: []
budget:
  aggregate_bounds_ref: "<approved cap/unit per accounting path>"
  allocations_and_subcaps_ref: "<native/external/task/provider allocations>"
  concurrency_limit: "<approved bound>"
  retry_replacement_limit: "<approved bound>"
  stop_and_escalation_ref: "<approved policy>"
  ledger_ref: "<single authoritative usage/reservation/remaining ledger>"
```

If external calls are enabled, each approved scope must add its explicit
provider/endpoint, allowed models, purpose, data categories, secure credential
reference, budget allocation, and approval record. Do not fill those fields
with keys or infer them from a native-session grant.

## Dispatch and recovery examples

| Case | Required outcome |
|---|---|
| Approved native worker | Current policy names its exact model and supported in-range reasoning; host applies/proves them; consent is sufficient for native work; parent allowance is reserved. Dispatch may proceed. |
| Explicitly disabled external calls | Native work may proceed within its own approval; direct external research/evaluation/API calls are blocked. |
| Approved external call | Endpoint/model/purpose/data match the recorded opt-in, secure credential reference is usable, and external plus parent limits have a valid reservation. No new per-call interview is needed. |
| Invalid minimum/default/maximum | Default falls outside the approved supported ordering, or minimum is above maximum. Block selection; ask for corrected approval rather than silently clamping it. |
| Unsupported reasoning | Record N/A and obtain explicit acceptance if genuinely fixed. If required selection or applied-setting evidence is unavailable, block autonomous launch or use a specifically approved demonstrable manual path. |
| Proposed fallback | Proceed only if its exact model and reasoning are already approved and every relevant budget still fits; otherwise request approval. |
| Exhausted allocation | Block new affected workers/calls. Report consumption, reservations, scope, and escalation needed; do not reset the cap or automatically kill stateful jobs. |
| Unknown charge after disconnect | Keep the in-flight reservation and inspect actual provider/host usage and effects before retrying or reallocating. Silence does not mean zero spend. |
| Replacement coordinator or worker | Restore the same run policy, authority, usage, and reservations; adopt valid assignments without broadening limits. |
| New run or 2.0 upgrade | Reconcile prior work/charges and explicitly approve or reconfirm the new run policy before affected dispatch; existing live effects are not erased or retroactively orphaned. |
| New run while a migration survives | Retain the prior migration's owner, operation handle, resource exclusion, reservation, and uncertain charges in the authoritative project view. A conflicting migration remains blocked; an unrelated documentation task may proceed under its own approved settings and available budget. |

Deployment executors, reviewers, research/evaluation workers, parallel children,
and manual launches use the same gate. See the
[deployment protocol](DEPLOYMENT_BUILD_INSTRUCTIONS.md) and
[revision history](../reference/REVIEW_AND_CHANGES.md).
