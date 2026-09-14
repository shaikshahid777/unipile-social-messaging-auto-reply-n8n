# Architecture

## High-level flow

LinkedIn sender → Unipile → n8n Production Webhook → Extract Message Data → Required-field validation → Google Sheets duplicate lookup → duplicate branch or message logging → Unipile Send Message → status update → webhook response.

## Components

- LinkedIn: external messaging provider used for the assessment demonstration.
- Unipile: unified messaging layer and webhook provider.
- n8n: orchestration and business logic.
- Google Sheets: temporary message store and idempotency lookup.

## Data flow

The webhook event is normalized into nine core fields: event name, message ID, chat ID, sender name, sender ID, provider, account ID, message text, and timestamp. A message ID lookup prevents duplicate processing. New messages are logged before the outbound send, then the row is updated with SUCCESS or FAILED.
