# Agentic Infra Notes

Sanitized engineering notes on AI-assisted infrastructure, agentic workflows, LLMOps, and self-hosted automation control planes.

This repository documents architecture thinking, operating principles, safety boundaries, and workflow patterns from private R&D work. It does not expose production source code, credentials, private prompts, real endpoints, customer data, internal workflow exports, or proprietary routing logic.

## Scope

This repository focuses on:

- AI-assisted engineering workflows
- Multi-agent development systems
- Self-hosted automation control planes
- Local AI/dev infrastructure
- Human-in-the-loop execution boundaries
- LLMOps observability and cost control
- Agentic workflow safety and operational review

## Private R&D referenced

The following private projects are referenced only through sanitized notes:

- `Agents-Core` — multi-agent engineering workflow fabric
- `Aegis-Forge` — self-hosted AI engineering control plane
- `Local-Core` — local AI/dev infrastructure workspace
- `OpenClaw / ZeroClaw Research` — agentic systems risk review and isolated execution research
- `n8n workflow patterns` — reusable automation patterns with explicit safety boundaries
- `Trustlayer` — private product/R&D exploration, intentionally limited here
- `BOTAIO` — private product/R&D exploration, intentionally limited here

## Documentation map

- [`private-rd/project-index.md`](private-rd/project-index.md)
- [`case-studies/agents-core.md`](case-studies/agents-core.md)
- [`case-studies/aegis-forge.md`](case-studies/aegis-forge.md)
- [`case-studies/local-core.md`](case-studies/local-core.md)
- [`research/openclaw-zeroclaw-risk-review.md`](research/openclaw-zeroclaw-risk-review.md)
- [`patterns/n8n-workflow-automation-patterns.md`](patterns/n8n-workflow-automation-patterns.md)
- [`checklists/agentic-development-safety-checklist.md`](checklists/agentic-development-safety-checklist.md)
- [`checklists/llmops-observability-checklist.md`](checklists/llmops-observability-checklist.md)
- [`SECURITY.md`](SECURITY.md)

## Disclosure boundary

This repository intentionally excludes:

- source code from private projects
- real system prompts or private instruction chains
- credentials, tokens, keys, cookies, or `.env` files
- real service endpoints, IP addresses, hostnames, ports, or internal URLs
- customer data or customer-specific workflows
- production architecture diagrams with implementation-level details
- exact model routing rules
- provider API keys, cost ledgers, or private usage data
- production n8n workflow exports
- proprietary implementation details

## Engineering principles

- Prefer reproducible setups over manual configuration.
- Keep automation observable, reviewable, and reversible.
- Separate planning, execution, review, and operational ownership.
- Use local or lower-cost models for routine tasks where safe.
- Reserve stronger models for reasoning-heavy work.
- Require human approval for destructive, credential-related, financial, production, or externally visible actions.
- Treat context, cost, and operational risk as first-class engineering constraints.

## Status

Active notes repository. Content is intentionally sanitized and incomplete by design.
