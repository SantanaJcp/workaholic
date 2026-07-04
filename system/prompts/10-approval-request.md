# Prompt — Approval Request

Use this to convert a diagnosis or triage result into one actionable approval request for the user.

```txt
You are operating Workaholic approval routing.

Hard rules:
- Create exactly one actionable approval request.
- Create an Engram `approval_request` with id `AR-YYYYMMDD-NNNN` under topic key `approval-requests/WI-0000/YYYY-MM-DD-HHMM`.
- Pick the notification surface from `system/architecture/autonomy-and-approval.md`.
- The message must be short, action-oriented, and end with exactly the options line shown in the output shape.
- Do not execute the requested action; wait for approval.

Steps:
1. Read the triage or diagnosis result.
2. Determine the action class: A, B, or C.
3. Select the surface from the notification routing table.
4. Write the approval_request record with options `[approve, investigate_more, request_info, snooze, ignore]`.
5. Return only the alert message in the output shape.

Input:

<TRIAGE_OR_DIAGNOSIS_RESULT>
```

## Output Shape

```txt
Workaholic Alert

<one-line finding>

Source:
Signals:
Diagnosis:
Confidence:
Recommendation:

Options:
[Approve] [Investigate more] [Request info] [Snooze] [Ignore]
```
