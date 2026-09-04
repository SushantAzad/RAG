# On Call Escalation Matrix

This document lives one level deeper than the other runbooks, useful for testing retrieval across nested directory depths.

## Escalation Path

1. **Primary On Call** — First responder, paged immediately for all severities
2. **Secondary On Call** — Paged automatically if Primary does not acknowledge within 10 minutes
3. **Engineering Manager On Call** — Paged for SEV1/SEV2 incidents lasting longer than 30 minutes, or automatically if Secondary does not acknowledge within 15 minutes
4. **VP Engineering** — Paged for SEV1 incidents lasting longer than 60 minutes, or any incident involving customer data exposure

## Rotation Schedule

Primary and Secondary rotations are weekly, handed off every Monday at 9:00 AM in the assigned team's primary time zone. The rotation schedule is managed in PagerDuty and synced to each engineer's calendar automatically.

## Special Escalation Cases

- **Security incidents**: Always page the security on call in parallel with standard escalation, regardless of severity level
- **Data privacy incidents** (potential PII exposure): Page the Data Protection Officer directly in addition to standard escalation
- **Payment processing incidents**: Page the Payments team lead directly, since payment issues often require coordination with external processors on a separate incident timeline
