# Troubleshooting

## 401 Unauthorized

Check the Unipile API credential, token validity, authentication header, and credential binding in n8n. Regenerate the token if it has expired or been revoked.

## 403 Forbidden

Check account permissions, token scopes, provider/account state, and whether the connected account is authorized for the requested operation.

## Account DISCONNECTED

Reconnect the LinkedIn account through Unipile Hosted Connection, then verify the account reports a healthy operational status before testing.

## Missing webhook events

Verify that the workflow is Published/Active, the registered callback URL is the production n8n webhook URL, the correct account is connected, and the messaging event subscription is enabled.

## Duplicate webhook deliveries

Treat message_id as the idempotency key. Look it up before writing/sending so a repeated event is recorded as DUPLICATE and does not trigger a second reply.
