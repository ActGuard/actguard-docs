# ActGuard

ActGuard is a runtime governance layer for AI agents.

It provides enforceable budgets, tool safeguards, and verifiable execution controls for production LLM systems — without requiring changes to how models are called.

Instead of trusting agents to behave, ActGuard makes behavior measurable, enforceable, and auditable.

---

## Why ActGuard Exists

LLM agents in production fail in predictable ways:

- Silent cost overruns  
- Endless retry loops  
- Hallucinated identifiers  
- Cross-step data corruption  
- Tool misuse  
- Missing workflow prerequisites  
- Prompt injection side effects  

Traditional guardrails focus on prompt shaping.  
ActGuard focuses on **runtime enforcement**.

---

## What ActGuard Does

ActGuard wraps LLM execution and tool calls with hard constraints.

### 1. Budget Enforcement

Set limits on:

- Token usage  
- USD cost  
- Model consumption per run  
- Per-tenant or per-agent limits  

Supports:

- OpenAI  
- Anthropic  
- Google  
- Streaming responses  
- Async execution  

No code changes to model calls — patch once within a guard context.

---

### 2. Tool Guards

Decorators for safe tool execution:

- `rate_limit`
- `max_attempts`
- `timeout`
- `circuit_breaker`
- `idempotent`

Prevents retry storms, duplicate side effects, and runaway loops.

---

### 3. Proof & Enforcement Layer

Optional custody verification:

- Ensure identifiers were actually fetched  
- Ensure required steps occurred before side effects  
- Prevent cross-step corruption  
- Block destructive calls not backed by evidence  

This moves agents from “best effort” to **provable correctness constraints**.

---

### 4. Gateway Integration

ActGuard can emit runtime events to a central platform:

- Token usage  
- Tool invocation metadata  
- Guard decisions  
- Enforcement blocks  

Designed for:

- Multi-tenant SaaS  
- Agent marketplaces  
- Enterprise AI governance  

---

## Architecture

At runtime:
```
LLM → Agent → Tool Calls
↓
ActGuard
↓
Enforce / Block / Record
```

Events can optionally stream to:

- Pub/Sub  
- BigQuery  
- Observability pipelines  
- Central governance dashboards  

---

## Who It’s For

- Teams deploying LLM agents in production  
- Companies with cost exposure to LLM APIs  
- Multi-tenant AI platforms  
- Builders who need runtime safety — not just prompt safety  

---

## Philosophy

LLMs are probabilistic.

Production systems cannot be.

ActGuard turns agent execution into something:

- Bounded  
- Observable  
- Enforceable  
- Economically measurable  