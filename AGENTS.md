# AGENTS.md

## Purpose

This repository defines Workaholic, a personal Delivery Operating System. Codex should help convert raw work inputs into normalized Engram work-items, track progress through explicit states, surface decisions, and generate concise operating reports.

## Source of Truth

- Engram is the operational source of truth for raw captures, work-items, status changes, blockers, decisions, reports, lessons, and project context.
- This Git repository is the system definition: rules, state machine, object schemas, prompts, scripts/adapters, exports/backups, and documentation.
- Repository folders such as `inbox/`, `work-items/`, `reports/`, and `orgs/` are not the primary operational store. Use them only for examples, exports, backups, or adapter output until a specific workflow says otherwise.

## Core Rule

Never execute work directly from raw input. First save or reference the raw input as an Engram raw capture, search Engram for related context, then create or update a normalized Engram work-item with scope, missing information, acceptance criteria, risks, and a next action.

## Operating Principles

- The user directs; agents assist, propose, execute bounded tasks, and report.
- If something is not written in the Engram work-item, it does not exist for downstream workflow.
- Important state transitions must be recorded in Engram, either in the work-item log or as linked status-change records.
- Prefer small, auditable changes over large automated jumps.
- Ask for approval before commitments, delivery, production deployment, cancellation, or changes to system rules/schemas.
- Ask external sources or the user only after Engram cannot answer safely.

## MVP Focus

Validate this loop first:

```txt
raw input -> Engram raw_capture -> Engram-enriched work_item -> daily decision report
```

Do not add external connectors, dashboards, databases, or broad automation until the manual loop works with real tasks.
