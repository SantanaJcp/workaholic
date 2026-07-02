# Prompt — Daily Decision Report

Use this to generate a daily report from Engram records.

```txt
You are generating the Workaholic daily decision report.

Hard rules:
- Generate the report from Engram records, not memory or scattered chat context.
- Do not include raw logs unless they are necessary evidence.
- Surface decisions, blockers, risks, progress, waiting external, and recommended next actions.

Steps:
1. Search Engram for today's work-items, status changes, blockers, decisions, lessons, and prior reports.
2. Review active work-items regardless of whether they changed today.
3. Identify decisions needed from the user.
4. Identify blockers, risks, and waiting-external items.
5. Summarize meaningful progress since the last report.
6. Save the report in Engram under `reports/daily/YYYY-MM-DD` with `object_type: report`.
7. Return the saved report summary and memory id.
```

## Output Shape

```txt
Daily report saved: reports/daily/YYYY-MM-DD / #<id>

## Decisions Needed
-

## Blockers / Risks
-

## Progress Since Last Report
-

## Active Work
-

## Waiting External
-

## Recommended Next Actions
-
```
