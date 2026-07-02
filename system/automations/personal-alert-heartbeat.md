# Automation Template — Personal Alert Heartbeat

## Metadata

```yaml
name: Personal Alert Heartbeat
type: thread_automation
status: draft
audience: user_only
cadence: every 90 minutes
active_days: weekdays
active_window: 08:00-18:00
timezone: America/Santo_Domingo
position_in_operating_layers: 4
created_from_work_item: WI-0006
```

## Purpose

Produce short personal alerts for the user only. These are not stakeholder notifications.

This is the fourth automation layer after:

1. Daily Command Brief
2. EOD Closeout
3. Manual INTAKE
4. Personal Alert Heartbeat

## Cadence

- Weekdays only.
- Every 90 minutes.
- Only between 8:00 AM and 6:00 PM `America/Santo_Domingo`.
- Do not run overnight.
- Start with 90 minutes.
- Consider hourly only if signal quality is good.

## Triggers

- `READY_FOR_REVIEW`
- `READY_FOR_MR`
- `READY_FOR_DEPLOY`
- `CERTIFICATION_FAILED`
- `BLOCKED`
- `DECISION_NEEDED`
- `APPROVAL_NEEDED`
- `DELIVERY_RISK`
- `READY_TO_CLOSE`

## Prompt

```txt
You are the Workaholic Personal Alert Heartbeat.

Use Engram first.

Purpose:
Produce very short personal alerts for the user only. These are not stakeholder notifications.

Rules:
- Use Engram first.
- Output must be very short.
- No long summaries.
- No implementation work.
- No external messages.
- Do not modify files.
- Do not create commits.
- Do not contact external systems.
- If nothing matters, output exactly:
No personal alerts right now.

Look for these alert triggers:
- READY_FOR_REVIEW
- READY_FOR_MR
- READY_FOR_DEPLOY
- CERTIFICATION_FAILED
- BLOCKED
- DECISION_NEEDED
- APPROVAL_NEEDED
- DELIVERY_RISK
- READY_TO_CLOSE

Default output shape:

## Personal Alerts

- [TYPE] WI-0000 — concise action needed

Expanded format only when needed:

## Personal Alert
Type:
Work item:
Project:
Why now:
Action needed from you:
Recommended response:
```

## Activation Notes

Create this as a thread automation in the Workaholic Chief of Staff thread. Schedule it weekdays every 90 minutes between 8:00 AM and 6:00 PM `America/Santo_Domingo`. Do not run overnight.

## Change Log

- 2026-07-02 — Draft created as the fourth Workaholic automation layer.
