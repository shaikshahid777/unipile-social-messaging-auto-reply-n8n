# Google Sheets Schema

## Messages tab

| Column | Purpose |
|---|---|
| message_id | Unique incoming message identifier / idempotency key |
| chat_id | Unipile chat identifier used for reply |
| sender_name | Sender display name |
| sender_id | Sender identifier |
| provider | Messaging provider, e.g. LINKEDIN |
| message_text | Incoming message text |
| timestamp | Event/message timestamp |
| event_name | Webhook event name |
| reply_status | PENDING, SUCCESS, FAILED, DUPLICATE, or INVALID_PAYLOAD |
| reply_message_id | Outbound reply identifier when available |
| processed_at | Workflow processing timestamp |
