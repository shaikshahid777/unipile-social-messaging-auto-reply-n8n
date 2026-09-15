# Unipile Social Messaging Auto-Reply — n8n

Production-style webhook automation for receiving LinkedIn messages through Unipile, validating and deduplicating events, logging messages to Google Sheets, and automatically sending a confirmation reply.

## Overview

This project demonstrates an end-to-end social messaging integration built with **n8n Cloud + Unipile + LinkedIn + Google Sheets**.

When an external LinkedIn user sends a message to the connected account:

`LinkedIn → Unipile → n8n Webhook → Validate → Duplicate Check → Google Sheets → Unipile Reply → Status Update`

The workflow is designed to be deterministic, auditable, idempotent, and suitable for a production-style assessment demonstration.

## Key Features

- Unipile API authentication using n8n encrypted credentials
- LinkedIn account connected through Unipile Hosted Connection
- Production n8n webhook for incoming messaging events
- Message payload extraction and required-field validation
- Duplicate detection using `message_id`
- Temporary message persistence in Google Sheets
- Automated confirmation reply through the Unipile Unified Messaging API
- SUCCESS / FAILED / DUPLICATE / INVALID_PAYLOAD handling
- Secure secret handling with no API keys committed to source control
- Documentation, test plan, troubleshooting guide, and assessment mapping

## Workflow

1. **Webhook** — receives the incoming Unipile messaging event.
2. **Extract Message Data** — normalizes event, message, chat, sender, provider, account, text, and timestamp.
3. **Check Required Fields** — validates the minimum required event fields.
4. **Duplicate Check Lookup** — searches Google Sheets by `message_id`.
5. **IF Already Processed** — prevents duplicate replies.
6. **Append Row** — records a new incoming message.
7. **Unipile Send Message** — sends the required confirmation to the captured chat.
8. **Update Reply Status** — records the final result.
9. **Respond to Webhook** — returns the processing outcome.

## Automated Reply

> Thank you for your message. We have received your inquiry and will respond shortly.

## Data Model

The temporary **Messages** sheet tracks:

`message_id`, `chat_id`, `sender_name`, `sender_id`, `provider`, `message_text`, `timestamp`, `event_name`, `reply_status`, `reply_message_id`, `processed_at`.

## Validation

The published workflow was validated with a real LinkedIn message. The demonstration covers webhook receipt, downstream n8n execution, message logging, and automatic reply delivery.

### Video Demonstration

[Loom — End-to-End Demonstration](https://www.loom.com/share/3fd44a3badf84f07a6908205d3554a22)

## Repository Structure

```
.
├── workflow/
│   └── n8n workflow export
├── docs/
│   ├── architecture.md
│   ├── testing.md
│   ├── troubleshooting.md
│   └── assessment-mapping.md
├── database/
│   └── google-sheets-schema.md
├── examples/
│   └── sample-webhook-payload.json
├── demo/
│   └── loom-link.md
└── security/
    └── SECURITY.md
```

## Security

Never commit Unipile API keys, access tokens, OAuth credentials, webhook secrets, cookies, or private personal data. Production secrets should remain in n8n's encrypted credential store.

## Assessment Coverage

This repository covers Unipile workspace access, API authentication, LinkedIn connectivity, account readiness, webhook registration, incoming message capture, payload validation, temporary database logging, automated replies, end-to-end workflow testing, and troubleshooting.

## Author

**Shaik Mohammad Shaheed**

AI & Automation | n8n | API Integration | Webhooks | AI Agents | Generative AI

## License

This project is provided for educational and assessment purposes.
