# System Architecture Overview

## High Level Summary

The platform is built as a set of microservices communicating over gRPC internally and REST/GraphQL externally. Services are deployed on Kubernetes across three regions (us-east-1, eu-west-1, ap-southeast-1) for redundancy and latency reduction.

## Core Services

### API Gateway
Built on Envoy, the API Gateway handles routing, rate limiting, authentication token validation, and request logging. All external traffic passes through the gateway before reaching internal services.

### Auth Service
Handles user authentication and authorization using OAuth 2.0 and JWT tokens. Tokens are short lived (15 minutes) with refresh tokens valid for 30 days. Auth service is backed by a PostgreSQL cluster with read replicas in each region.

### Catalog Service
Manages product catalog data, including search indexing via Elasticsearch. Catalog updates are published to a Kafka topic and consumed by the search indexer, recommendation engine, and cache invalidation service.

### Order Service
Handles order creation, state transitions, and payment orchestration. Uses a saga pattern to coordinate distributed transactions across inventory, payment, and shipping services, with compensating transactions for rollback on failure.

### Notification Service
Sends email, SMS, and push notifications. Consumes events from Kafka and applies user notification preferences before dispatching through third party providers (SendGrid for email, Twilio for SMS).

## Data Storage

- **PostgreSQL**: Primary transactional data store for orders, users, and auth.
- **Elasticsearch**: Product search and full text queries.
- **Redis**: Session caching and rate limit counters.
- **S3**: Object storage for user uploads, product images, and generated reports.
- **Kafka**: Event streaming backbone connecting services asynchronously.

## Deployment Pipeline

Code is built and tested via GitHub Actions. Merged changes to main trigger a build, run the full test suite, and produce a container image tagged with the commit SHA. Deployment to staging is automatic; production deployment requires manual approval from an on call engineer and follows a canary rollout strategy, shifting traffic in 10% increments over 30 minutes while monitoring error rates.

## Observability

Metrics are collected via Prometheus and visualized in Grafana. Distributed tracing uses OpenTelemetry, exported to a Jaeger backend. Logs are shipped to a centralized ELK stack with a 30 day retention window for standard logs and 1 year retention for audit logs.

## Disaster Recovery

Each region maintains an independent copy of critical data with cross region replication for PostgreSQL (async, typically under 2 second lag) and S3 (versioned, cross region replication enabled). RTO target is 15 minutes, RPO target is 5 minutes for the primary transactional database.
