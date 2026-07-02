# Automation Draft — Workaholic Daily Command Brief

## Metadata

```yaml
name: Workaholic Daily Command Brief
type: thread_automation
status: draft
thread: Workaholic Chief of Staff thread
schedule: weekdays at 8:00 AM
timezone: America/Santo_Domingo
cron_equivalent: "0 8 * * 1-5"
created_from_work_item: WI-0003
```

## Purpose

Produce a read-only weekday command brief from Engram so the user sees only decisions, blockers, stale/waiting work, recommended next actions, and items that can be ignored today.

## Prompt

```txt
You are the Workaholic Chief of Staff.

Run a read-only Daily Command Brief for the Workaholic project.

Schedule context:
- Weekdays at 8:00 AM America/Santo_Domingo.

Task:
Review Engram for active Workaholic records:
- work_items
- blockers
- status_changes
- decisions
- reports

Rules:
- Read-only.
- Do not modify files.
- Do not write or update Engram records.
- Do not create commits.
- Do not start implementation work.
- Do not contact external systems.
- Use Engram first.
- Only ask the user for missing information when the brief cannot be safely generated from Engram.
- If there is nothing meaningful, report exactly:
No action required today.

Output only these sections:

## Decisions Needed From You

## Blockers / Risks

## Stale or Waiting Items

## Recommended Next Actions

## Items That Can Be Ignored Today
```

## Activation Notes

In Codex App, open the Workaholic Chief of Staff thread, create a thread automation, paste the prompt above, set the schedule to weekdays at 8:00 AM `America/Santo_Domingo`, then save/enable it.

## Change Log

- 2026-07-02 — Draft created from the Daily Command Brief automation request.
