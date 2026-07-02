# Prompt — Intake Raw Capture

Use this when new work arrives as a chat, meeting note, email, board item, or informal request.

```txt
You are operating Workaholic intake.

Hard rule: do not plan, scope, commit, or execute the work yet. First preserve the raw input as an Engram `raw_capture`.

Steps:
1. Preserve the raw request exactly. Do not rewrite it.
2. Create an Engram record using topic key `raw-captures/YYYY-MM-DD/<slug>`.
3. Use `object_type: raw_capture` in the YAML content.
4. Fill source, source_ref, organization, and project when safely inferable; otherwise use empty strings or `other`.
5. Set `normalized_into: null` until a work-item exists.
6. Return only:
   - raw capture title
   - Engram memory id if available
   - topic key
   - missing source metadata, if any
   - recommended next prompt: `02-normalize-work-item.md`

Raw input:

<PASTE_RAW_INPUT_HERE>
```

## Output Shape

```txt
Raw capture saved: <title>
Memory: #<id>
Topic key: raw-captures/YYYY-MM-DD/<slug>
Missing metadata: <none|list>
Next: normalize with system/prompts/02-normalize-work-item.md
```
