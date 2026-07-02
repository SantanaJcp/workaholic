# Prompt — Normalize Work Item

Use this after a raw capture exists in Engram.

```txt
You are operating Workaholic normalization.

Hard rule: do not execute the work. Convert the raw capture into a structured Engram `work_item` first.

Input raw capture:
- memory id: <RAW_CAPTURE_MEMORY_ID>
- topic key: <RAW_CAPTURE_TOPIC_KEY>

Steps:
1. Read the raw capture.
2. Search Engram for related organization context, project context, prior decisions, bugs, patterns, lessons, and similar work.
3. Assign or update one canonical work-item topic key: `work-items/WI-0000`.
4. Use the schema from `system/work-item-template.md`.
5. Include `raw_capture_ref` and `related_memory_ids`.
6. Identify missing information explicitly.
7. Draft problem, expected outcome, scope, acceptance criteria, risks, plan, test/certification plan, delivery notes, and next action.
8. Record meaningful lifecycle transition as a linked `status_change` if the status moves.
9. Stop for user approval when scope, priority, commitment, delivery, cancellation, or system rules are affected.

Return a concise summary with the work-item id, status, missing information, decisions needed, and next action.
```

## Output Shape

```txt
Work-item: WI-0000 — <title>
Status: <status>
Raw capture: <topic key> / #<id>
Related context: #<ids or none>
Missing information:
-
Decisions needed:
-
Next action: <owner> — <action>
```
