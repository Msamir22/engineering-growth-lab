# System Design — Warehouse Appointment Scheduling

Generic/sanitized MR-inspired exercise. No proprietary Capstone details.

## Problem
Warehouses have docks/time windows. Users/carriers create, reschedule, and cancel appointments. The same capacity cannot be double-booked. Changes should be auditable.

## Day 07 Work

### Clarifying Questions
Write at least 10:
- fixed slot length?
- dock capacity >1?
- approval flow?
- time zones?
- temporary holds?
- availability freshness?
- cancellation rules?
- read vs booking correctness priority?

### Functional Requirements
TBD

### NFRs
Include consistency, latency, availability, scale, auditability.

### Hypothetical Capacity
Choose and label assumptions:
- warehouses;
- docks/warehouse;
- bookings/day;
- peak booking RPS;
- read/write ratio.

### API
Availability/create/reschedule/cancel/get.

### Data Model
Warehouse, Dock, Appointment, Carrier/User, AuditEvent.

### Concurrency Deep Dive
Two simultaneous requests target the same dock/time.

Compare:
- DB unique/exclusion constraint;
- pessimistic lock;
- optimistic concurrency/version;
- distributed lock.

Do not automatically combine all mechanisms.

### Failure Scenarios
- duplicate retry;
- DB timeout after ambiguous commit;
- reschedule race;
- stale availability;
- notification failure after successful booking.

### Tutor Challenge
- what needs strong consistency?
- what can be eventual?
- does Redis guarantee booking correctness?
- idempotency design?
- 10x scale?
