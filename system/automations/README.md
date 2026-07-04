# Automation Drafts

This folder stores reusable automation drafts as system-definition artifacts.

Engram remains the operational source of truth. These Markdown files define repeatable automation structures that can later be activated manually in Codex or adapted by an automation adapter.

## Rules

- Store each automation draft as Markdown before activating it.
- Keep automation prompts small, explicit, and auditable.
- Prefer read-only automations until the manual loop proves value.
- Do not include secrets, private tokens, or credentials.
- Do not make an automation responsible for raw execution from unnormalized input.
- Link each automation to the relevant prompt, work-item pattern, or report template when possible.

## Naming

Use kebab-case names:

```txt
<cadence-or-purpose>-<short-name>.md
```

Examples:

```txt
daily-command-brief.md
weekly-project-review.md
blocked-work-follow-up.md
```

## Current Drafts

- `daily-command-brief.md` — read-only weekday Chief of Staff brief for active Workaholic Engram records.
- `eod-closeout.md` — read-only weekday end-of-day operational closeout.
- `semi-automatic-intake.md` — on-demand `INTAKE:` normalization prompt.
- `notification-policy.md` — draft-only notification policy and message shape.
- `personal-alert-heartbeat.md` — short user-only action alerts for review, MR, deploy, blockers, decisions, and closure.
- `always-on-intake.md` — on-demand `CHANNEL_EVENT:` simulated always-on intake pipeline (layer 5).
- `automation-template.md` — base structure for future automation drafts.
