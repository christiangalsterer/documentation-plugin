# Kafka design review

Use this reference to assess a proposed Kafka integration against its
requirements. Establish the system boundary and distinguish stated
requirements from assumptions before evaluating choices.

## Requirements and boundaries

- Identify producers, consumers, Kafka clusters, connectors or stream
  processors, downstream systems, and ownership boundaries.
- Record message volume, peak rate, message size, latency targets, retention,
  ordering scope, durability expectations, availability targets, and recovery
  objectives when they affect the design.
- Identify broker version, client library and version, deployment model, and
  managed-service tier where behavior depends on them.
- State which requirements are hard constraints and which are preferences.

## Review dimensions

- **Message flow:** Trace record creation, key assignment, production,
  replication, consumption, offset handling, side effects, and replay.
- **Partitioning and ordering:** Confirm the key expresses the required
  ordering boundary and assess skew, hot partitions, and parallelism.
- **Delivery and effects:** Define the guarantee at each boundary. Consider
  producer retries, acknowledgments, consumer commit timing, transactions,
  idempotency, and external side effects.
- **Failure and recovery:** Identify component failures, retry behavior,
  poison-record handling, replay implications, and recovery objectives.
- **Lifecycle and capacity:** Review retention or compaction, replication,
  storage, throughput, quotas, and failure headroom.
- **Contracts and ownership:** Establish schema compatibility, rollout order,
  topic ownership, access policies, and operational responsibilities.
- **Operations:** Identify service-level indicators, actionable alerts, and
  who responds to them.

## Recommendation

Prefer a concrete design that satisfies the stated constraints and makes
tradeoffs explicit. Record unresolved questions separately. Do not treat
retention as a backup or disaster-recovery plan, and do not infer a guarantee
from a configuration option without considering the whole message path.
