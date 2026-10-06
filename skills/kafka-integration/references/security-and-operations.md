# Security and operations

Use this reference when reviewing access control, secret handling, monitoring,
capacity signals, alerting, or incident response.

## Security

- Review TLS in transit, client authentication, authorization, network
  boundaries, and least-privilege access for each producer, consumer,
  connector, and operator.
- Define secret provisioning, rotation, and access. Do not place credentials
  in source code, examples, logs, or shared diagnostic output.
- Ask users to redact tokens, passwords, private endpoints, customer payloads,
  and sensitive identifiers from configurations and logs.
- Verify authentication mechanisms and authorization behavior for the actual
  Kafka distribution, client, and managed service.

## Operations

Select signals that reflect the service objectives and have an actionable
response. Depending on the design, monitor:

- Produce errors, request latency, throughput, and buffer pressure
- Consumer lag, processing latency, commit failures, and rebalance churn
- Under-replicated or offline partitions and broker availability
- Disk usage, network throughput, storage growth, and capacity headroom
- Connector task or stream processor health and error rates
- Retry and dead-letter volume, schema failures, and downstream availability

For each alert, define its threshold or objective, owner, response, and
escalation. Validate monitoring and recovery procedures with failure tests or
operational exercises appropriate to the environment.
