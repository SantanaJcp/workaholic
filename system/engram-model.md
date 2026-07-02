# Engram Model

## Contract

Engram is the operational memory for Workaholic. The Git repository defines the model; it does not own day-to-day operational state.

Engram records must carry Workaholic's operational fields inside their content. Do not assume fields such as status, priority, organization, project, ownership, or due date are first-class indexed fields. Encode them in the record body using the schemas below, and use topic keys for stable lookup.

## Operational Objects

Use stable `object_type` values inside each Engram record's content:

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

If the Engram tool's `type` field is constrained, use the closest broad category there and keep the exact value in `object_type`.

## Record Conventions

- `topic_key` identifies the canonical object location.
- `object_type` identifies the Workaholic object type inside the record content.
- `title` should include the object id or slug plus a concise human label.
- Operational fields belong in the YAML block at the top of the content.
- Updates should preserve one canonical record per work-item and append important history to `## Log`.
- Linked records should reference the canonical `work_item` id and topic key.

## Topic Key Conventions

```txt
raw-captures/YYYY-MM-DD/<slug>
work-items/WI-0001
status-changes/WI-0001/YYYY-MM-DD-HHMM
blockers/WI-0001/<slug>
decisions/WI-0001/<slug>
lessons/<project-slug>/<slug>
orgs/<org-slug>
projects/<project-slug>
reports/daily/YYYY-MM-DD
reports/weekly/YYYY-WW
```

## Required Work-Item Content

Work-items must use the schema in `system/work-item-template.md` and include these sections:

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

## Minimal Content Schemas

### Raw Capture

```yaml
object_type: raw_capture
id: RC-YYYYMMDD-0001
captured_at: YYYY-MM-DD HH:mm
source: teams | board | chat | meeting | email | note | other
source_ref: ""
organization: ""
project: ""
captured_by: agent | user
normalized_into: null
```

```txt
## Raw Input

Paste the original request without rewriting it.

## Capture Notes

-
```

### Status Change

```yaml
object_type: status_change
work_item_id: WI-0000
work_item_topic_key: work-items/WI-0000
from_status: captured
to_status: normalized
changed_at: YYYY-MM-DD HH:mm
changed_by: agent | user
reason: ""
```

### Blocker

```yaml
object_type: blocker
work_item_id: WI-0000
status: open | resolved
owner: ""
opened_at: YYYY-MM-DD HH:mm
follow_up_at: null
resolved_at: null
```

### Decision

```yaml
object_type: decision
work_item_id: WI-0000
decided_at: YYYY-MM-DD HH:mm
decider: user | agent
decision: ""
```

### Report

```yaml
object_type: report
report_type: daily | weekly
date: YYYY-MM-DD
source: engram
```

### Lesson

```yaml
object_type: lesson
project: ""
learned_at: YYYY-MM-DD
applies_to: []
```

### Organization Context

```yaml
object_type: org_context
organization: ""
owner_model: ""
cadence: weekly | biweekly | daily | ad_hoc
```

### Project Context

```yaml
object_type: project_context
organization: ""
project: ""
ownership: full | partial
cadence: weekly | biweekly | daily | ad_hoc
```

## Update Rules

1. Save raw input as `raw_capture` before planning or execution.
2. Search Engram for related project context, prior decisions, lessons, bugs, and similar work.
3. Create or update one canonical `work_item` under `work-items/<id>`.
4. Record meaningful status changes in the work-item log; create a linked `status_change` record when the transition needs its own audit trail.
5. Keep approvals explicit in the work-item content.
6. Generate reports from Engram records, not from memory or scattered chat context.
7. Ask the user only when Engram and written sources cannot safely resolve missing information.

## Search and Enrichment Workflow

```txt
1. Capture raw input in Engram.
2. Search Engram by organization, project, keywords, source reference, and similar work.
3. Add relevant findings to "Retrieved Context From Engram" with source memory IDs when available.
4. Identify missing information and risks.
5. Draft or update the work-item.
6. Stop for approval when scope, priority, commitment, delivery, cancellation, or system rules are affected.
```
