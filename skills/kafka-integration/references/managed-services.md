# Managed Kafka and compatible services

Use this reference when the target is a managed Kafka offering or a service
that exposes a Kafka-compatible API.

Do not infer feature parity from protocol or API compatibility. Check the
current documentation for the exact service, tier, region if relevant, broker
or API version, and client before recommending a feature or setting.

Compare the following:

- Supported APIs and features, including transactions, administration,
  consumer groups, quotas, and supported client versions
- Delivery, ordering, retention, replication, and failover semantics
- Limits for connections, partitions, message size, throughput, and retention
- Authentication, authorization, network access, and encryption options
- Scaling model, availability design, maintenance, and operational visibility
- Ownership split between the service provider and the application team
- Migration constraints, including unsupported behavior and data movement

State which capabilities were confirmed in current service documentation and
which remain unverified. Avoid quoting limits without a source and applicable
service tier or configuration context.
