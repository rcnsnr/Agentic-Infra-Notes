# BOTAIO — n8n Workflow Model Fine-Tuning Lab

## Summary

BOTAIO includes a private AI-assisted engineering lab focused on local fine-tuning infrastructure for an n8n workflow-specialist model.

The goal was to explore whether a coding-oriented LLM could be adapted to generate valid, structured, and reviewable n8n workflow JSON from natural language requests.

This public note focuses on the infrastructure, runtime, debugging, training-pipeline, and inference-readiness learnings. It does not publish model weights, private datasets, internal scripts, local paths, credentials, endpoints, or production claims.

## Positioning

This was an AI-assisted engineering lab, not a claim of ML research expertise.

AI tools were used for:

- planning
- debugging
- documentation
- implementation support
- troubleshooting
- operational review

The primary engineering focus was:

- local AI infrastructure
- reproducible training setup
- hardware/runtime compatibility
- containerized execution
- memory and context-length trade-offs
- QLoRA troubleshooting
- safe inference-readiness planning

## Problem

n8n workflows are structured JSON graphs. A useful n8n-specialist assistant needs to understand:

- n8n node structure
- connection logic
- credential boundaries
- trigger/action patterns
- conditional branching
- data transformation
- workflow importability
- safe review before production execution

General-purpose LLMs can draft n8n workflows, but they often fail on:

- invalid JSON
- missing node parameters
- broken node connections
- unsafe workflow assumptions
- hallucinated nodes or fields
- weak error handling
- missing credential boundaries

## Goal

Explore a local fine-tuning workflow for an n8n workflow-specialist model that can improve structural familiarity with n8n workflow JSON and support safer workflow drafting.

The intended output is not autonomous production workflow deployment. The intended output is a draft-generation assistant that still requires human review and sandbox testing.

## Hardware and runtime context

The lab was designed around a local AI workstation class environment:

- ASUS Ascent GX10 / NVIDIA GB10 Grace Blackwell class hardware
- Blackwell GPU architecture
- Arm CPU architecture
- large coherent unified memory
- containerized training runtime
- local model storage and experimentation

Public documentation intentionally avoids exact local paths, hostnames, ports, SSH targets, credentials, and machine-specific configuration.

## Base model

The experiment used a coding-oriented 32B-class model family as the base:

- Base family: Qwen2.5-Coder-32B-Instruct
- Target domain: n8n workflow generation
- Target output shape: valid, importable, reviewable n8n workflow JSON
- Adaptation approach: staged fine-tuning with LoRA/QLoRA-style techniques

## Why Qwen2.5-Coder-32B

The model family was selected because:

- it is strong at code and structured output generation
- it is dense rather than MoE, reducing runtime compatibility complexity
- it is a reasonable size for local high-memory AI workstation experimentation
- JSON and workflow-graph generation are close to its coding strengths

## Training strategy

The training strategy was staged.

```text
Base coding model
   |
   v
Stage 1: n8n structure / syntax adaptation
   |
   v
Merged intermediate model
   |
   v
Stage 2: complex workflow / reasoning-oriented adaptation
   |
   v
Final candidate model
   |
   v
Inference and evaluation planning
```

## Stage 1: n8n structure adaptation

Stage 1 focused on teaching the model n8n workflow structure.

Primary objective:

- learn n8n JSON shape
- learn common node structures
- learn basic connection patterns
- improve workflow-schema familiarity

Operational notes:

- long-running local training job
- large-context training considerations
- memory pressure required careful configuration
- final loss stabilized in the training notes
- output produced an intermediate merged model candidate

Public details intentionally exclude exact dataset processing scripts, private local paths, model artifact locations, and raw training logs.

## Stage 2: complex workflow adaptation

Stage 2 focused on more complex workflow patterns.

Primary objective:

- improve multi-node workflow composition
- improve conditional logic patterns
- improve handling of higher-complexity flows
- improve reasoning over workflow steps

Operational notes:

- used a filtered set of higher-complexity workflows
- used a lower learning-rate continuation strategy
- checkpointing was used for safety and recovery
- Blackwell/CUDA/bitsandbytes compatibility required troubleshooting

Public details intentionally avoid overclaiming final model quality without independent inference and evaluation results.

## Key engineering challenges

### 1. Arm + Blackwell ecosystem maturity

Some Python and training libraries were not equally mature across Arm CPU and Blackwell GPU environments.

Observed impact:

- compatibility issues
- dependency friction
- container runtime requirements
- reduced ability to rely on standard x86 CUDA assumptions

Engineering response:

- move toward containerized execution
- reduce dependency complexity where possible
- prefer stable runtime paths over experimental shortcuts
- document failure modes and recovery steps

### 2. FP8 and training compatibility

FP8 was useful as a storage/runtime optimization concept, but training-time compatibility introduced issues in the lab.

Observed impact:

- FP8-related operator/runtime incompatibility during training
- gradient/checkpointing interactions required fallback decisions

Engineering response:

- avoid forcing unsupported FP8 training paths
- move toward a more stable QLoRA-style configuration
- prioritize reproducibility over theoretical maximum speed

### 3. Memory and context-length trade-offs

Large models and long workflow JSON examples create high memory pressure.

Observed impact:

- context length directly affected memory behavior
- checkpointing and optimizer choices mattered
- memory stability was more important than maximal batch size

Engineering response:

- use memory-aware optimizer choices
- use gradient/memory-saving techniques where stable
- treat context length as an operational budget
- preserve recoverability through checkpointing

### 4. Dataset quality and shape

n8n workflow data is not automatically training-ready.

Observed impact:

- schema inconsistencies
- long examples
- noisy workflows
- variable workflow quality
- risk of teaching invalid or unsafe workflow patterns

Engineering response:

- filter for higher-quality workflow examples
- format examples consistently
- avoid raw workflow publishing
- treat dataset preparation as part of the core engineering problem

## Safety and disclosure boundaries

The public showcase intentionally excludes:

- model weights
- private training datasets
- raw workflow datasets after transformation
- internal scripts
- exact local runtime paths
- real endpoint names
- private logs
- local hostnames or ports
- credentials or tokens
- full inference configuration
- production deployment claims

## Inference-readiness plan

The planned inference-readiness path is:

```text
Final model candidate
   |
   v
Merge adapter into base model
   |
   v
Quantize for local inference where safe
   |
   v
Serve through a local inference runtime
   |
   v
Route through a controlled model gateway
   |
   v
Generate workflow drafts
   |
   v
Validate JSON / schema / importability
   |
   v
Human review and sandbox test
```

## Evaluation plan

Before making any production-oriented claims, the model should be evaluated against:

- JSON validity rate
- n8n import success rate
- node hallucination rate
- missing-parameter rate
- connection validity
- credential boundary correctness
- unsafe-action detection
- workflow execution success in sandbox
- human review acceptance rate
- regression against baseline prompts

## What this case study demonstrates

This lab demonstrates:

- local AI infrastructure setup
- containerized fine-tuning workflow design
- debugging under new hardware/runtime constraints
- staged model adaptation thinking
- QLoRA-oriented fallback decisions
- memory and context-budget reasoning
- AI-assisted engineering workflow discipline
- safe public documentation boundaries

## What this case study does not claim

This case study does not claim:

- production-ready model quality
- state-of-the-art benchmark performance
- autonomous workflow deployment safety
- ML research novelty
- general fine-tuning expertise across all model families
- validated enterprise-grade n8n generation accuracy

## Current status

Training-stage documentation exists. Independent inference and evaluation results are not published yet.

The next public-safe milestone would be a sanitized evaluation report showing JSON validity, n8n import success, failure classes, and human-review outcomes without exposing private data or production workflows.
