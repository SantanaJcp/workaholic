# Engram Work-Item Template

Store this content in Engram under topic key `work-items/WI-0000`. Do not create a repository work-item file unless exporting or testing the workflow.

```yaml
object_type: work_item
id: WI-0000
title: ""
organization: ""
project: ""
type: feature | bug | support | research | coordination
source: teams | board | chat | meeting | email | note | other
source_ref: ""
raw_capture_ref: raw-captures/YYYY-MM-DD/<slug>
ownership: full | partial
status: captured | normalized | clarifying | defined | planned | approved | in_progress | in_test | in_certification | ready_for_delivery | delivered | closed | blocked | paused | cancelled | waiting_external
priority: low | medium | high | urgent | null
captured_at: YYYY-MM-DD
due_date: null
definition_confidence: low | medium | high
related_memory_ids: []
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

# WI-0000 — Title

## Raw Request

Paste the original input here without rewriting it, or reference the linked `raw_capture` topic key.

## Retrieved Context From Engram

-

## Problem

What problem needs to be solved?

## Expected Outcome

What should be true when this is done?

## Missing Information

- [ ]

## Scope

### In Scope

-

### Out of Scope

-

## Acceptance Criteria

- [ ]

## Risks / Assumptions

-

## Plan

- [ ]

## Test / Certification Plan

- [ ]

## Delivery / MR / Deploy Notes

-

## Log

- YYYY-MM-DD HH:mm — Created from raw capture `<topic_key>`.
