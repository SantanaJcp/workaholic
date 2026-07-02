# AGENTS.md

## Purpose

This repository is a personal Delivery Operating System. Codex should help convert raw work inputs into normalized work-items, track progress through explicit states, surface decisions, and generate concise operating reports.

## Core Rule

Never execute work directly from raw input. First normalize the input into a work-item with scope, missing information, acceptance criteria, risks, and a next action.

## Operating Principles

- The user directs; agents assist, propose, execute bounded tasks, and report.
- The source of truth is text in this repository.
- If something is not written in the work-item, it does not exist for downstream workflow.
- Important state transitions must be recorded in the work-item log.
- Prefer small, auditable changes over large automated jumps.
- Ask for approval before commitments, delivery, production deployment, or changes to system rules.

## MVP Focus

Validate this loop first:

```txt
raw input -> normalized work-item -> daily decision report
```

Do not add external connectors, dashboards, databases, or broad automation until the manual loop works with real tasks.
