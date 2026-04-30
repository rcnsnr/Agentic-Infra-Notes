# Security Policy

This repository contains sanitized public documentation only.

It intentionally excludes production code, private prompts, credentials, customer data, internal endpoints, real workflow exports, and proprietary implementation details.

## Do not commit

Do not commit:

- API keys
- tokens
- passwords
- cookies
- private keys
- real `.env` files
- private prompts
- system instructions from private agents
- production endpoints
- private hostnames
- internal IP addresses
- SSH targets
- customer data
- internal workflow definitions
- raw n8n workflow exports
- private infrastructure configuration
- screenshots containing secrets or internal URLs

## Allowed public content

Allowed content includes:

- abstract architecture notes
- sanitized case studies
- risk-review methodology
- generic workflow diagrams
- operational checklists
- non-sensitive ADRs
- public-safe engineering principles
- placeholder examples

## Sensitive data response

If sensitive data is accidentally committed:

1. Revoke or rotate the affected credential immediately.
2. Remove the sensitive data from the repository.
3. Review commit history and public forks if applicable.
4. Check whether the data was exposed through actions logs, screenshots, artifacts, or releases.
5. Document the incident and prevention step.
6. Add or improve guardrails to prevent recurrence.

## Review checklist before publishing

- [ ] No real credential is present.
- [ ] No `.env` file is present.
- [ ] No private prompt is present.
- [ ] No production endpoint is present.
- [ ] No internal hostname or IP is present.
- [ ] No raw customer data is present.
- [ ] No raw workflow export contains secrets.
- [ ] No screenshot contains sensitive information.
- [ ] No implementation detail exposes private routing logic.
- [ ] No content implies unsafe autonomous execution.

## Disclosure

This repository is not a public security program. If you notice sensitive data or a security issue in this repository, contact the repository owner privately instead of opening a public issue.
