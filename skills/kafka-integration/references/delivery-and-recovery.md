# Delivery and recovery

Use this reference when evaluating producer or consumer reliability,
processing guarantees, retries, external effects, replay, or recovery.

## Trace the guarantee

State the guarantee separately for each boundary: application to producer,
producer to broker, broker storage and replication, consumer processing,
offset commit, and downstream side effect. End-to-end behavior depends on the
whole path.

- **At-most-once:** Committing before processing can lose work if processing
  fails after the commit.
- **At-least-once:** Processing before committing can replay work if the
  consumer fails before its commit is recorded. Handlers and side effects may
  need idempotency or deduplication.
- **Transactional processing:** Kafka transactions can coordinate supported
  Kafka reads, writes, and offsets within their defined scope. They do not by
  themselves make arbitrary external side effects exactly once.

## Producers and consumers

- Review acknowledgments, idempotence, retries, delivery timeouts, batching,
  buffer pressure, and asynchronous send-error handling for the actual client
  and service.
- Review offset commit timing, processing concurrency, rebalance handling,
  backpressure, and what replay means to downstream systems.
- For external effects, consider idempotency keys, deduplication, an outbox,
  or another coordination pattern appropriate to the system boundary.

## Retries, poison records, and replay

- Bound retries and define delay, ownership, and observability. Avoid retry
  loops that consume unbounded resources or hide persistent failures.
- Decide how to handle poison records, including whether the requirement to
  preserve order prevents moving past a failed record.
- Define dead-letter handling explicitly: destination, metadata retained,
  access controls, ownership, alerting, retention, and safe replay procedure.
- Estimate replay volume and its effect on downstream capacity and ordering.
- Test recovery from partial processing, restarts, and duplicate delivery.
