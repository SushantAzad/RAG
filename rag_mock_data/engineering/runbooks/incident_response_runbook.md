# Incident Response Runbook

## Severity Levels

- **SEV1**: Complete outage or data loss affecting all users. Immediate response required, all hands.
- **SEV2**: Significant degradation affecting a large subset of users or a core feature is unavailable.
- **SEV3**: Minor issue affecting a small subset of users or a non critical feature.
- **SEV4**: Cosmetic issue or minor bug with no meaningful user impact.

## Response Steps

1. **Acknowledge** the page within 5 minutes via PagerDuty. Failure to acknowledge within 10 minutes escalates to the secondary on call.
2. **Assess severity** using the criteria above and update the incident channel topic in Slack (#incidents) with the severity level.
3. **Declare the incident** by running `/incident declare` in Slack, which creates a dedicated channel, a Zoom bridge, and a status page draft.
4. **Assign roles**: Incident Commander (IC), Communications Lead, and Subject Matter Expert(s). The person who acknowledged the page is IC by default unless they explicitly hand off.
5. **Mitigate first, root cause later.** Prioritize restoring service (rollback, feature flag disable, traffic shift) over full root cause analysis during the active incident.
6. **Communicate** status updates every 30 minutes for SEV1/SEV2 incidents, both internally in the incident channel and externally on the status page if customer facing.
7. **Resolve** once metrics confirm the issue is mitigated. Keep the incident channel open for at least 30 minutes post resolution to watch for recurrence.
8. **Postmortem** is required for all SEV1 and SEV2 incidents, due within 5 business days, following the postmortem template in the engineering wiki.

## Common Mitigations by Symptom

| Symptom | First Action |
|---|---|
| Elevated 5xx errors after deploy | Roll back the most recent deployment |
| Database connection pool exhaustion | Scale read replicas, check for long running queries |
| Kafka consumer lag spiking | Scale consumer group, check for a poison message |
| Elevated latency, no recent deploy | Check upstream third party provider status pages |
| Full disk on a node | Trigger log rotation, cordon and drain the node |

## Escalation Contacts

Primary on call rotation is managed in PagerDuty under the "platform-oncall" schedule. Secondary escalation goes to the Engineering Manager on call, listed in the #eng-leadership Slack channel topic. For security related incidents, page the security team directly using the "security-oncall" PagerDuty schedule in addition to standard escalation.
