# API Parameters

## Required Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| senderId | string | Your WhatsApp number that will send the message |
| authToken | string | Your authentication token |
| messageText | string | The message content to send |
| receiverId | string | Recipient's WhatsApp number |

## Optional Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| mediaurl | string | URL of media to send (images, videos, etc.) |
| uploadFile | file | File to upload when using form-data method |

## Parameter Format

- Phone numbers should include country code (e.g., 917000782082)
- Media URLs must be publicly accessible
- Uploaded files must be in supported formats (jpg, png, pdf, etc.)