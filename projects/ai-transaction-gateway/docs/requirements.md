# Requirements

## Problem

A client submits natural-language financial text. The service returns structured transaction **candidates**.

AI output is not automatically persisted financial truth.

## Initial Functional Requirements

- FR-1 accept natural-language transaction text;
- FR-2 return zero/one/multiple candidates;
- FR-3 represent amount/currency/type/merchant/date when available;
- FR-4 reject invalid client input;
- FR-5 support deterministic fake provider;
- FR-6 expose health;
- FR-7 later expose educational job flow;
- FR-8 later support idempotent duplicate handling.

## NFR Categories — Refine Day 01

- latency;
- availability;
- reliability;
- validation/correctness;
- privacy;
- observability;
- cost;
- scalability.

For every numeric target explain why it is reasonable.

Questions:
- What p95 is acceptable when provider latency dominates?
- Total timeout?
- What happens on malformed model output?
- What can be logged?
- Maximum input length and why?

## Out of Scope Sprint 01

- real Monyvi persistence;
- personal bank/SMS data;
- full auth architecture;
- production Redis/queue;
- cloud deployment.

## Assumptions

- production scale values are hypothetical exercises;
- financial data is synthetic;
- assumptions must be documented rather than hidden in code.
