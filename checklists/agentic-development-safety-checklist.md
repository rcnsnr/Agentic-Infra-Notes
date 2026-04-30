# Agentic Development Safety Checklist

Use this checklist before allowing an AI-assisted agent or workflow to modify files, call tools, publish content, or interact with external systems.

## 1. Task definition

- [ ] Is the task goal explicit?
- [ ] Is the target repository, directory, or workspace clear?
- [ ] Is the expected output format defined?
- [ ] Are assumptions documented?
- [ ] Are out-of-scope actions listed?
- [ ] Is there a clear stopping condition?

## 2. Scope boundaries

- [ ] Are allowed files/directories defined?
- [ ] Are blocked files/directories defined?
- [ ] Are generated files intentional?
- [ ] Are destructive operations blocked or gated?
- [ ] Are production resources excluded unless explicitly approved?
- [ ] Are credentials and private configs excluded?

## 3. Tool permissions

- [ ] Are allowed tools listed?
- [ ] Are risky tools disabled by default?
- [ ] Are shell commands reviewed before execution?
- [ ] Is network access required and justified?
- [ ] Is package installation required and justified?
- [ ] Are write operations gated?
- [ ] Are external API calls gated?

## 4. Human approval gates

Require human approval before:

- [ ] deleting files or data
- [ ] modifying credentials or access
- [ ] changing production configuration
- [ ] publishing public content
- [ ] sending external messages
- [ ] installing dependencies
- [ ] running generated code outside a sandbox
- [ ] merging pull requests
- [ ] executing irreversible operations

## 5. Secret handling

- [ ] No `.env` file is included.
- [ ] No API key is included.
- [ ] No token is included.
- [ ] No password is included.
- [ ] No private key is included.
- [ ] No cookie/session value is included.
- [ ] `.env.example` contains placeholders only.
- [ ] Secret scanning was considered before publishing.

## 6. Execution safety

- [ ] The agent has a limited workspace.
- [ ] The task can be interrupted safely.
- [ ] The task has a rollback path.
- [ ] Intermediate outputs are reviewable.
- [ ] Generated code is not trusted without inspection.
- [ ] Commands are logged or summarized.
- [ ] Failures produce actionable information.

## 7. Review before merge or publish

- [ ] Final diff is reviewed by a human.
- [ ] Tests or validation commands were run where applicable.
- [ ] Documentation was updated.
- [ ] Security-sensitive changes were inspected.
- [ ] No private data is present.
- [ ] No hidden generated artifacts are present.
- [ ] Known limitations are documented.
- [ ] Rollback instructions are documented where relevant.

## 8. Release readiness

- [ ] The change has a clear purpose.
- [ ] The change is reversible or has a mitigation plan.
- [ ] Operational impact is understood.
- [ ] Observability impact is understood.
- [ ] Failure modes are documented.
- [ ] Ownership is clear.
