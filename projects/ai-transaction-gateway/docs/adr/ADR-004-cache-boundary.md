# ADR-004 — Cache Boundary

**Status:** Open — decide Day 08

Questions:
- what is safe to cache?
- key includes prompt/model/config/account/category/time context?
- what about "today"/"yesterday"?
- TTL?
- sensitive input/privacy?
- what happens with multiple instances?

Experiment with in-memory TTL cache only after key assumptions are explicit.

Never describe process-local cache as a distributed production cache.
