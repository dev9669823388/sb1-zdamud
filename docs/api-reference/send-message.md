# Send Message

Send WhatsApp messages using various HTTP methods.

## Endpoint

```http
POST https://beta.whats91.com/api/v5/?action=send
```

## Methods

### GET Request

Send a message by passing parameters directly in the URL.

#### Request

```http
GET https://beta.whats91.com/api/v5/?action=send&senderId=917000782082&authToken=33-z41cepdnttJoLHIZn7zcQitR49dVg2WBMooeAdQie5b0efe5&messageText=Test+02&receiverId=919425008429&mediaurl=https://beta.whats91.com/mms/mms_1727672203.jpg
```

#### cURL Example

```bash
curl --location 'https://beta.whats91.com/api/v5/?action=send&senderId=917000782082&authToken=33-z41cepdnttJoLHIZn7zcQitR49dVg2WBMooeAdQie5b0efe5&messageText=Test+02&receiverId=919425008429&mediaurl=https://beta.whats91.com/mms/mms_1727672203.jpg'
```

#### Response

```json
{
    "status": "success",
    "message": "Message sent successfully",
    "messageId": "123456789"
}
```

### POST - URL Encoded

Send a message using URL-encoded form data.

#### Request

```http
POST https://beta.whats91.com/api/v5/?action=send
Content-Type: application/x-www-form-urlencoded

senderId=917000782082&authToken=33-z41cepdnttJoLHIZn7zcQitR49dVg2WBMooeAdQie5b0efe5&messageText=Test+02&receiverId=919425008429&mediaurl=https://beta.whats91.com/mms/mms_1727672203.jpg
```

#### cURL Example

```bash
curl --location 'https://beta.whats91.com/api/v5/?action=send' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--data-urlencode 'senderId=917000782082' \
--data-urlencode 'authToken=33-z41cepdnttJoLHIZn7zcQitR49dVg2WBMooeAdQie5b0efe5' \
--data-urlencode 'messageText=Test 02' \
--data-urlencode 'receiverId=919425008429' \
--data-urlencode 'mediaurl=https://beta.whats91.com/mms/mms_1727672203.jpg'
```

#### Response

```json
{
    "status": "success",
    "message": "Message sent successfully",
    "messageId": "123456789"
}
```

### POST - JSON Body

Send a message using JSON in the request body.

#### Request

```http
POST https://beta.whats91.com/api/v5/?action=send
Content-Type: application/json

{
    "senderId": "917000782082",
    "authToken": "33-z41cepdnttJoLHIZn7zcQitR49dVg2WBMooeAdQie5b0efe5",
    "messageText": "Test 02",
    "receiverId": "919425008429",
    "mediaurl": "https://beta.whats91.com/mms/mms_1727672203.jpg"
}
```

#### cURL Example

```bash
curl --location 'https://beta.whats91.com/api/v5/?action=send' \
--header 'Content-Type: application/json' \
--data-raw '{
    "senderId": "917000782082",
    "authToken": "33-z41cepdnttJoLHIZn7zcQitR49dVg2WBMooeAdQie5b0efe5",
    "messageText": "Test 02",
    "receiverId": "919425008429",
    "mediaurl": "https://beta.whats91.com/mms/mms_1727672203.jpg"
}'
```

#### Response

```json
{
    "status": "success",
    "message": "Message sent successfully",
    "messageId": "123456789"
}
```

### POST - Form Data

Send a message with file upload using form data.

#### Request

```http
POST https://beta.whats91.com/api/v5/?action=send
Content-Type: multipart/form-data

--boundary
Content-Disposition: form-data; name="senderId"

917000782082
--boundary
Content-Disposition: form-data; name="authToken"

33-z41cepdnttJoLHIZn7zcQitR49dVg2WBMooeAdQie5b0efe5
--boundary
Content-Disposition: form-data; name="messageText"

Test 02
--boundary
Content-Disposition: form-data; name="receiverId"

919425008429
--boundary
Content-Disposition: form-data; name="mediaurl"

https://beta.whats91.com/mms/mms_1727672203.jpg
--boundary
Content-Disposition: form-data; name="uploadFile"; filename="image.jpg"
Content-Type: image/jpeg

[Binary file content]
--boundary--
```

#### cURL Example

```bash
curl --location 'https://beta.whats91.com/api/v5/?action=send' \
--form 'senderId="917000782082"' \
--form 'authToken="33-z41cepdnttJoLHIZn7zcQitR49dVg2WBMooeAdQie5b0efe5"' \
--form 'messageText="Test 02"' \
--form 'receiverId="919425008429"' \
--form 'mediaurl="https://beta.whats91.com/mms/mms_1727672203.jpg"' \
--form 'uploadFile=@"/path/to/file.jpg"'
```

#### Response

```json
{
    "status": "success",
    "message": "Message sent successfully",
    "messageId": "123456789",
    "uploadedFile": {
        "url": "https://beta.whats91.com/mms/uploaded_123456.jpg",
        "type": "image/jpeg",
        "size": 1024567
    }
}
```

## Error Responses

When an error occurs, the API will respond with an appropriate HTTP status code and a JSON error message:

```json
{
    "status": "error",
    "code": "INVALID_AUTH",
    "message": "Invalid authentication token provided"
}
```

Common error codes:
- `INVALID_AUTH`: Authentication token is invalid or expired
- `INVALID_SENDER`: Sender ID is not registered or invalid
- `INVALID_RECEIVER`: Receiver ID is invalid
- `MEDIA_ERROR`: Error processing media file or URL
- `MESSAGE_FAILED`: Message failed to send