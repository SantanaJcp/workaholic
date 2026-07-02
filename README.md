# Workaholic

Personal Delivery Operating System for managing multi-project work with AI-assisted intake, planning, execution tracking, reporting, and delivery orchestration.

## Current MVP

The first version validates one core loop:

```txt
raw input -> Engram raw_capture -> Engram-enriched work_item -> daily decision report
```

No external integrations are required yet. Inputs can be pasted manually into Codex, then captured and normalized in Engram.

## Operating Model

Workaholic is Engram-first:

- Engram stores operational state: raw captures, work-items, status changes, blockers, decisions, reports, lessons, and project context.
- This Git repository stores the system contract: rules, states, schemas, prompts, scripts/adapters, exports/backups, and documentation.
- Agents must enrich new work-items from Engram memory before asking the user or checking external sources.

## Manual Workflow

Use the MVP loop before adding integrations or dashboards:

```txt
capture raw input -> create Engram raw_capture -> search Engram context -> create/update Engram work_item -> report decisions
```

The user remains the director. Agents may capture, normalize, enrich, plan, report, and prepare bounded handoffs, but user approval is required for scope, priority, commitments, cancellation, and delivery decisions.

## Reusable Prompts

The prompt pack lives in `system/prompts/`:

- `01-intake-raw-capture.md` — preserve new work as an Engram raw capture.
- `02-normalize-work-item.md` — enrich a raw capture and create/update a work-item.
- `03-chief-of-staff-heartbeat.md` — review active work and surface decisions, blockers, risks, and progress.
- `04-daily-report.md` — generate a decision-focused daily report from Engram records.
- `05-worker-handoff.md` — prepare bounded execution for a worker thread.
- `06-closeout-learning.md` — close work and capture lessons.

## Repository Structure

```txt
AGENTS.md   Agent operating contract.
system/     Rules, state machine, Engram object model, reusable prompts, templates, and agent behavior.
inbox/      Optional exports/examples of raw captures; not the primary store.
work-items/ Optional exports/examples of work-items; not the primary store.
reports/    Optional exports/examples of reports; not the primary store.
orgs/       Optional exports/examples of org/project context; not the primary store.
```
