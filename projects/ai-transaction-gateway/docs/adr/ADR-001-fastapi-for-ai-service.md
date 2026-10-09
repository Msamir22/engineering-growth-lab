# ADR-001 — FastAPI for the AI Lab

**Status:** Proposed

## Context
We need hands-on Python/API/async/AI engineering while keeping production Monyvi unchanged.

## Decision
Use Python + FastAPI for this standalone learning service.

## Alternatives
- TypeScript/Edge Function: fewer runtimes, but misses Python learning.
- ASP.NET Core: aligns with Capstone, scheduled later.

## Consequences
Positive: real Python/FastAPI practice and AI ecosystem access.  
Negative: another runtime and risk of assuming Python is automatically a production improvement.

## Review
Day 14: decide whether FastAPI solves a concrete Monyvi problem.
