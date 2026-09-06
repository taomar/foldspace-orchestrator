# Configure the run before dispatch

**Revision: 2.1 - 6 September 2026**

This is the bootstrap questionnaire and configuration reference for FoldSpace
Orchestrator, not an executable configuration loader. The canonical
[orchestration protocol](FIRST_SESSION_AND_ORCHESTRATION.md) and
[operator guide](../guides/OPERATOR_GUIDE.md) define the surrounding workflow.

## Mandatory gate

Before a new run launches **any orchestrated workers, including discovery
workers**, or makes direct external LLM API calls, explicitly ask the operator
to approve models, reasoning, external-call consent, and budget controls.
Reconcile any prior configuration and reconfirm it for the new run.

The current bootstrap chat may continue safe local planning and read available
capability documentation to prepare the interview. It is not retroactively
blocked. Do not spend money or send private repository/user data to an external
endpoint merely to discover models, reasoning options, pricing, or credentials.

Within-run continuation, replay, or handoff carries the approved scope forward
without asking on every tool call. New providers, expanded data/purpose scopes,
unapproved fallbacks, wider reasoning bounds, or expanded limits need renewed
explicit approval. A fresh session is not necessarily a new run.

## Bootstrap questionnaire

Ask **one question at a time** where the host supports it. Replace choices with
actual supported options and record the response; do not preselect a model or
invent a spending cap. Unknown answers leave the affected work blocked.

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

Split compound follow-up fields into individual questions rather than treating
the table as a single blanket approval prompt. Existing explicit answers can
be summarized for reconfirmation; do not force the operator to recreate them.

## Model and reasoning validation

Record the provider and exact supported ID, selected model for each applicable
role, allowed fallbacks, and the mechanism that applies and reports settings.
An allowlisted family alone is not an exact model selection.

Reasoning labels are **provider/model-specific categorical values**, not
universal numbers. Obtain their supported ordering from adequate host/provider
evidence. Check `minimum <= default/effective <= maximum` in that ordering,
not lexical order or a mapping from another model's labels.

If reasoning is fixed, unavailable, or unsupported, record **not configurable /
N/A** with the operator's acceptance. Do not fabricate a min/max range. If
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

Always ask the external-call question, even if the answer is **disabled**.
Before consent, external calls are **denied**. An enabled grant must identify
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

Deployment executors, reviewers, research/evaluation workers, parallel children,
and manual launches use the same gate. See the
[deployment protocol](DEPLOYMENT_BUILD_INSTRUCTIONS.md) and
[revision history](../reference/REVIEW_AND_CHANGES.md).
