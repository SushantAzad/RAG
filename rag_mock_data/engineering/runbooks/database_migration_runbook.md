# Database Migration Runbook

## Pre Migration Checklist

- Migration script has been reviewed and approved by at least one other engineer
- Migration has been tested against a staging database with production like data volume
- Rollback script exists and has been tested
- Migration is scheduled during a low traffic window (typically 2:00 AM to 4:00 AM in the primary user time zone)
- On call engineer is aware and available during the migration window

## Migration Types

### Additive Migrations (Low Risk)
Adding a new nullable column, adding a new table, or adding a new index (using `CREATE INDEX CONCURRENTLY` to avoid locking). These can generally run during business hours with standard review.

### Destructive Migrations (High Risk)
Dropping a column, dropping a table, or renaming a column. These require the following extended process:
1. Deploy code that stops using the column/table but does not remove it (a "soft deprecation" period of at least 2 weeks).
2. Confirm via query logs that the column/table has zero reads in the deprecation window.
3. Schedule the actual drop during a maintenance window with a database backup taken immediately beforehand.

### Data Backfills
Large backfills should be run in batches (recommended batch size: 5,000 rows) with a short sleep between batches to avoid replication lag and connection pool exhaustion. Monitor replication lag throughout using the `pg_stat_replication` dashboard in Grafana.

## Execution Steps

1. Take a manual database snapshot immediately before starting, in addition to the automated hourly snapshots.
2. Run the migration using the deployment pipeline's migration job, never manually against production.
3. Monitor the migration job logs in real time and watch the error rate and latency dashboards for the affected service.
4. Verify the migration completed successfully by running the post migration validation query included in the migration PR.
5. Update the migration tracking sheet in the engineering wiki with the completion timestamp and any anomalies observed.

## Rollback Procedure

If a migration causes issues, execute the paired rollback script immediately. For destructive migrations that have already dropped data, restore from the pre migration snapshot rather than attempting to reconstruct data, since partial reconstruction risks data inconsistency.

## Notes

Never run schema migrations and data backfills in the same deployment. Separate them so that a failure in one does not block or complicate rollback of the other.
