# Autonomy Levels and Approval Policy

## Autonomy Levels

| Level | Name | Policy |
| --- | --- | --- |
| L0 | Suggest Only | Current default: capture, classify, propose; modifies nothing. |
| L1 | Intake Autonomy | Create raw_captures, channel_events, draft/merge work-items, dedupe, prepare alerts — **target level once Phase 1 is validated**. |
| L2 | Diagnosis Autonomy | Read-only: logs, repos, dashboards, sandbox reproduction, diagnosis_report. |
| L3 | Execution With Approval | Bounded worker: branch, code, tests, PR/MR draft — never deploy. |
| L4 | Low-Risk Auto Execution | Typo/docs/test-only/known playbooks — future, off by default. |

## Action Classes

- Class A (autonomous at current level): capture, classify, dedupe, correlate, Engram search, work-item draft, read-only diagnosis prep, alert drafting.
- Class B (batch approval in Daily Command Brief): canonical work-item creation below confidence 0.7, duplicate merges, priority proposals, snoozes.
- Class C (explicit interrupt approval): code changes, worker execution, external replies, commitments, priority overrides, cancellation, delivery/deploy, rules/schema changes, new channel contracts.

## Notification Surface Routing

| Signal | Surface |
| --- | --- |
| noise/FYI | EOD Closeout only |
| low severity / non-urgent Class B | Daily Command Brief |
| diagnosed P2, decision needed, fix candidate ready | Personal Alert Heartbeat |
| P1/incident, urgent Class C | immediate interrupt alert |

Surfaces map to the existing automations `daily-command-brief.md`, `eod-closeout.md`, `personal-alert-heartbeat.md`.

## Current Setting

`autonomy_level: L0`

Raising it requires a user decision recorded as an Engram `decision` record.
