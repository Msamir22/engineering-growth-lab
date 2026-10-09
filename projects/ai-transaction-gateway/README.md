# AI Transaction Gateway

A production-style learning service for practicing System Design + Python/FastAPI + AI Engineering.

## Purpose

Accept natural-language financial text and return validated structured **transaction candidates**.

Example input:

```json
{"text":"I spent 450 EGP at Carrefour yesterday"}
```

Example target shape:

```json
{
  "transactions": [{
    "amount": 450,
    "currency": "EGP",
    "type": "expense",
    "merchant": "Carrefour",
    "date": "2026-10-08"
  }]
}
```

The AI result is not automatically persisted financial truth.

## What We Are Learning

- typed Python;
- FastAPI contracts/DI/OpenAPI;
- async HTTP;
- provider abstraction;
- structured LLM outputs;
- validation;
- retries/timeouts;
- idempotency;
- caching;
- async-job concepts;
- AI evals;
- capacity/load testing;
- ADRs and failure-mode analysis.

## Architecture v0

```text
Client
  ↓
FastAPI
  ↓
Application Service
  ↓
TransactionAIProvider
  ├─ FakeAIProvider
  └─ Real Provider
       ↓
  Structured Output Validation
       ↓
  Domain Mapping
       ↓
  API Response
```

The internal structure should evolve only when responsibilities exist. Do not create layers for appearance.

## Planned API

### GET /health
Day 01.

### POST /v1/transactions/parse
Day 02 onward.

### POST /v1/transactions/parse/jobs
### GET /v1/jobs/{id}
Day 09 educational async prototype. In-process state is intentionally not production durable.

## Setup

```bash
uv sync
uv run uvicorn ai_transaction_gateway.main:app --reload
```

Later:

```bash
uv run pytest
uv run ruff check .
uv run mypy src
```

## Python

`>=3.14,<3.15`

If a required dependency has a verified incompatibility, document evidence/decision before changing the version.

## Runtime Dependencies

- FastAPI
- Uvicorn
- HTTPX
- pydantic-settings

## Development

- pytest
- pytest-asyncio
- Ruff
- mypy
- Locust

## Test Strategy

1. domain/application unit tests;
2. fake provider;
3. mocked provider adapter tests;
4. API tests;
5. failure-path tests;
6. eval corpus;
7. load tests using fake provider.

Normal tests must not depend on paid/live model calls.

## Privacy/Security

- synthetic financial examples only;
- no real SMS/bank data;
- no secrets;
- avoid raw sensitive logging;
- model output is untrusted and validated.

## Monyvi Relationship

Compare the lab against Monyvi's existing architecture. Do not assume Python is better.

At Day 14 answer:
- What does a separate Python service materially improve?
- What extra network/deployment/secret/observability complexity does it add?
- Could the current Edge Function architecture meet the same need more simply?
- Is a polyglot boundary justified?

## Portfolio Ready When

- clean clone setup works;
- meaningful tests;
- fake + real provider;
- timeout/retry/idempotency documented;
- eval corpus + baseline;
- load evidence;
- architecture/capacity/failure docs;
- ADRs;
- architecture review complete.

## References

- https://www.python.org/downloads/release/python-3140/
- https://docs.astral.sh/uv/
- https://fastapi.tiangolo.com/tutorial/body/
- https://fastapi.tiangolo.com/tutorial/dependencies/
- https://fastapi.tiangolo.com/tutorial/background-tasks/
- https://www.python-httpx.org/async/
- https://pytest-asyncio.readthedocs.io/
- https://docs.locust.io/
