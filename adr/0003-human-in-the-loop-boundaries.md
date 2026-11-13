# ADR 0003: Human-in-the-Loop Boundaries

Status: Proposed public ADR, awaiting owner review.

This draft formalizes principles already described in the linked public notes. It does not establish a historical approval date or verify runtime enforcement.

## Context

An agent can produce a plausible plan or pass tests while still exceeding the intended scope. Correct output does not itself authorize publication, credential changes, production access, or irreversible actions.

The public Agents-Core case study and safety checklist describe explicit scope, human approval gates, reviewable outputs, and rollback thinking.

## Proposed decision

Define permitted actions and the target workspace before execution. Keep the authority to change permissions separate from the model's task reasoning.

Require the applicable human approval before destructive changes, credential or access changes, production configuration changes, public publication, external communications, and other consequential actions.

A review checkpoint should state the concrete target, proposed change, known impact, validation performed, unresolved risks, and recovery plan. A failed or missing approval should stop the gated action.

Treat generated code and tool output as material to inspect, not as independent proof of safety or permission. Passing tests does not bypass the approval boundary.

## Alternatives for review

- Autonomous execution across all tools: less interruption, but unacceptable uncertainty about authority and external effects.
- Confirmation before every small step: simple to describe, but adds friction and can weaken attention to important decisions.
- Explicit scopes with risk-based checkpoints: routine work can remain bounded while consequential steps receive deliberate review.

This ADR proposes the third approach. Exact permissions remain specific to the owner, task, and execution environment.

## Consequences

Human review adds latency and needs clear ownership. Repeated or vague approval requests can cause fatigue. Requests should be concrete, and prior authorization should not be silently stretched to changed targets or risks.

Application-level approval also needs enforcement by the surrounding tool and execution permissions. A prompt alone is not a security boundary.

## Validation needed

Use synthetic cases for allowed work, denied actions, changed scope, missing approval, and interrupted execution. Verify that gated actions stop, approvals are attributable, results remain reviewable, and rollback procedures are documented.

Do not publish raw credentials, private prompts, sensitive payloads, or internal endpoints as evidence.

## Public evidence

- [Agents-Core case study](../case-studies/agents-core.md): approval boundaries, operational signals, and separation of responsibilities.
- [Agentic development safety checklist](../checklists/agentic-development-safety-checklist.md): task scope, approval, execution safety, release review, and rollback.
- [LLMOps observability checklist](../checklists/llmops-observability-checklist.md): requested, granted, rejected, allowed, and denied events.
- [Security policy](../SECURITY.md): public disclosure restrictions.
