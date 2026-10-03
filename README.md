<!-- SHOWCASE_START --><div align="center">[![Typing](https://readme-typing-svg.demolab.com?font=Fira+Code&weight=700&size=22&duration=2800&pause=900&color=58A6FF&center=true&vCenter=true&width=900&lines=unipile%20social%20messaging%20auto%20reply%20n8n;AI%20%7C%20Automation%20%7C%20Engineering;Explore%20the%20project%20%F0%9F%9A%80)](https://github.com/shaikshahid777/unipile-social-messaging-auto-reply-n8n)<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0D1117,50:161B22,100:58A6FF&height=110&section=header&text=unipile-social-messaging-auto-reply-n8n&fontSize=26&fontColor=FFFFFF&animation=twinkling&fontAlignY=65" width="100%" alt="Animated project banner"/>

[![Repository](https://img.shields.io/badge/Repository-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/shaikshahid777/unipile-social-messaging-auto-reply-n8n) [![Issues](https://img.shields.io/badge/Report-Issue-red?style=for-the-badge&logo=github)](https://github.com/shaikshahid777/unipile-social-messaging-auto-reply-n8n/issues/new) [![Stars](https://img.shields.io/github/stars/shaikshahid777/unipile-social-messaging-auto-reply-n8n?style=for-the-badge&logo=github)](https://github.com/shaikshahid777/unipile-social-messaging-auto-reply-n8n/stargazers) [![Fork](https://img.shields.io/github/forks/shaikshahid777/unipile-social-messaging-auto-reply-n8n?style=for-the-badge&logo=github)](https://github.com/shaikshahid777/unipile-social-messaging-auto-reply-n8n/fork) [![Profile](https://img.shields.io/badge/Profile-Visit-0A66C2?style=for-the-badge&logo=github)](https://github.com/shaikshahid777)</div>

> ✨ **Project Showcase Mode:** animated banner • interactive navigation • live repository actions

[🚀 Repository](https://github.com/shaikshahid777/unipile-social-messaging-auto-reply-n8n) · [🐞 Report Issue](https://github.com/shaikshahid777/unipile-social-messaging-auto-reply-n8n/issues/new) · [⭐ Star](https://github.com/shaikshahid777/unipile-social-messaging-auto-reply-n8n/stargazers) · [🔱 Fork](https://github.com/shaikshahid777/unipile-social-messaging-auto-reply-n8n/fork) · [👤 Profile](https://github.com/shaikshahid777)

<!-- SHOWCASE_END -->

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
