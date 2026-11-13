# Alerts

Turn recent alerts into an assessment backed by evidence. This is an
investigation, not permission to fix anything.

1. Inventory every alert in the window and cluster repeats by likely cause:
   service, error, endpoint, where the stack starts. Keep the count and the
   first and last time. Don't drop the quiet ones.
2. Correlate with what actually ran: logs, traces, deploys, data. Start narrow
   around the alert time and widen only as needed.
3. Trace the path in the source the deployed service really runs. Local `HEAD`
   is not what is deployed, and the service that logged an error is not always
   its source.
4. Assess each cluster, evidence before labels:
   - magnitude, from blast radius and user impact, not message count
   - status: ongoing, likely resolved, confirmed resolved, or unknown
   - recurrence risk, with one concrete reason
   - confidence, from how well the sources agree
   - the smallest useful next action
5. Say how the alert itself could be better, only where this window showed a
   gap: grouping, severity, a missing owner or link, no recovery signal.

Separate what you observed from what you infer. Alert volume is not occurrence
volume, no newer alert is not proof of recovery, and an unexplained transient
is not low risk because it stopped.

Order by ongoing user impact, then recurrence risk, then frequency.
