# Testing & Validation

## Live end-to-end test

A real LinkedIn message was used to validate the published workflow.

1. External LinkedIn user sends a message.
2. Unipile delivers the message_received event.
3. n8n extracts and validates the payload.
4. Google Sheets logs the message.
5. Unipile sends the confirmation reply.
6. The sheet is updated with SUCCESS and the reply message ID.

## Evidence

[Loom demonstration](https://www.loom.com/share/3fd44a3badf84f07a6908205d3554a22)

The workflow also contains explicit branches for invalid payloads, duplicate messages, and outbound-send failures.
