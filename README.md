# Agentic Infra Notes

Sanitized engineering notes on AI-assisted development, agent workflows, LLM infrastructure, and operational safety.

This repository shares architectural reasoning, workflow patterns, and engineering lessons from private R&D. It contains documentation rather than the private implementations. Experiments, design guidance, and independently validated results are distinguished below.

## Start here

### 1. AI-assisted engineering workflow

Read the [Agents-Core case study](case-studies/agents-core.md) for task routing, role separation, context discipline, and human review boundaries. Then use the [development safety checklist](checklists/agentic-development-safety-checklist.md) to inspect approval and validation concerns.

**Evidence type:** sanitized architecture and operating principles. Private implementation code and comparative performance results are not published here.

### 2. Local AI infrastructure and debugging

Read the [BOTAIO fine-tuning lab](case-studies/botaio-n8n-finetuning-lab.md) for Arm/Blackwell compatibility, QLoRA-oriented fallback decisions, memory pressure, and recoverable training workflows. The [draft model card](model-cards/qwen2.5-coder-32b-n8n-finetune.md) records intended use and evaluation limits.

**Evidence type:** historical lab documentation. BOTAIO is on hold. Independent inference and model-quality evaluation results are not published; this work is not a production-readiness claim.

### 3. Operations and safety

Start with the [LLMOps observability checklist](checklists/llmops-observability-checklist.md), [n8n workflow patterns](patterns/n8n-workflow-automation-patterns.md), and [agentic systems risk review](research/openclaw-zeroclaw-risk-review.md).

**Evidence type:** operational guidance and design review. These are not measured service-level results or a certified security assessment.

## Local LLM research

The Hermes research direction explores a local-model assistant with scoped handoffs to coding tools such as Claude Code or Codex CLI. Research questions include model/runtime compatibility, tool-call reliability, context limits, and the boundary between local inference and optional cloud services.

The design priorities are:

- Separate assistant data, task coordination, and code execution into explicit trust boundaries.
- Give workers only task-scoped files and capabilities; keep administrative credentials outside model-visible context.
- Validate with synthetic tasks before allowing access to personal data or external accounts.
- Record correctness, failure modes, latency, and resource use before claiming quality or cost improvements.
- Plan version pinning, backups, restore checks, and rollback before operational rollout.

**Status:** research and architecture design. This repository does not publish a validated Hermes deployment, a completed coding-agent integration, or performance benchmarks. This is separate from the historical BOTAIO fine-tuning experiment.

Upstream references: [Hermes model providers](https://hermes-agent.nousresearch.com/docs/integrations/providers), [Hermes security](https://hermes-agent.nousresearch.com/docs/user-guide/security), and [NVIDIA's local-LLM playbook](https://build.nvidia.com/spark/hermes-agent). These establish available integration paths, not results from this lab.

## Documentation map

- [Private R&D project index](private-rd/project-index.md)
- [Agents-Core: engineering workflow fabric](case-studies/agents-core.md)
- [Aegis-Forge: control-plane design](case-studies/aegis-forge.md)
- [Local-Core: local development infrastructure](case-studies/local-core.md)
- [BOTAIO: historical fine-tuning lab](case-studies/botaio-n8n-finetuning-lab.md)
- [Qwen2.5-Coder-32B: draft model card](model-cards/qwen2.5-coder-32b-n8n-finetune.md)
- [OpenClaw / ZeroClaw: risk review](research/openclaw-zeroclaw-risk-review.md)
- [n8n workflow automation patterns](patterns/n8n-workflow-automation-patterns.md)
- [Agentic development safety checklist](checklists/agentic-development-safety-checklist.md)
- [LLMOps observability checklist](checklists/llmops-observability-checklist.md)
- [Security and disclosure policy](SECURITY.md)

## Decision records

The three entries in [adr/](adr/) are proposed public decision records with context, alternatives, consequences, and validation plans. They formalize principles described in the linked notes and await owner review. They are not accepted decisions or evidence of runtime enforcement.

## Engineering principles

- Prefer reproducible setups over manual configuration.
- Separate planning, execution, review, and operational ownership.
- Keep automation observable, reviewable, and reversible.
- Treat context, cost, hardware/runtime compatibility, and operational risk as engineering constraints.
- Make human approval boundaries explicit for destructive, credential-related, financial, production, and externally visible actions.
- Keep design intent separate from demonstrated behavior.

## Disclosure boundary

This repository intentionally excludes private source code, prompts, routing logic, credentials, customer data, production workflow exports, real endpoints, machine-specific paths, private datasets, and unpublished model weights.

See [SECURITY.md](SECURITY.md) for the publication review checklist.

## Status

Public documentation collection with intentionally limited disclosure. Each case study states its evidence boundaries. The historical BOTAIO experiment is on hold; its evaluation plans describe possible future validation, not a scheduled continuation.
