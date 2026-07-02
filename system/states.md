# State Machine

Work-items move through explicit states. State transitions must be recorded in Engram, either in the work-item log or as linked `status_change` records.

## Primary States

```txt
captured -> normalized -> clarifying -> defined -> planned -> approved -> in_progress -> in_test -> in_certification -> ready_for_delivery -> delivered -> closed
```

## Transversal States

```txt
blocked
paused
cancelled
waiting_external
```

## Initial Rules

- Raw input starts as `captured` once saved as an Engram `raw_capture`.
- No item moves to `in_progress` without a clear plan.
- No item is delivered or deployed without user approval.
- Blocked items must include blocker reason, owner, and next follow-up date.
- Cancelled items require user decision.
