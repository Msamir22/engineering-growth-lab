# Failure Modes

| Failure | Behavior | Retry? | Result | Observe |
|---|---|---|---|---|
| connect timeout | bound wait | maybe | mapped error | timeout counter |
| read timeout | bound wait | maybe | mapped error | latency/timeout |
| provider 429 | bounded policy | usually limited | exhausted/retry | rate-limit metric |
| provider 5xx | selected transient retry | bounded | unavailable | status metric |
| provider 4xx | usually non-transient | usually no | config/request error | alert/log |
| malformed structured output | reject | policy-dependent | validation error | schema metric |
| domain-invalid output | reject safely | usually no blind retry | domain error | domain metric |
| restart with in-memory jobs | jobs lost | N/A | prototype limitation | restart |
| multi-instance local cache | inconsistent copies | N/A | documented limitation | cache metrics |
| same idempotency key/different payload | reject | no | conflict | audit metric |

## Day 06 Retry Budget

Decide:
- attempts;
- retryable errors;
- base delay;
- jitter;
- total timeout budget;
- prevention of nested retry amplification.
