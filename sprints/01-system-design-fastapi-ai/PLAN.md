# Sprint 01 — System Design + Python/FastAPI + AI Engineering

## Intent

Learn system design and Python/FastAPI/AI in parallel, using one track to reinforce the other.

- System Design answers: **what should the system do, how should it behave, and what are the trade-offs?**
- Python/FastAPI/AI answers: **can we build and measure the risky parts?**

## Capacity

- 14 learning days
- ~4 hours/day
- ~50–56 total hours
- ~25% study / ~75% hands-on

## Primary Project

[AI Transaction Gateway](../../projects/ai-transaction-gateway/README.md)

Natural language in → validated financial transaction candidates out.

This is a standalone lab, not an automatic Monyvi migration.

## Daily Rhythm

1. 30–40m focused learning
2. 45–60m design/reasoning
3. 90–120m build
4. 30–45m verify/document/commit

## Week 1

### Day 01 — Requirements + environment
Study:
- functional vs non-functional requirements;
- latency/throughput/availability/reliability;
- stateful vs stateless;
- Python basics needed immediately.

Build:
- uv environment;
- run starter FastAPI app;
- implement GET /health;
- first pytest;
- refine requirements.md.

Exit:
- explain latency vs throughput and stateful vs stateless;
- health test passes.

### Day 02 — Contracts + typing + Pydantic
Study:
- REST contracts/versioning;
- Python unions/Literal/Enum;
- Pydantic BaseModel/Field;
- OpenAPI.

Build:
- POST /v1/transactions/parse;
- typed request/response;
- empty/oversized input tests.

Exit:
- client-invalid input cannot reach provider logic.

### Day 03 — Layering + DI
Study:
- separation of concerns;
- ports/adapters practically;
- FastAPI Depends vs Angular DI.

Build:
- TransactionAIProvider Protocol;
- FakeAIProvider;
- application service;
- thin route;
- substitution tests.

Exit:
- fake/real provider can swap without endpoint rewrite.

### Day 04 — Async + latency
Study:
- I/O-bound vs CPU-bound;
- event loop;
- concurrency vs parallelism;
- HTTPX AsyncClient pooling.

Build:
- artificial provider latency;
- blocking vs async experiment;
- concurrent requests;
- record timings.

Exit:
- explain why async improves concurrency but not one provider call's intrinsic latency.

### Day 05 — Real provider + structured output
Study:
- model output is untrusted;
- structured output/schema validation;
- provider vs domain schema;
- env-based secrets.

Build:
- one real provider adapter (DeepInfra/DeepSeek is a natural candidate);
- structured validation;
- domain mapping;
- mocked adapter tests.

Exit:
- malformed output cannot silently become a transaction.

### Day 06 — Reliability
Study:
- timeout;
- transient vs permanent errors;
- bounded retries;
- exponential backoff/jitter;
- retry storms;
- circuit breaker concept.

Build:
- timeout;
- explicit retry policy;
- tests: timeout/429/5xx/malformed response;
- update failure-modes.md.

Exit:
- total retry/time budget is bounded and explainable.

### Day 07 — Warehouse appointment design
Sanitized MR-inspired problem.

Design:
- requirements/NFRs;
- hypothetical scale;
- APIs/data model;
- architecture;
- double-booking prevention;
- idempotency;
- failure cases;
- Mermaid diagram.

Exit:
- defend DB constraint/locking/concurrency choice under tutor challenge.

## Week 2

### Day 08 — Caching
Study:
- hit/miss/TTL/cache-aside/invalidation;
- local vs distributed cache.

Build:
- educational in-memory TTL cache;
- careful cache key;
- tests;
- cached vs uncached timing;
- document multi-instance limitation.

### Day 09 — Background jobs
Study:
- sync vs async;
- queues/workers;
- 202/job status;
- at-least-once/durability/DLQ.

Build:
- POST parse/jobs → 202 + job ID;
- GET jobs/{id};
- in-process educational queue/store;
- document why it is not durable/production distributed infrastructure.

### Day 10 — Idempotency
Study:
- retry ambiguity;
- duplicate requests;
- consistency/races.

Build:
- Idempotency-Key;
- request fingerprint;
- same key/same payload → replay;
- same key/different payload → conflict;
- Monyvi comparison notes.

### Day 11 — AI evaluation
Study:
- eval datasets;
- deterministic expected outputs;
- field-level metrics;
- regression testing.

Build:
- ~30 synthetic cases;
- evaluator;
- schema/count/amount/currency/type/merchant/date metrics;
- baseline result.

### Day 12 — Capacity + load
Study:
- average/peak RPS;
- concurrency;
- p50/p95/p99;
- external-provider bottlenecks.

Build:
- 100k-user hypothetical capacity estimate;
- Locust test against fake provider;
- low/slow provider modes;
- record environment/results.

### Day 13 — Yard live tracking
Sanitized YMS-inspired problem.

Study/design:
- polling vs SSE vs WebSocket;
- ordering;
- duplicates;
- reconnect/replay;
- current state vs event history.

Optional build:
- FastAPI SSE endpoint with synthetic events.

### Day 14 — Architecture defense
Run:
- tests;
- Ruff;
- mypy;
- eval baseline;
- load smoke.

Finish:
- architecture/failure/capacity docs;
- ADRs;
- mock Staff review;
- retrospective;
- next sprint proposal.

## Definition of Done

- all daily exit criteria reviewed;
- app runs from clean clone;
- tests pass;
- lint/type checks pass or have explicit documented follow-up;
- eval baseline exists;
- load-test evidence exists;
- two design exercises are complete;
- ADRs capture real decisions/trade-offs;
- retrospective identifies real gaps;
- PROGRESS.md links evidence.

## Non-Goals

Do not add without a proven need:

- Kubernetes
- production Redis
- advanced PostgreSQL
- Azure
- RAG/vector DB
- MCP
- multi-agent orchestration
- production Celery/RabbitMQ
- complex OAuth

## Research Rule

When behavior is version-sensitive or uncertain, verify using current official/primary documentation before treating it as fact.
