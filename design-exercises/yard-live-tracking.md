# System Design — Yard Live Tracking

Generic/sanitized YMS-inspired exercise. No proprietary Capstone details.

## Problem
Show near-real-time trailer/asset state across warehouse yards.

Synthetic events:
- entered;
- moved;
- dock assigned;
- departed.

## Day 13

### Clarify
- yards?
- events/sec?
- freshness requirement?
- server→client only?
- must every event be seen?
- latest state vs history?
- reconnect behavior?

### Compare
Polling vs SSE vs WebSocket.

Evaluate:
- simplicity;
- freshness;
- request/connection overhead;
- full duplex need;
- operational complexity;
- reconnect/replay.

### Data
YardEvent, current asset state, sequence/version, timestamp, source.

### Architecture
Ingestion → processing → current state/history → real-time fan-out → client.

### Ordering/Duplicates
- duplicate events?
- out of order?
- per-asset ordering sufficient?
- how prevent old event overwriting new state?

### Failures
- disconnect;
- fan-out restart;
- duplicate/delayed event;
- spike;
- store outage.

### Optional Prototype
FastAPI SSE endpoint with synthetic events.

### Tutor Challenge
- why not 5-second polling?
- why not WebSocket?
- replay strategy?
- source of truth?
- 10x connected clients?
