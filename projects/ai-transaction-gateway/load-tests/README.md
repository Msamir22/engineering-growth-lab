# Load Tests

Introduced Day 12.

Start with FakeAIProvider to isolate application behavior from provider quotas/network/cost.

Every benchmark must record:
- commit SHA;
- machine/environment;
- provider mode;
- simulated provider latency;
- users/spawn rate/duration;
- requests;
- failure rate;
- p50/p95/p99 when available.

Never publish a performance number without its configuration.
