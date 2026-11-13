# ADR 0001: Agent Routing Boundaries

Status: Proposed public ADR, awaiting owner review.

This draft formalizes principles already described in the linked public notes. It does not establish a historical approval date or verify runtime enforcement.

## Context

AI-assisted engineering can lose consistency when each repository and tool uses unrelated task rules. Unclear ownership, prompt drift, excessive context, and missing review gates make generated changes harder to inspect.

The published Agents-Core case study separates routing, architecture, implementation, audit, and operations. It also distinguishes routine work from reasoning-heavy or ambiguous tasks.

## Proposed decision

Route a task only after identifying its goal, target workspace, allowed actions, expected output, and stopping condition.

Keep planning, building, review, and operational responsibility explicit. Load the standards relevant to the task rather than the entire knowledge collection.

Local or lower-cost models may handle bounded, routine work where suitable. More demanding reasoning can use stronger models. Model choice does not grant additional tool, data, or publication permissions.

Before a result proceeds to release, record the changes, checks performed, unresolved risks, and applicable human review outcome.

## Alternatives for review

- One general-purpose agent for the whole workflow: simpler coordination, but weaker separation of responsibilities.
- The strongest model for every step: simpler selection, but no demonstrated cost benefit for routine tasks.
- Role-separated routing: clearer ownership and review, with additional handoff and coordination work.

These are design alternatives in this proposal, not a record of completed comparative experiments.

## Consequences

The workflow becomes easier to inspect, but handoffs can lose information or add latency. A routing decision must remain explainable, and uncertain scope should be clarified rather than silently expanded.

No accuracy, productivity, or cost improvement is claimed without a controlled evaluation.

## Validation needed

Use synthetic tasks covering routine edits, ambiguous requests, and higher-risk actions. Review route selection, context passed between roles, denied operations, final diffs, and verification results. Record failures and human corrections.

## Public evidence

- [Agents-Core case study](../case-studies/agents-core.md): role separation, model-selection principles, safety boundaries, and operational signals.
- [Agentic development safety checklist](../checklists/agentic-development-safety-checklist.md): scope, tools, review, and rollback questions.
- [LLMOps observability checklist](../checklists/llmops-observability-checklist.md): workflow, model, quality, and policy-decision telemetry.

Private routing rules, prompts, and implementation details are intentionally excluded.
