# ADR 003: Choice of Message Queue Technology

**Status:** Accepted
**Date:** 2024-08-12
**Deciders:** Platform Architecture Team

## Context

As the platform grew past 12 microservices, synchronous REST calls between services created tight coupling and cascading failure risk during traffic spikes. We needed an asynchronous messaging backbone to decouple services, support event driven workflows, and provide durable delivery guarantees.

## Decision

We chose Apache Kafka as the primary message queue and event streaming platform, over alternatives RabbitMQ and AWS SQS/SNS.

## Alternatives Considered

**RabbitMQ**: Strong support for complex routing patterns and lower operational complexity than Kafka, but weaker support for event replay and long term retention, which was important for our audit and analytics use cases.

**AWS SQS/SNS**: Fully managed, minimal operational overhead, but lacks native support for consumer groups and ordered partitioned consumption, which several of our use cases (order state transitions, inventory updates) require for correctness.

**Kafka**: Higher operational complexity, requiring dedicated expertise to run well, but offers log based retention allowing event replay, strong ordering guarantees within partitions, high throughput, and a mature ecosystem (Kafka Connect, Kafka Streams) that aligned with our anticipated growth in event volume.

## Consequences

Positive: Enabled event replay for debugging and backfilling downstream systems. Supported the growth from 12 to 40+ services without a redesign of the messaging layer. Enabled the analytics team to build a real time data pipeline directly off production event streams.

Negative: Required hiring a dedicated platform engineer with Kafka operations experience. Added operational overhead for cluster management, though this was later mitigated by migrating to Confluent Cloud (managed Kafka) in 2025.

## Follow Up

Revisit this decision if event volume exceeds current cluster capacity planning (see capacity_planning.md) or if managed Kafka costs exceed self hosted costs by a significant margin.
