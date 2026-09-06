# Benefits, fit, and tradeoffs

FoldSpace Orchestrator describes ways to make AI-assisted work more explicit
and recoverable. It does not provide a runtime that enforces those practices.
The benefits below are **intended outcomes of following the protocol with
adequate host support**, not published benchmark results.

[Overview](README.md) | [Getting started](GETTING_STARTED.md) |
[Prompt examples](../operations/EXAMPLES.md) | [Run configuration](../protocol/RUN_CONFIGURATION.md)

## Before and after

### From conversation-based delegation to accountable handoffs

**Before:** "Handle the API work" goes to another session. Neither side records
the required interface revision, allowed files, owner of a shared test service,
or how to return a result. "Done" later refers to a branch the reviewer cannot
reconstruct.

**With the protocol:** The coordinator records a versioned assignment with
inputs, dependencies, write scope, resources, authority, budget, and acceptance.
The worker returns an identified candidate and evidence. Review and integration
refer to that candidate rather than an ambiguous success message.

**Condition:** The records and work artifacts must be accessible, current, and
actually used. A written resource reservation is not an enforced lock.

### From waiting for everyone to dependency-driven progress

**Before:** Several workers start together; all subsequent work waits for the
slowest one, even when a ready result has independent consumers.

**With the protocol:** Tasks declare the dependency state they need. Work
against an agreed contract can proceed when appropriate, while work requiring
an accepted artifact, integrated candidate, or verified environment waits for
that specific state. Backpressure applies where the resource or downstream
capacity is constrained.

**Condition:** Extra concurrency is useful only if the host can support it and
review, integration, resource ownership, and the aggregate budget can keep up.
There is no target worker count to fill.

### From restarting blindly to resuming deliberately

**Before:** A connection stalls. A replacement session repeats the last prompt,
assuming the first operation never happened.

**With the protocol:** Captured intent, checkpoints, actual work bytes, and
operation records support inspection of what was delivered, applied, executed,
and accepted. The responsible actor reconciles surviving effects before
replaying valid pending work.

**Condition:** Uncaptured messages cannot be reconstructed reliably; inaccessible
jobs may remain uncertain. The protocol does not guarantee exactly-once effects
or give a replacement session control over an old process.

### From prepared release files to an authorized, observed release

**Before:** A generated pipeline or successful build is described as a deployed
release, or preparation is mistaken for permission to change production.

**With the protocol:** Candidate identity, target, authority, gate evidence,
operation handles, observed health, and recovery actions remain distinct.
Existing authorization is reused where it still covers the action; missing
authority is not inferred from a request to build tooling.

**Condition:** The target platform must supply real controls and observations.
Code rollback alone does not reverse data changes.

## Benefit-to-mechanism map

| Intended benefit | Mechanism in the source | What to look for in practice |
|---|---|---|
| More responsive coordination | Separate coordinator and execution responsibilities | Steering can be handled without the coordinator owning long-running execution |
| Less duplicated or conflicting work | Versioned contracts, one accountable owner, explicit resource scopes | Fewer incompatible writes and fewer results rejected for stale assignments |
| More useful parallelism | Ready-task dependencies and scoped backpressure | Ready work advances while unrelated blockers remain isolated |
| Better continuity across sessions | Requirements, authoritative state, checkpoints, retrievable work | A fresh session can recover the next action without recreating the project history |
| More inspectable acceptance | Evidence bound to candidate, contracts, environment, and requirements | "Accepted" has traceable checks and review, not just a completion message |
| More controlled retries and cost | Inherited parent budgets and finite attempt history | Replacement sessions do not silently obtain a new allowance |
| Operator control over model selection | Mandatory pre-run approval of exact supported models, role defaults, and fallback allowlists | Actual applied settings match the approved run policy |
| Explicit reasoning bounds | Per-model supported minimum/default/maximum, or accepted N/A | No silent scale mapping or unsupported setting presented as applied |
| Separate consent for external data transfer | Direct external LLM calls denied until endpoint, purpose, data scope, credential reference, and budget are approved | Native Copilot authorization is not reused as blanket external-call consent |
| Less budget oversubscription | Parent reservations before concurrent dispatch; inherited usage and uncertain-charge reconciliation | New work stops at known bounds rather than treating replacements as a fresh budget |
| Safer recovery from uncertain delivery | Preserve intent, distinguish delivery/application/effects, reconcile before replay | Unknown outcomes are investigated before potentially duplicating mutations |
| Clearer release accountability | Separate preparation, authority, execution, verification, and recovery | Release state corresponds to actual observed effects on the named target |

For the underlying rules, use
[FIRST_SESSION_AND_ORCHESTRATION.md](../protocol/FIRST_SESSION_AND_ORCHESTRATION.md),
the day-to-day [OPERATOR_GUIDE.md](../operations/OPERATOR_GUIDE.md), and
[DEPLOYMENT_BUILD_INSTRUCTIONS.md](../protocol/DEPLOYMENT_BUILD_INSTRUCTIONS.md).

## Where it fits

Good candidates include a feature with several real dependency boundaries,
work that regularly crosses session/context limits, a repository with several
contributors or agents sharing resources, and a release workflow that needs
explicit evidence and authority handoffs.

It can also support human-assisted execution when native worker orchestration
is missing, provided someone carries assignments and results and the limitation
is recorded honestly.

It is usually a poor fit for a trivial one-file change with no coordination
problem, a project unwilling to maintain authoritative state, or a workflow
where nobody can review consequential output. A restricted host may support
the recordkeeping but not the intended concurrent execution.

It is **not** an appropriate substitute for a production job scheduler,
transaction coordinator, access-control system, audited deployment gate,
independent supervisor, or platform-level reliability guarantee. Choose real
infrastructure when those properties are requirements.

## Costs and tradeoffs

| Cost or constraint | Practical consequence |
|---|---|
| Coordination overhead | Assignments, state reconciliation, checkpoints, and reviews take time; use the smallest useful records |
| Context overhead | Repeating the entire protocol can crowd out task context; use a compact core and load details when needed |
| Model and tool costs | More workers, retries, and repeated discovery can increase total cost even if work overlaps |
| Configuration and accounting overhead | Every new run needs explicit model/reasoning/consent/budget confirmation; native and external costs may use incomparable units |
| Enforcement limits | Model settings and monetary limits require actual host controls and usage/pricing evidence; unsupported autonomous dispatch must remain blocked |
| Host capability limits | Separate contexts, nonblocking dispatch, follow-up, cancellation, queue capture, and recovery must be checked independently |
| Review and integration capacity | Faster candidate production can create a backlog rather than faster accepted delivery |
| Shared-resource contention | Isolated worktrees do not isolate databases, ports, identities, queues, or external environments |
| Record maintenance | Stale state can be worse than an explicit unknown; keep a clear source of truth and owner |
| Confidentiality | Durable messages, checkpoints, and logs can contain sensitive material; choose storage and retention deliberately |
| Review independence | A same-worker review may be useful but is not an independent judgment; disclose the limit |
| Recovery complexity | An uncertain external effect may require human/platform investigation, not another prompt or retry |

The protocol can help expose these tradeoffs. It cannot make them disappear.

## Measure outcomes, not agent activity

Establish a baseline for comparable work in your own environment before
claiming improvement. Record task scope and complexity, host/model
configuration, relevant constraints, and the definition of "accepted" or
"integrated." Do not compare a draft patch in one workflow with a verified
release in another.

| Question | Useful observations |
|---|---|
| Does accepted work arrive sooner? | Elapsed time from ready assignment to accepted and integrated outcome; separate queue, execution, review, and integration time |
| Is coordination responsive? | Time from steering capture to acknowledgement and valid application; distinguish delivery from application |
| Is ready work unnecessarily idle? | Ready-but-unassigned intervals, documented blockers, ownership, and unblock actions |
| Is output correct and current? | Rework, stale-candidate rejections, failed acceptance gates, and defects found after integration |
| Is concurrency economical? | Total model/tool cost and worker effort per accepted outcome, including retries and review |
| Does continuity work? | Time to reconstruct an actionable checkpoint, missing work artifacts, and repeated investigation |
| Does recovery avoid replay mistakes? | Lost-intent incidents, duplicate effects, unresolved outcomes, and reconciliation work |
| Is the whole workflow balanced? | Review/integration backlog and contention for shared resources |

Collect evidence in appropriate storage without publishing private prompts,
credentials, customer data, or operational logs. Include failed and blocked
tasks instead of measuring only successful examples. Attribute changes
cautiously: model updates, task mix, reviewer availability, and host behavior
can explain differences.

This repository ships no benchmark suite, telemetry collector, or measured
performance claims. Its source revision's
[historical verification and limits](../reference/REVIEW_AND_CHANGES.md#5-verification-and-limits)
are a useful boundary for interpreting what has and has not been demonstrated.
