# Partitioning and capacity

Use this reference for key selection, ordering, parallelism, throughput,
storage planning, or capacity under failure.

## Partitioning and ordering

- Define the ordering boundary first. Kafka ordering is scoped to a partition;
  a key is commonly used to keep related records on the same partition.
- Check whether keys distribute traffic evenly. A dominant key can create a
  hot partition even when cluster-wide capacity appears sufficient.
- Relate partition count to desired consumer parallelism and per-partition
  processing capacity. More partitions also affect metadata, file handles,
  recovery, and operational overhead.
- Evaluate partition-count changes carefully. Depending on partitioner and
  client behavior, changing the count can map a key to a different partition
  and affect ordering across the change.

## Capacity and availability

- Estimate peak rather than only average record rate and account for message
  size, compression, batching, replication traffic, and consumer fan-out.
- Estimate retained storage from ingress, retention or compaction behavior,
  replication, and expected growth. Include recovery and rebuild headroom.
- Include quotas, network and disk throughput, broker and partition limits,
  and the failure domains available in the target deployment.
- Model capacity during broker or zone loss and during consumer catch-up or
  replay, not only during steady state.
- Validate estimates with representative load tests and measured service
  behavior. Do not present an estimate as a benchmark.
