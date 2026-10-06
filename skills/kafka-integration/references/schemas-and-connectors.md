# Schemas and connectors

Use this reference for event contracts, schema changes, Kafka Connect, or
Kafka Streams design and review.

## Schemas and compatibility

- Identify the serialization format, schema ownership, compatibility policy,
  and how producers and consumers discover schemas.
- Check additions, removals, type changes, defaults, required fields, and
  semantic changes against the selected compatibility policy and deployed
  clients.
- Plan rollout order across producers and consumers. Account for old and new
  versions running concurrently and for retained records consumed later.
- Validate compatibility with the actual schema tooling and policy. Do not
  infer compatibility solely from a schema diff.

## Kafka Connect

- Identify connector type, source or sink behavior, task parallelism, offset
  and state handling, retry behavior, and supported configuration for the
  connector and service versions.
- Review delivery and idempotency at both Kafka and the external system
  boundary. Connector retries can result in duplicate effects depending on
  connector behavior.
- Define ownership for connector deployment, credentials, errors, restarts,
  upgrades, and dead-letter behavior.

## Kafka Streams

- Identify the processing topology, state stores, changelog and repartition
  topics, processing guarantees, and external side effects.
- Assess state recovery, task reassignment, local storage, scaling, and the
  impact of topology or application changes on existing state.
- Verify guarantees and configuration against the deployed Kafka Streams
  version and the target cluster capabilities.
