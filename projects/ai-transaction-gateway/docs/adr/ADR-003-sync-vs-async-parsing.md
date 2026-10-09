# ADR-003 — Synchronous vs Job-Based Parsing

**Status:** Open — decide Day 09

## Synchronous
Pros: simple client flow, fewer components.  
Cons: caller waits on provider latency/failure.

## Job-Based
Pros: decoupling, potential durable retries/backpressure.  
Cons: queue/job persistence, status UX, operational complexity.

## Sprint Experiment
Implement an educational in-process job flow and document why it is not durable/distributed.

## Decision
TBD after experiment.
