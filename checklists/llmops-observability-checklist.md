# LLMOps Observability Checklist

Use this checklist to define minimum observability for AI-assisted workflows, agentic systems, model gateways, and LLM-powered automation.

## 1. Request telemetry

Track:

- [ ] request count
- [ ] request source
- [ ] workflow or run ID
- [ ] model/provider used
- [ ] input token estimate
- [ ] output token estimate
- [ ] total token estimate
- [ ] request duration
- [ ] response status
- [ ] retry count
- [ ] timeout count

## 2. Error telemetry

Track:

- [ ] provider errors
- [ ] rate-limit errors
- [ ] timeout errors
- [ ] validation errors
- [ ] tool execution errors
- [ ] policy-denied tool calls
- [ ] malformed output
- [ ] failed parsing
- [ ] failed post-processing
- [ ] failed human approval

## 3. Cost and quota signals

Track:

- [ ] provider
- [ ] model
- [ ] estimated cost
- [ ] budget group
- [ ] quota usage
- [ ] cost per workflow
- [ ] cost per run
- [ ] high-cost requests
- [ ] fallback usage
- [ ] abnormal cost spikes

## 4. Quality signals

Track where possible:

- [ ] human review result
- [ ] accepted output
- [ ] rejected output
- [ ] rework required
- [ ] repeated hallucination patterns
- [ ] invalid tool usage
- [ ] incorrect assumptions
- [ ] missing citations or evidence
- [ ] task completion rate
- [ ] failure by task category

## 5. Agent workflow signals

Track:

- [ ] selected workflow
- [ ] selected agent role
- [ ] stage transition
- [ ] approval requested
- [ ] approval granted
- [ ] approval rejected
- [ ] tool requested
- [ ] tool allowed
- [ ] tool denied
- [ ] final output state

## 6. Runtime health

Track:

- [ ] service uptime
- [ ] queue depth
- [ ] active runs
- [ ] failed runs
- [ ] stuck runs
- [ ] worker health
- [ ] model gateway health
- [ ] tool runtime health
- [ ] database health
- [ ] vector/search service health

## 7. Logs

Logs should include:

- [ ] timestamp
- [ ] correlation ID
- [ ] run ID
- [ ] workflow name
- [ ] agent role
- [ ] model/provider
- [ ] event type
- [ ] non-sensitive error message
- [ ] policy decision
- [ ] review decision

Logs should not include:

- [ ] raw credentials
- [ ] API keys
- [ ] private prompts
- [ ] full sensitive payloads
- [ ] customer secrets
- [ ] private tokens
- [ ] cookies or session values

## 8. Alerts

Consider alerts for:

- [ ] high error rate
- [ ] high timeout rate
- [ ] provider outage
- [ ] cost spike
- [ ] abnormal token usage
- [ ] repeated policy-denied tool calls
- [ ] stuck workflow runs
- [ ] queue backlog
- [ ] repeated human rejection
- [ ] failed critical automation

## 9. Runbooks

Document runbooks for:

- [ ] provider outage
- [ ] model degradation
- [ ] rate-limit exhaustion
- [ ] runaway cost
- [ ] stuck agent run
- [ ] failed workflow execution
- [ ] credential rotation
- [ ] leaked secret response
- [ ] policy misconfiguration
- [ ] rollback to safer execution mode

## 10. Dashboard minimums

A useful dashboard should show:

- [ ] requests over time
- [ ] errors over time
- [ ] latency over time
- [ ] token usage over time
- [ ] estimated cost over time
- [ ] model/provider split
- [ ] workflow success/failure rate
- [ ] denied tool calls
- [ ] approval backlog
- [ ] active/stuck runs
