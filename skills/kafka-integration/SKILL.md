---
name: kafka-integration
description: >-
  Design, implement, review, and troubleshoot Apache Kafka integrations.
  Use for producers, consumers, topics, partitions, delivery semantics,
  Kafka Connect and Streams, schemas, security, operations, recovery, and
  Kafka-compatible managed services. Works as a standalone guide for people
  or as reusable Kafka-specific guidance for agents and other skills.
metadata:
  author: Christian Galsterer
  version: "1.0.0"
---

# Kafka integration

Use this skill to reason about Kafka integration behavior and tradeoffs. It is
usable directly by a human or as domain guidance for another agent or skill.
For Kafka documentation, use this skill to establish and verify technical
content, then use `tech-writer` for document structure and writing conventions.

## Workflow

1. **Identify the task and boundary.** Determine whether the user needs a
   conceptual answer, design, implementation guidance, review, migration, or
   troubleshooting. Identify which applications, Kafka components, and
   downstream systems are in scope.
2. **Gather decision-relevant context.** Establish requirements and constraints
   that could change the recommendation. Depending on the task, this may
   include broker and client versions, deployment or managed-service type,
   throughput, peak message size, latency, ordering scope, retention, delivery
   expectations, availability, and recovery objectives.
3. **Ask or proceed with assumptions.** Ask concise questions only when a
   missing fact could materially change the answer. Otherwise, state
   assumptions and give a useful initial recommendation. Do not make users
   provide irrelevant details before answering a focused question.
4. **Trace the relevant message flow.** Consider key and partition selection,
   producer acknowledgments and retries, broker replication, consumer
   assignment and offset commits, downstream side effects, and replay or
   recovery as applicable.
5. **Evaluate behavior under failure.** Check the relevant failure cases,
   such as broker or zone loss, producer errors, consumer restarts and
   rebalances, poison records, schema incompatibility, downstream outages,
   lag growth, or replay. Use the references below when they apply.
6. **Recommend and qualify.** Give a concrete recommendation, its tradeoffs,
   operational consequences, and validation steps. Separate confirmed facts
   from assumptions and risks. Qualify version- or service-specific claims.
7. **Adapt the output.** Answer a focused question directly. For substantial
   design reviews or incidents, use the corresponding template if it helps;
   templates are optional and should be adapted to the request.

## Choose relevant references

Load only the references needed for the task:

- [Design review](references/design-review.md) for requirements, architecture,
  and tradeoff analysis.
- [Delivery and recovery](references/delivery-and-recovery.md) for producer or
  consumer reliability, processing guarantees, retries, and replay.
- [Partitioning and capacity](references/partitioning-and-capacity.md) for
  ordering, keys, throughput, storage, and failure headroom.
- [Schemas and connectors](references/schemas-and-connectors.md) for schema
  evolution, Kafka Connect, and Kafka Streams.
- [Security and operations](references/security-and-operations.md) for access
  controls, monitoring, and operational diagnosis.
- [Managed services](references/managed-services.md) when the target is a
  Kafka-compatible service or a managed Kafka offering.

Optional starting points:

- [Design review template](templates/design-review.md)
- [Troubleshooting template](templates/troubleshooting.md)

## Use with other agents and skills

Treat this skill as the source of reusable Kafka-specific workflow and review
criteria. Another agent can apply it while retaining its own role, tools, and
output conventions. A documentation skill can consume verified Kafka facts
from this skill and apply its own structure and style rules. A human can use
the workflow and linked checklists directly; no agent persona is required.

## Boundaries

- Do not assume a Kafka-compatible API supports every Apache Kafka feature or
  provides identical semantics. Verify support for the target service and tier.
- Do not claim global ordering, exactly-once effects across arbitrary systems,
  automatic dead-lettering, or unlimited retention without a design that
  establishes those properties.
- Do not prescribe production settings as universal defaults. Explain the
  dependencies and tradeoffs, and label examples as examples.
- Do not invent benchmark results, service limits, configuration properties,
  or version support. Check current authoritative documentation when tools are
  available. If they are not, say which details need verification.
- Treat credentials, customer payloads, and production identifiers as
  sensitive. Ask for sanitized configurations and logs; do not request or
  repeat secrets.

## Response checklist

For substantial design or review work, cover the relevant items below:

- Recommendation and assumptions
- Components and end-to-end message flow
- Delivery, ordering, and side-effect behavior
- Failure, replay, and recovery behavior
- Tradeoffs and operational signals
- Validation steps and version- or service-specific details to verify

Skip irrelevant items. For focused questions, answer directly and include only
the caveats needed for correctness.
