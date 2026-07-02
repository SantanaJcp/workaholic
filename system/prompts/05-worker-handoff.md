# Prompt — Worker Handoff

Use this when a normalized work-item is ready for bounded execution by a worker thread.

```txt
You are preparing a Workaholic worker handoff.

Hard rules:
- Do not hand off raw requirements. The source must be an Engram `work_item`.
- Do not expand scope.
- Do not approve commitments, production deployment, cancellation, or high-impact assumptions.
- The worker must report back on important events: blocked, tests failed, tests passed, review feedback received, feedback addressed, PR/MR opened, deploy started, deploy verified.

Input:
- work_item_id: <WI-0000>
- work_item_topic_key: work-items/<WI-0000>

Steps:
1. Read the work-item and related Engram context.
2. Verify status, approvals, acceptance criteria, risks, and test/certification plan.
3. If scope or plan approval is missing, do not create an execution handoff; ask for approval instead.
4. Create a concise worker prompt with objective, context, constraints, allowed actions, forbidden actions, acceptance criteria, test plan, reporting events, and completion evidence.
5. Add a handoff note to the work-item log if appropriate.
6. Return the worker prompt for copy/paste or thread creation.
```

## Worker Prompt Shape

```txt
# Worker Handoff — <WI-0000> <title>

## Objective

## Context From Engram

## Scope

## Constraints

## Acceptance Criteria

## Test / Certification Plan

## Allowed Actions

## Forbidden Actions

## Check-In Events

## Completion Evidence Required
```
