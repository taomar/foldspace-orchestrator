# FoldSpace Orchestrator

**Bridge separate agent contexts. Keep the work connected.**

FoldSpace is a **documentation-based operating protocol for GitHub Copilot**:
explicit coordination, bounded worker assignments, durable project memory, and
evidence-based acceptance.

**These are instructions and guides, not executable software.** No runtime,
scheduler, extension, or supervisor is installed. Use demonstrated host
capabilities or an explicit assisted/manual handoff.

[Get started](GETTING_STARTED.md) |
[Benefits](BENEFITS.md) |
[Prompt examples](../operations/EXAMPLES.md) |
[Run configuration](../protocol/RUN_CONFIGURATION.md)

Current protocol: **2.1.2**. See the [release history](../reference/REVIEW_AND_CHANGES.md).

## On this page

[Why FoldSpace](#why-foldspace) |
[Quick start](#quick-start) |
[Run controls](#configure-every-new-run) |
[Files and reading path](#reading-path-and-repository-map) |
[Limits](#capabilities-and-limits)

## Why FoldSpace

Separate agent conversations can lose track of who owns work, which
requirements are current, and whether a previous operation actually finished.
FoldSpace makes those handoffs explicit.

| Instead of... | Use... |
|---|---|
| Vague delegation and overlapping edits | Versioned assignments, named owners, and bounded write/resource scopes |
| Waiting for every worker before moving on | Ready work driven by its actual dependencies and available capacity |
| Accepting an unexplained "done" | Evidence tied to the actual candidate and acceptance criteria |
| Restarting from memory or blindly retrying | Durable state, recoverable work, and reconciliation of surviving effects |

These mechanisms are intended to improve continuity and accountability, not
promise measured speedups. Read the [benefits and tradeoffs](BENEFITS.md).

### Who it is for

Developers and teams coordinating dependent work across sessions, especially
when review, shared resources, or release handoffs matter. For a small isolated
edit, one session and a focused check may be simpler.

## How it works

The coordinator handles intent, dependencies, assignments, and acceptance.
Workers own substantive execution, review, integration, and operation records.

```mermaid
flowchart TD
    U["User: outcome and approval"] --> C["Coordinator"]
    C <--> W["Workers: execution, review, integration"]
    C <--> S["Durable project state and evidence"]
    W <--> S
```

This is a conceptual flow, **not an installed service or a mandatory serial
pipeline**. Each task waits on its own dependencies. Concurrency follows
approved limits, demonstrated capacity, resource ownership, and review capacity,
not a fixed worker count.

## Quick start

1. [Obtain the pack](GETTING_STARTED.md#obtain-the-documentation-pack), then open
   the **target repository** where you want to work.
2. Supply only the compact [bootstrap entry](../protocol/BOOTSTRAP.md) and your
   brief/current state first. Keep the detailed references accessible by path;
   do not preload the whole pack into the opening turn.
3. Expect one next question or bounded-action checkpoint, then a completed
   response. Complete the interview and give final approval before any worker,
   including discovery, or direct external LLM call starts.

```text
Start with BOOTSTRAP.md; keep the detailed references available for scoped reading.
Target: [repository; new project, new run in an existing project, or continuation]
Outcome and acceptance: [one bounded result and observable criteria]
Constraints and authority: [allowed scope, compatibility, and excluded effects]

Preserve existing instructions, work, active owners, operations, and accounting.
First acknowledge supplied intent/run mode, ask one unresolved question, and
end the response before further investigation. On a missing-input/evidence hold,
show the exact gap and next actor, then return; do not scan, poll or wait for jobs.
For a new run, conduct the mandatory interview one question at a time:
exact supported models/role defaults/fallbacks, per-model reasoning bounds and
default, external-call consent, budgets/units and allocations, concurrency,
retries, and stop policy. Ask for final approval; use no silent defaults.
Until then, do only safe local preparation in this current bootstrap chat.

After approval, reserve budget and prepare the first versioned assignment.
Use evidenced host controls or an approved manual worker packet with a return
path. Accept only candidate-specific evidence; do not expand release authority.
```

This is ordinary language, not a native command. The
[first-use guide](GETTING_STARTED.md) includes copying references, a
[worked example](GETTING_STARTED.md#a-bounded-worked-example), and
[manual fallback](GETTING_STARTED.md#manual-worker-fallback).

## Configure every new run

| Required approval | What it covers |
|---|---|
| Models | Allowed providers/families and exact supported IDs, role defaults/overrides, and fallback models |
| Reasoning | Each model's approved minimum/maximum and default within those bounds, using its verified supported order; explicitly accepted N/A when not configurable |
| External LLM calls | Explicitly disabled, or approved provider/endpoint, models, purpose, data categories, secure credential references, and budget |
| Budget and execution | Aggregate cap in measurable units, native/external allocations and relevant subcaps, reservations, concurrency, retries/replacements, and stop/escalation policy |

Direct external calls default **denied**; native Copilot authorization does
not authorize them. Missing budget is not unlimited; uncapped scope needs
explicit opt-in. Do not invent conversions between credits, tokens, and money.

Same-run continuation retains approved authority. A new run reconfirms settings
without dropping existing owners, operations, charges, or reservations.
Children and replacements inherit or tighten limits; uncertain charges must
be reconciled before reallocation. See the [full questionnaire](../protocol/RUN_CONFIGURATION.md).

## Reading path and repository map

```text
foldspace-orchestrator/
|-- LICENSE
|-- .gitattributes
|-- .gitignore
|-- .github/
|   `-- CONTRIBUTING.md
|-- docs/
|   |-- README.md
|   |-- BENEFITS.md
|   `-- GETTING_STARTED.md
|-- protocol/
|   |-- BOOTSTRAP.md
|   |-- FIRST_SESSION_AND_ORCHESTRATION.md
|   |-- DEPLOYMENT_BUILD_INSTRUCTIONS.md
|   `-- RUN_CONFIGURATION.md
|-- operations/
|   |-- OPERATOR_GUIDE.md
|   `-- EXAMPLES.md
`-- reference/
    `-- REVIEW_AND_CHANGES.md
```

| Your next question | Read |
|---|---|
| How do I try it? | [Getting started](GETTING_STARTED.md) and [compact bootstrap entry](../protocol/BOOTSTRAP.md) |
| What must I approve? | [Run configuration](../protocol/RUN_CONFIGURATION.md) |
| How do I operate it? | [Operator guide](../operations/OPERATOR_GUIDE.md) and [prompt examples](../operations/EXAMPLES.md) |
| What are the detailed rules? | [Canonical protocol](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md) |
| What are the costs and release boundaries? | [Benefits/tradeoffs](BENEFITS.md) and [deployment reference](../protocol/DEPLOYMENT_BUILD_INSTRUCTIONS.md) |
| What changed, or how can I contribute? | [Revision history](../reference/REVIEW_AND_CHANGES.md) and [contribution guide](../.github/CONTRIBUTING.md) |

## What gets created in your project

Adoption reuses or creates small authoritative records for policy, capabilities,
requirements, assignments, evidence, and current state. Suggested `docs/ai/*`
paths are **outputs in your target project**, not preinstalled files here.
Keep secrets and private operational material out of public commits.

## Deployment scope

The deployment reference covers distributing the working setup and releasing
the adopter's software. It prescribes no cloud or pipeline product.
Preparation does not grant release authority: candidate, target, effects, and
required gates must match the recorded authorization.

## Capabilities and limits

Markdown cannot enforce model settings, budgets, locks, or permissions; wake
idle sessions; recover inaccessible unsent messages; guarantee exactly-once
effects or successful recovery; or repair IDE/provider defects.

Record what the actual host demonstrates. If required controls cannot be
applied and evidenced, block affected autonomous work or use a specifically
approved, demonstrable manual path. Do not pretend unsupported automation works
or assume a quiet job stopped. Compatibility and performance are not guaranteed.

If the bootstrap itself stops responding, another prompt may only join its
queue. Use [independent early-stall and automation triage](../operations/OPERATOR_GUIDE.md#early-bootstrap-with-little-or-no-worker-activity),
not a queued recovery message. The compact entry is prevention, not a host reset.

## License and name

Released under the [MIT License](../LICENSE). The name takes inspiration from
space-folding in *Dune*, as a metaphor for connecting separate agent contexts.
This independent project is not an official GitHub or Microsoft product and
is not affiliated with or endorsed by the owners of *Dune*.
