# ADR-002 — AI Provider Abstraction

**Status:** Proposed

## Context
Deterministic tests need a fake provider; live behavior needs a real provider. Provider HTTP code in routes creates coupling.

## Decision
Define a narrow application-facing provider contract and implement:
- FakeAIProvider
- one real provider adapter

## Benefits
- deterministic tests;
- provider isolation;
- easier comparison;
- less provider leakage.

## Cost
Abstraction adds code and can become artificial.

## Guardrail
Do not invent a universal LLM framework. Model only this application's needs.
