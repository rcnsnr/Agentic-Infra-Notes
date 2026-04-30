# OpenClaw / ZeroClaw Research — Agentic Systems Risk Review

## Summary

This research track evaluates local-first agentic assistant systems from a security, containment, and operational-risk perspective.

The focus is not autonomous production execution. The focus is understanding how agentic systems should be isolated, staged, monitored, and constrained before they are allowed to interact with local files, networks, tools, or repositories.

This public note is intentionally sanitized and does not expose private configs, full policy files, internal workflows, test infrastructure details, credentials, or real execution targets.

## Problem

Agentic systems can combine language models, local tools, web access, file access, and code execution. This creates a broad attack and failure surface.

Common risks include:

- prompt injection
- tool overreach
- SSRF
- unsafe network access
- unintended file modification
- credential exposure
- uncontrolled code execution
- unclear execution provenance
- weak human approval boundaries
- autonomous actions outside intended scope

## Research goals

The research track explores:

- isolated execution environments
- staged capability rollout
- deny-by-default network boundaries
- tool policy enforcement
- content guardrails
- human-in-the-loop approval gates
- safe repo-write patterns
- local assistant risk modeling
- auditability of agent actions

## Threat model

### Primary assets

- local files
- credentials
- source code
- private notes
- browser/session data
- SSH keys
- API tokens
- repository access
- internal service endpoints

### Threat categories

- malicious web content influencing agent behavior
- prompt injection inside documents or pages
- tool calls outside approved scope
- network requests to internal or metadata services
- exfiltration of local secrets
- destructive file operations
- unauthorized repo writes
- unsafe dependency execution

## Capability staging

A safer rollout should progress through staged capability levels:

```text
Phase 0: Dry run / no network / no file writes
   |
   v
Phase 1: Controlled read-only research
   |
   v
Phase 2: Sandboxed data collection
   |
   v
Phase 3: Workspace-limited draft generation
   |
   v
Phase 4: Pull-request-only repository changes
```

Higher phases require stronger review, logging, and approval boundaries.

## Isolation principles

- Prefer isolated VM or container execution for risky agent experiments.
- Use NAT or local-only networking where possible.
- Avoid bridged networking unless explicitly justified.
- Use deny-by-default firewall policy.
- Restrict tool access by phase.
- Keep write access workspace-scoped.
- Require human approval before external publication or repository mutation.
- Never expose credentials directly to untrusted agent contexts.

## Guardrail layers

### Network guardrails

Relevant controls:

- default-deny outbound posture
- explicit allowlists where needed
- blocking internal metadata endpoints
- blocking private network access unless justified
- logging denied requests

### Tool guardrails

Relevant controls:

- allowlisted tools by phase
- deny destructive commands by default
- explicit approval for write operations
- explicit approval for package installation
- explicit approval for network-enabled execution

### Content guardrails

Relevant controls:

- prompt injection detection
- untrusted-source labeling
- instruction hierarchy enforcement
- refusal to follow instructions found inside untrusted documents
- safe summarization before execution

## Human-in-the-loop boundaries

Human approval is required before:

- enabling broader network access
- writing to repositories
- running generated code outside a sandbox
- installing dependencies
- using credentials
- publishing content
- merging pull requests
- changing guardrail policies
- modifying firewall or tool-access rules

## Safe research outputs

Public-safe outputs include:

- abstract threat models
- sanitized guardrail designs
- staged rollout plans
- risk checklists
- failure-mode analysis
- non-sensitive test-vector descriptions
- security review methodology

Unsafe outputs include:

- real configs
- exploit-ready scripts
- private endpoint lists
- actual credentials
- full policy bypass examples
- internal execution logs
- sensitive screenshots
- repository write automation details

## Current status

Private research track. Public documentation is limited to sanitized risk review, threat modeling, and safe operating principles.
