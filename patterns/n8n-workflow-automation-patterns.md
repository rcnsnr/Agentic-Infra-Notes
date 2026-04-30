# n8n Workflow Automation Patterns

## Summary

This note documents safe public patterns for private n8n workflow automation experiments.

It does not publish real workflow exports, webhook URLs, credentials, customer flows, production endpoints, or internal business logic.

## Problem

Workflow automation can become fragile and risky when workflows are built without explicit reliability, credential, approval, and failure-handling patterns.

Common failure modes include:

- hidden credential exposure
- webhook URLs committed to git
- production workflows edited directly
- missing retry logic
- no error branch
- silent partial failures
- unbounded AI-generated changes
- unclear ownership of workflow outputs
- no human approval before external action

## Design principles

- Never commit real workflow exports without sanitization.
- Never publish real webhook URLs.
- Keep credentials in the automation platform, not in exported JSON.
- Treat AI-generated workflows as drafts until manually reviewed.
- Add explicit error paths.
- Add retry and timeout behavior where supported.
- Prefer small composable workflows over large opaque flows.
- Document trigger, input, output, failure mode, and owner.
- Require human approval before sending external messages, changing records, or invoking paid/irreversible actions.

## Safe pattern categories

### 1. Webhook intake with validation

```text
Webhook trigger
   |
   v
Input validation
   |
   +--> Invalid payload -> reject/log
   |
   v
Normalize payload
   |
   v
Next workflow step
```

Key controls:

- validate required fields
- reject unknown payloads
- avoid trusting sender-provided metadata
- log only non-sensitive identifiers
- avoid exposing full payloads in public examples

### 2. Human approval before external action

```text
Draft generated output
   |
   v
Human approval step
   |
   +--> Reject -> stop/log
   |
   +--> Approve -> send/update/execute
```

Use this for:

- emails
- CRM updates
- payment-related actions
- public posting
- customer-facing notifications
- repo or issue updates
- AI-generated recommendations

### 3. Error handling branch

```text
Main workflow path
   |
   +--> Success -> continue
   |
   +--> Error -> notify owner / log / retry decision
```

Recommended fields to capture:

- workflow name
- node name
- error category
- non-sensitive correlation ID
- retry count
- timestamp
- owner/team
- next action

### 4. Retry with bounded attempts

```text
Action node
   |
   +--> Success -> continue
   |
   +--> Transient failure -> retry with limit
   |
   +--> Permanent failure -> error branch
```

Controls:

- max retry count
- timeout
- backoff
- dead-letter or manual review path
- clear distinction between transient and permanent failures

### 5. Credential isolation

Do:

- store credentials in n8n credential storage
- use environment variables for non-secret config
- document placeholders only
- rotate credentials if exported accidentally
- review workflow JSON before sharing

Do not:

- commit API keys
- commit bearer tokens
- publish webhook URLs
- paste production credentials into AI tools
- share raw workflow exports without inspection

### 6. AI-assisted workflow drafting

```text
Requirement
   |
   v
AI draft
   |
   v
Manual review
   |
   v
Sandbox test
   |
   v
Production copy / controlled import
```

Controls:

- never directly edit production workflows with AI
- test in a dev or copy workflow first
- validate node configuration explicitly
- avoid relying on defaults
- inspect expressions and credentials before enabling

## Public-safe documentation

Good examples:

- abstract workflow diagrams
- sanitized pseudo-workflows
- reliability checklists
- approval-boundary patterns
- failure-mode notes
- credential-handling rules

Unsafe examples:

- raw workflow exports
- webhook URLs
- credential node details
- customer payloads
- internal endpoint names
- production API schemas
- screenshots containing tokens or real data

## Review checklist

Before publishing any n8n-related content:

- [ ] No real webhook URL is present.
- [ ] No credential value is present.
- [ ] No customer data is present.
- [ ] No production endpoint is present.
- [ ] No internal hostname is present.
- [ ] No private business logic is exposed.
- [ ] Workflow is described as a pattern, not as a production export.
- [ ] Human approval boundaries are documented.
- [ ] Error handling is documented.
- [ ] Retry/timeout behavior is documented.

## Current status

Private workflow automation experiments. Public documentation is limited to sanitized patterns and operational safety notes.
