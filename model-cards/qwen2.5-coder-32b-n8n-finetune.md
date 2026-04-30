# Draft Model Card — Qwen2.5-Coder-32B n8n Fine-Tuning Experiment

## Status

Draft / private R&D.

Model weights are not published from this repository. This file is a sanitized public model card for documentation and portfolio purposes only.

## Model summary

This experiment fine-tuned a Qwen2.5-Coder-32B-Instruct class base model toward n8n workflow generation.

The target behavior is to generate structured, reviewable n8n workflow JSON drafts from natural language automation requests.

The model is intended for draft generation and sandbox validation. It is not intended to autonomously deploy or modify production workflows.

## Intended use

Intended use cases:

- draft n8n workflow JSON from natural language
- assist with workflow structure planning
- suggest node chains and control flow
- support workflow prototyping in a sandbox
- help review n8n workflow patterns

Non-goals:

- autonomous production workflow deployment
- credential handling
- merchant/customer-impacting actions
- unsupervised workflow execution
- final decision-making for business-critical automation
- replacing human review

## Base model

- Base model family: Qwen2.5-Coder-32B-Instruct
- Target domain: n8n workflow automation
- Output focus: structured JSON workflow drafts
- Training approach: staged LoRA/QLoRA-style adaptation

## Training objective

The training objective was to improve the model's familiarity with:

- n8n workflow JSON structure
- node definitions
- graph connection patterns
- common trigger/action flows
- conditional branching
- multi-node workflow composition
- structured automation output

## Training stages

### Stage 1: Structure and syntax adaptation

Focus:

- n8n JSON structure
- common node patterns
- workflow syntax familiarity
- basic workflow composition

Expected improvement:

- better schema awareness
- fewer malformed workflow drafts
- stronger structured-output behavior

### Stage 2: Complex workflow adaptation

Focus:

- multi-node workflows
- conditional logic
- data transformation
- reasoning-oriented workflow composition
- higher-complexity examples

Expected improvement:

- stronger workflow planning
- better graph composition
- improved ability to map user intent to node chains

## Hardware and runtime

The training lab was conducted on local AI workstation class hardware:

- ASUS Ascent GX10 / NVIDIA GB10 Grace Blackwell class system
- Arm CPU architecture
- Blackwell GPU architecture
- large coherent unified memory
- containerized training runtime

Public documentation intentionally avoids exact local paths, hostnames, endpoints, credentials, and machine-specific configuration.

## Training configuration

Sanitized training configuration:

- adaptation method: QLoRA-style fine-tuning
- quantization/training strategy: memory-aware local training configuration
- context length: long-context workflow examples were supported during experimentation
- checkpointing: used for recovery and staged progress
- optimizer/runtime choices: selected for memory stability and compatibility

Exact internal scripts, paths, and private logs are not published.

## Known engineering constraints

### Hardware/runtime compatibility

The lab encountered compatibility constraints around:

- Arm CPU package availability
- Blackwell GPU runtime maturity
- CUDA/library compatibility
- FP8 training-path limitations
- memory pressure from large model + long workflow context

### Dataset quality

n8n workflow data required filtering and formatting because raw workflows can be:

- inconsistent
- overly long
- noisy
- unsafe
- incomplete
- dependent on credentials or external services

### Output reliability

Workflow generation needs validation beyond language-model output quality.

Important checks include:

- valid JSON
- valid n8n schema
- importability
- valid node references
- valid graph connections
- no hallucinated node types
- no unsafe credential assumptions
- safe error-handling behavior

## Evaluation plan

Before any production-oriented claims, the model should be evaluated against:

- JSON validity rate
- n8n import success rate
- node hallucination rate
- missing required parameter rate
- connection validity
- workflow execution success in sandbox
- unsafe-action detection
- human review acceptance rate
- regression against baseline prompting
- comparison against the base model

## Safety considerations

Generated workflows must be reviewed before use.

Do not directly deploy generated workflows to production. Always:

- inspect generated JSON
- validate node configuration
- test in a sandbox
- remove or replace placeholder credentials
- review webhook exposure
- review external API calls
- add error handling
- add retry and timeout behavior where needed
- require human approval before external or irreversible actions

## Limitations

Known limitations:

- independent public evaluation is not published yet
- model weights are not published from this repository
- training data details are intentionally sanitized
- generated workflows may still contain invalid or unsafe assumptions
- n8n node schemas change over time
- integrations may require credentials or tenant-specific configuration
- workflow execution behavior must be tested in a real n8n sandbox

## Disclosure boundary

This model card intentionally excludes:

- model weights
- private datasets
- raw transformed datasets
- local filesystem paths
- training logs
- exact runtime commands
- internal scripts
- credentials
- endpoints
- private inference configuration
- production workflow exports

## Recommended use pattern

```text
User request
   |
   v
Model-generated workflow draft
   |
   v
JSON validation
   |
   v
n8n import validation
   |
   v
Sandbox execution
   |
   v
Human review
   |
   v
Controlled deployment decision
```

## Current status

Training-stage documentation exists. Independent inference and evaluation results are not published yet.

This model card should be updated only after a sanitized evaluation report is available.
