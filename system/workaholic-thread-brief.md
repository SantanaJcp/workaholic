# Workaholic — Thread Brief

## Purpose

Workaholic is a personal, AI-agent-assisted Delivery Operating System for managing multiple projects across different organizations, sources, ownership models, and delivery cadences.

The goal is not a manual productivity system. The goal is an agentic operating system where the user directs: sets priorities, makes important decisions, approves commitments, and resolves blockers, while AI agents capture, normalize, enrich, plan, monitor, execute bounded tasks, report, and learn.

## Original Problem

The user manages several projects in parallel. Requirements arrive through different sources and with different quality levels:

- Some arrive as raw conversations or meetings with lots of detail but little structure.
- Some arrive through structured boards but with poor detail.
- Some arrive as short informal messages with almost no structure.

Ownership also varies:

- In some projects, the user owns the full cycle from requirement discovery through delivery/deployment.
- In other projects, the user owns only part of the cycle because requirements arrive already structured or are managed by another team.

Cadence varies too:

- Some work updates weekly.
- Some work updates biweekly.
- Most projects still require daily awareness, progress updates, and follow-up.

The current pain is that too much depends on memory, manual follow-up, reactive tracking, and scattered sources.

## Desired Outcome

Create a system that progressively removes the user from operational tracking and moves the user into a direction/supervision role.

The system should support the full cycle:

```txt
capture -> intake -> normalization -> enrichment -> clarification -> scope -> spec -> plan -> prioritization -> execution -> testing -> certification -> MR/delivery/deploy -> reporting -> closure -> learning
```

## Key Architectural Decision

We initially considered storing inbox/work-items/tasks as Markdown/YAML files in Git.

After discussion, the preferred direction changed:

```txt
Engram = operational memory + semantic context
Git repo = system definition, schemas, prompts, scripts, exports, and documentation
```

This matters because Engram already holds project memory, decisions, discoveries, lessons, prompts, context, and semantic search. Using Engram for operational state lets new work-items be enriched from prior memory before asking for external information.

## Engram-First Model

Engram should hold operational objects such as:

- raw captures
- normalized work-items
- status changes
- blockers
- decisions
- ownership/context
- lessons learned
- closure notes

The Git repository should hold:

- `AGENTS.md`
- rules
- state machine
- object schemas
- prompts/skills instructions
- scripts/adapters
- exports/backups
- documentation

## Why Engram Helps

A new task should be enriched in this order:

```txt
1. Save raw input to Engram.
2. Search Engram for related project context, prior decisions, bugs, patterns, lessons, and similar work.
3. Create or update a structured work-item in Engram.
4. Identify missing information.
5. Ask external sources or the user only when Engram cannot answer safely.
```

This makes Engram the system nervous system, not just a passive note store.

## Important Caveat

Engram can store structured content with `type`, `title`, `project`, `scope`, `topic_key`, and Markdown/YAML content. But status, priority, organization, due date, and similar fields are not first-class indexed fields unless we encode them into content/title/topic/type or build an adapter.

So the design needs strict conventions.

## Proposed Engram Object Types

Use stable types/conventions such as:

```txt
raw_capture
work_item
status_change
blocker
decision
lesson
report
org_context
project_context
```

## Proposed Topic Key Conventions

Examples:

```txt
raw-captures/YYYY-MM-DD/<slug>
work-items/WI-0001
status-changes/WI-0001/YYYY-MM-DD-HHMM
blockers/WI-0001/<slug>
decisions/WI-0001/<slug>
lessons/<project>/<slug>
orgs/<org-slug>
projects/<project-slug>
reports/daily/YYYY-MM-DD
reports/weekly/YYYY-WW
```

## Proposed Work Item Content Shape

A work-item stored in Engram should have structured Markdown/YAML content similar to:

```yaml
id: WI-0001
title: ""
organization: ""
project: ""
type: feature | bug | support | research | coordination
source: teams | board | chat | meeting | email | note | other
source_ref: ""
ownership: full | partial
status: captured | normalized | clarifying | defined | planned | approved | in_progress | in_test | in_certification | ready_for_delivery | delivered | closed | blocked | paused | cancelled | waiting_external
priority: low | medium | high | urgent | null
captured_at: YYYY-MM-DD
due_date: null
definition_confidence: low | medium | high
blocked_by: []
approvals:
  scope: pending | approved | rejected
  plan: pending | approved | rejected
  delivery: pending | approved | rejected
next_action:
  owner: ""
  action: ""
  due: null
```

Then body sections:

```txt
## Raw Request
## Retrieved Context From Engram
## Problem
## Expected Outcome
## Missing Information
## Scope
## Acceptance Criteria
## Risks / Assumptions
## Plan
## Test / Certification Plan
## Delivery / MR / Deploy Notes
## Log
```

## State Machine

The main lifecycle is:

```txt
captured -> normalized -> clarifying -> defined -> planned -> approved -> in_progress -> in_test -> in_certification -> ready_for_delivery -> delivered -> closed
```

Transversal states:

```txt
blocked
paused
cancelled
waiting_external
```

## Chief of Staff Pattern

The user shared an external pattern describing a Codex “Chief of Staff thread”. It is useful, but only as part of the larger system.

Interpretation:

```txt
Chief of Staff Thread = orchestration subsystem
```

It should not own everything. It should coordinate after intake/normalization exists.

Responsibilities:

- review active work-items from Engram;
- check progress;
- detect blockers/stale work;
- coordinate worker threads;
- use goals to keep objective and completion criteria visible;
- use heartbeats/thread automations for recurring follow-up;
- ensure tests/certification/delivery status are tracked;
- generate decision-focused daily/weekly reports.

Hard rule:

```txt
Never start execution directly from raw requirements. First normalize into a work-item.
```

## Goals and Heartbeats

Goals should be measurable, not vague.

Example Chief of Staff goal:

```txt
Maintain all active Workaholic work-items with current status, next action, blockers, and delivery/test/reporting status. Surface only decisions, risks, blockers, and meaningful progress to the user.
```

Heartbeat usage should depend on mode:

```txt
normal mode: every 60-90 minutes
release/deploy mode: every 10-15 minutes
blocked mode: every 30 minutes until resolved
daily brief: morning
EOD report: end of day
weekly report: weekly per relevant cadence
```

Worker threads should check in immediately when important events happen:

```txt
PR opened
tests passed/failed
review feedback received
feedback addressed
deploy started
deploy verified
blocked
```

## Human Approval Rules

Start conservative.

User approval required for:

- scope approval;
- plan/priority approval;
- external commitments;
- merge/deploy to production;
- cancellation;
- changes to system rules/schemas;
- high-impact assumptions.

Delegation can later mature:

```txt
Level 0: agent proposes, user approves.
Level 1: agent executes low-risk routine actions and notifies.
Level 2: agent executes routine actions with audit review.
```

## MVP Direction

The first MVP should validate one loop:

```txt
raw input -> Engram raw_capture -> Engram-enriched work_item -> daily decision report
```

Do not build connectors, dashboards, complex automations, or many agents yet.

## Current Repository State

The repository currently exists at:

```txt
/Users/santana/Development/workaholic
```

It was initialized with a Markdown/Git-first skeleton. That should now be revised toward Engram-first.

Current files include:

```txt
AGENTS.md
README.md
system/rules.md
system/states.md
system/work-item-template.md
system/chief-of-staff.md
system/daily-report-template.md
system/thread-bootstrap.md
```

## Immediate Next Steps

1. Update repository documentation to reflect the Engram-first architecture.
2. Create `system/engram-model.md` defining:
   - object types;
   - topic key conventions;
   - content schemas;
   - update rules;
   - search/enrichment workflow.
3. Update `AGENTS.md` so Codex treats Engram as the operational source for work-items/status, and Git as the system definition.
4. Update or replace `system/work-item-template.md` with an Engram work-item schema.
5. Update `system/chief-of-staff.md` so it reads from Engram memory first, then asks/searches externally only when necessary.
6. Create one manual sample raw capture in Engram and transform it into one sample work-item.
7. Generate the first daily decision report from that sample.

## First Task For This Thread

Start by reviewing the repository files and this brief. Then propose and apply the smallest documentation changes needed to make Workaholic explicitly Engram-first.

Do not implement external integrations yet. Do not create dashboards. Do not overbuild. First make the system contract clear.
