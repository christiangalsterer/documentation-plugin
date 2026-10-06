# Kafka integration design review

Adapt or remove sections that do not apply. Replace prompts with verified
facts, and label assumptions and unresolved questions.

## Goal and scope

- Use case:
- In-scope components and boundaries:
- Required outcome:

## Environment and constraints

- Kafka distribution, broker version, and deployment model:
- Client libraries and versions:
- Managed service and tier, if applicable:
- Throughput, peak message size, and latency requirements:
- Ordering, retention, delivery, availability, and recovery requirements:
- Other constraints:

## Design and message flow

Describe producers, topics, keys and partitioning, replication, consumers,
offset handling, downstream effects, and replay.

## Guarantees and failure behavior

- Delivery behavior at each boundary:
- Ordering scope:
- Idempotency, transactions, or deduplication:
- Retry and poison-record handling:
- Failure and recovery behavior:

## Operations and security

- Signals and alerts:
- Capacity and failure headroom:
- Access control and secret handling:
- Ownership and incident response:

## Recommendation

- Recommended design:
- Tradeoffs and risks:
- Validation steps:
- Version- or service-specific details to verify:
- Open questions:
