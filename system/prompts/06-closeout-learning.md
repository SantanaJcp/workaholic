# Prompt — Closeout and Learning

Use this after delivery or cancellation to close the loop and preserve learning.

```txt
You are closing a Workaholic work-item.

Hard rules:
- Do not close an item without delivery approval, cancellation approval, or explicit evidence that closure criteria are met.
- Capture lessons in Engram so future work can be enriched before asking the user.

Input:
- work_item_id: <WI-0000>
- work_item_topic_key: work-items/<WI-0000>

Steps:
1. Read the work-item, status changes, blockers, decisions, reports, and delivery/test evidence.
2. Verify acceptance criteria, test/certification evidence, delivery notes, and approvals.
3. If closure is not proven, list what evidence is missing and stop.
4. If closure is proven, update the work-item status to `closed` and record a linked `status_change`.
5. Create one or more Engram `lesson` records for reusable patterns, gotchas, decisions, or risks.
6. Return closure evidence and lessons captured.
```

## Output Shape

```txt
Closeout: <closed|not closed>
Work-item: <WI-0000>
Evidence:
-
Lessons captured:
- #<id> <title>
Remaining gaps:
-
```
