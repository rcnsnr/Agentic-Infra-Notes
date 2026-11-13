# ADR 0002: Context Budgeting

Status: Proposed public ADR, awaiting owner review.

This draft formalizes principles already described in the linked public notes. It does not establish a historical approval date or verify runtime enforcement.

## Context

Agent workflows need enough information to act correctly, while unnecessary material increases token usage and can distract from the current task. Session-to-session context loss is a separate problem from simply using a larger context window.

The public Agents-Core notes describe loading relevant standards, reusable memory conventions, and context-budget control. The local fine-tuning case study separately records hardware-memory and training context-length constraints; these are not the same measurement as an agent's prompt budget.

## Proposed decision

Begin with a small task context: goal, scope, constraints, relevant source material, and acceptance criteria. Add detail when the task needs it rather than loading the whole project by default.

Preserve reusable decisions and project context in reviewable, versioned documentation. Treat a summary as a navigation aid; verify consequential claims against their source.

Track input and output token estimates, duration, retries, model/provider, and quality outcomes. Budget choices should account for task correctness as well as cost.

Do not invent a universal token limit or claim a percentage saving. Task-specific limits and their enforcement need separate evidence.

## Alternatives for review

- Load all available context: broad coverage, but higher cost and more irrelevant material.
- Use only a short summary: lower initial load, but a greater risk of missing constraints or stale conclusions.
- Use a small core with selective expansion: more deliberate source retrieval and maintenance, with better control over what enters each task.

These alternatives have not been benchmarked by this ADR.

## Consequences

Selective loading can reduce unnecessary context, but retrieval mistakes may omit important information. Summaries can become stale. Source references and review of missing assumptions are therefore part of the design.

Context length, token estimates, and GPU memory are distinct signals and should not be presented as interchangeable.

## Validation needed

Compare the same synthetic tasks under an all-context baseline and selective loading. Record correctness, missing constraints, token use, latency, rework, and stale-source failures. Review the results before choosing numerical budgets or claiming improvements.

## Public evidence

- [Agents-Core case study](../case-studies/agents-core.md): relevant-standard loading, context loss, and reusable workflow conventions.
- [LLMOps observability checklist](../checklists/llmops-observability-checklist.md): token, cost, latency, quality, and retry signals.
- [Historical fine-tuning lab](../case-studies/botaio-n8n-finetuning-lab.md): hardware-memory and training context-length trade-offs.

Private memory contents, prompts, thresholds, and configuration are intentionally excluded.
