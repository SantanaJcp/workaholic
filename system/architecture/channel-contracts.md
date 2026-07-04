# Channel Contracts

Workaholic listens to intake contracts, not channels. Every source must be explicitly authorized before it can feed the intake pipeline.

## Contract Schema

```yaml
channel: ""
ingestion_mode: forward | pull | webhook | api
allowed_sources: []
allowed_event_types: []
default_action: capture_only | capture_and_classify | capture_and_diagnose
auto_work_item_creation: true | false
auto_diagnosis: true | false
auto_external_reply: false
requires_user_approval_for: [code_changes, external_replies, commitments, deployments]
status: draft | active | paused
```

## Manual / Forward-to-Intake

```yaml
channel: manual_forward
ingestion_mode: forward
allowed_sources: [user, approved_forwarder]
allowed_event_types: [message, alert, transcript, forward]
default_action: capture_and_classify
auto_work_item_creation: false
auto_diagnosis: false
auto_external_reply: false
requires_user_approval_for: [code_changes, external_replies, commitments, deployments]
status: active
```

- Phase 1 uses this contract only; the user or an approved forwarder pastes `CHANNEL_EVENT:` envelopes.
- Risk: forwarded content may omit provenance, so the router must preserve sender and source notes exactly as provided.

## Email

```yaml
channel: email
ingestion_mode: pull
allowed_sources: [dedicated_label:Workaholic Intake]
allowed_event_types: [message, forward]
default_action: capture_and_classify
auto_work_item_creation: false
auto_diagnosis: false
auto_external_reply: false
requires_user_approval_for: [code_changes, external_replies, commitments, deployments]
status: draft
```

- Pull only from a dedicated `Workaholic Intake` label to avoid broad mailbox surveillance.
- Risk: email threads can include sensitive personal data and signatures; redaction must happen before LLM triage.

## Dashboard Webhooks

```yaml
channel: dashboard
ingestion_mode: webhook
allowed_sources: [sentry, github_actions, uptime_monitors]
allowed_event_types: [alert, webhook]
default_action: capture_and_diagnose
auto_work_item_creation: true
auto_diagnosis: true
auto_external_reply: false
requires_user_approval_for: [code_changes, external_replies, commitments, deployments]
status: draft
```

- Alerts are structured and can often proceed to read-only diagnosis after correlation.
- Risk: noisy monitors can flood Engram; dedupe keys and rate limits are required before activation.

## WhatsApp

```yaml
channel: whatsapp
ingestion_mode: api
allowed_sources: [allowlisted_contacts, allowlisted_groups]
allowed_event_types: [message, forward]
default_action: capture_and_classify
auto_work_item_creation: false
auto_diagnosis: false
auto_external_reply: false
requires_user_approval_for: [code_changes, external_replies, commitments, deployments]
status: draft
```

- Use WhatsApp Business API, Twilio, or Kapso only; do not use personal-WhatsApp QR bridge scraping.
- Risk: informal messages often lack acceptance criteria, so missing information should be surfaced early.

## Teams

```yaml
channel: teams
ingestion_mode: api
allowed_sources: [approved_channels, approved_mentions, approved_hashtags]
allowed_event_types: [message, alert]
default_action: capture_and_classify
auto_work_item_creation: false
auto_diagnosis: false
auto_external_reply: false
requires_user_approval_for: [code_changes, external_replies, commitments, deployments]
status: draft
```

- Microsoft Graph message reads require tenant-admin/protected-API consent.
- Risk: broad Teams reads can over-collect internal conversations; activation must specify channels plus mention or hashtag conventions.

## Call Transcripts

```yaml
channel: call_transcript
ingestion_mode: forward
allowed_sources: [consented_transcripts]
allowed_event_types: [transcript, forward]
default_action: capture_and_classify
auto_work_item_creation: false
auto_diagnosis: false
auto_external_reply: false
requires_user_approval_for: [code_changes, external_replies, commitments, deployments]
status: draft
```

- Only consented transcripts may be forwarded into Workaholic.
- Risk: transcripts can contain private or third-party information; mark sensitive when confidentiality is unclear.

## Activation Rule

Activating any contract beyond Manual/Forward requires an approved work-item and a user decision recorded in Engram.
