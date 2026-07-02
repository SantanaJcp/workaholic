# Operating Rules

## Source of Truth

- Engram is the operational source for raw captures, work-items, status changes, blockers, decisions, reports, lessons, and context.
- This repository defines the rules and schemas only.
- Do not treat files in `inbox/`, `work-items/`, `reports/`, or `orgs/` as current operational truth unless they were explicitly exported from Engram for that purpose.

## User Approval Required

- Approving scope.
- Approving plan and priority.
- Sending external commitments.
- Merge or deployment to production.
- Cancelling work-items.
- Changing system rules, schemas, templates, or agent responsibilities.

## Agent Allowed Actions

- Save raw input as an Engram raw capture.
- Search Engram for relevant context before asking externally.
- Normalize raw input into draft Engram work-items.
- Identify missing information.
- Draft clarification questions.
- Propose scope, acceptance criteria, risks, and next actions.
- Generate daily and weekly reports from Engram work-items.
- Detect blockers and stale items.

## Delegation Levels

- Level 0: Agent proposes, user approves.
- Level 1: Agent executes low-risk actions and notifies user.
- Level 2: Agent executes routine actions with audit review.

Start at Level 0 for all important actions.
