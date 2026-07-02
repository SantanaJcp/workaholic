# Workaholic

Personal Delivery Operating System for managing multi-project work with AI-assisted intake, planning, execution tracking, reporting, and delivery orchestration.

## Current MVP

The first version validates one core loop:

```txt
raw input -> normalized work-item -> daily decision report
```

No external integrations are required yet. Inputs can be pasted manually into `inbox/` until the workflow proves useful.

## Structure

```txt
inbox/       Raw captured inputs before normalization.
work-items/  Normalized work-items, one file per item.
reports/     Daily and weekly reports.
orgs/        Organization/project profiles and operating context.
system/      Rules, state machine, templates, and agent behavior.
```
