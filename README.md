# Engineering Growth Lab

A hands-on career-development laboratory for building Lead/Staff-level engineering skills through real system design, backend, AI, architecture, and production-quality prototypes.

This repository is the persistent source of truth for the learning program. ChatGPT/Zalata can use it to review progress, update plans, inspect implementations, and continue from the latest checkpoint without relying only on chat history.

## Current Sprint

**Sprint 01 — System Design + Python/FastAPI + AI Engineering**

- Duration: 2 weeks / 14 learning days
- Time budget: ~4 hours/day, ~25–30 hours/week
- Primary project: [AI Transaction Gateway](projects/ai-transaction-gateway/README.md)
- Applied design exercises:
  - [Warehouse Appointment Scheduling](design-exercises/warehouse-appointment-system.md)
  - [Yard Live Tracking](design-exercises/yard-live-tracking.md)
- Full sprint plan: [PLAN.md](sprints/01-system-design-fastapi-ai/PLAN.md)
- Progress: [PROGRESS.md](PROGRESS.md)

## Learning Philosophy

- ~25% focused study; ~75% designing, coding, testing, measuring, and documenting.
- Every day should produce evidence: code, tests, ADR, diagram, benchmark, eval result, or written design.
- AI is a tutor/reviewer/interviewer, not a substitute for the learner's first attempt.
- Architecture choices require explicit trade-offs.
- Do not introduce technology just because it is fashionable.
- MR/YMS exercises are sanitized. Never publish proprietary Capstone code, customer data, private architecture, credentials, or confidential details.
- CV/portfolio claims stay locked until the matching work exists and can be demonstrated.

## Long-Term Learning Order

1. System Design
2. Security + Scaling + Architecture
3. Python + FastAPI + AI Engineering
4. Advanced AI agents / tool calling / MCP / evals
5. React + Next.js
6. .NET + advanced backend fundamentals
7. PostgreSQL + Redis + Docker
8. Azure + CI/CD + observability
9. Leadership + interviews
10. Job search + freelance pipeline

System Design and Python/FastAPI/AI are intentionally running in parallel in Sprint 01.

## Repository Structure

```text
engineering-growth-lab/
├── README.md
├── ROADMAP.md
├── PROGRESS.md
├── sprints/
│   └── 01-system-design-fastapi-ai/
│       ├── PLAN.md
│       ├── DAY-01.md ... DAY-14.md
│       └── RETROSPECTIVE.md
├── projects/
│   └── ai-transaction-gateway/
│       ├── README.md
│       ├── pyproject.toml
│       ├── .python-version
│       ├── src/
│       ├── tests/
│       ├── evals/
│       ├── load-tests/
│       └── docs/
│           ├── requirements.md
│           ├── architecture.md
│           ├── capacity.md
│           ├── failure-modes.md
│           └── adr/
└── design-exercises/
    ├── warehouse-appointment-system.md
    └── yard-live-tracking.md
```

## Tutor Workflow

For each day:

1. Open that day's file.
2. Attempt the pre-work/questions before requesting a final answer.
3. Ask the tutor to teach only the concepts needed.
4. Implement/design the assignment.
5. Commit the first attempt.
6. Request Staff/Principal-style review.
7. Fix verified defects.
8. Record evidence and lessons in the day file and PROGRESS.md.
9. Move on only when the exit criteria are met.

## Sprint 01 Tooling Baseline

- Python 3.14 (project constraint: `>=3.14,<3.15`)
- uv
- FastAPI
- Pydantic v2
- HTTPX
- pytest + pytest-asyncio
- Ruff
- mypy
- Locust

## Engineering Rules

- Type public Python interfaces.
- Treat model output as untrusted external input.
- Never commit secrets or personal financial data.
- Test failure paths, not only happy paths.
- Use async only where it helps I/O-bound concurrency.
- State assumptions/uncertainty in architecture docs.
- Performance/eval claims must include configuration.
- Keep the simplest architecture that meets stated requirements.

## Verified Primary References

- Python 3.14: https://www.python.org/downloads/release/python-3140/
- uv Python/project management: https://docs.astral.sh/uv/concepts/python-versions/
- FastAPI request models: https://fastapi.tiangolo.com/tutorial/body/
- FastAPI dependencies: https://fastapi.tiangolo.com/tutorial/dependencies/
- FastAPI background tasks: https://fastapi.tiangolo.com/tutorial/background-tasks/
- HTTPX async: https://www.python-httpx.org/async/
- pytest-asyncio: https://pytest-asyncio.readthedocs.io/
- Locust: https://docs.locust.io/

## Success Definition

This repository should become evidence that Mohamed can:

- turn ambiguous requests into requirements/NFRs;
- estimate capacity and identify bottlenecks;
- design API/data boundaries;
- reason about consistency, idempotency, retries, caching, and queues;
- implement typed, testable backend services;
- validate and evaluate AI outputs;
- measure latency/load rather than hand-wave performance;
- defend architecture decisions and trade-offs in Lead/Staff interviews.
