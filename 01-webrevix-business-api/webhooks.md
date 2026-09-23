# Webhooks

Webhooks allow the Webrevix Business API to notify an external application when an event occurs.

Instead of repeatedly requesting the API to check whether something has changed, an application can provide a webhook URL and receive notifications automatically.

## How Webhooks Work

A typical webhook workflow looks like this:

```text
Event occurs
     ↓
Webrevix detects the event
     ↓
Webrevix sends an HTTP request
     ↓
Your webhook URL receives the request
     ↓
Your application processes the event
```

For example:

```text
Customer submits form
        ↓
Lead is created
        ↓
Webrevix generates lead.created event
        ↓
Webhook request is sent
        ↓
Your CRM receives the lead
```

## Webhook Events

The API currently supports the following events:

| Event              | Description                           |
| ------------------ | ------------------------------------- |
| `lead.created`     | A new lead has been created           |
| `lead.updated`     | An existing lead has been updated     |
| `business.created` | A new business has been created       |
| `business.updated` | An existing business has been updated |

## Webhook URL

To receive webhook events, your application must provide a publicly accessible HTTPS endpoint.

Example:

```text
https://example.com/webhooks/webrevix
```

Your endpoint should accept HTTP `POST` requests.

## Example Webhook Request

When a new lead is created, Webrevix sends a request similar to:

```http
POST /webhooks/webrevix HTTP/1.1
Host: example.com
Content-Type: application/json
```

The request body contains information about the event.

```json
{
  "id": "evt_12345",
  "type": "lead.created",
  "created_at": "2026-09-23T10:30:00Z",
  "data": {
    "lead": {
      "id": "lead_12345",
      "business_id": "biz_12345",
      "name": "John Doe",
      "email": "john@example.com",
      "status": "new"
    }
  }
}
```

## Event Structure

Every webhook event contains the following fields:

| Field        | Type   | Description                    |
| ------------ | ------ | ------------------------------ |
| `id`         | string | Unique event identifier        |
| `type`       | string | Type of event                  |
| `created_at` | string | Time the event was created     |
| `data`       | object | Data associated with the event |

## Handling Webhook Events

Your application should inspect the `type` field to determine which action to perform.

For example:

```javascript
if (event.type === "lead.created") {
  // Process the new lead
}
```

A lead could then be:

```text
Webrevix
   ↓
Webhook
   ↓
Your server
   ↓
CRM
   ↓
Email notification
   ↓
Sales team
```

## Successful Response

Your webhook endpoint should return a successful HTTP response after receiving and processing the event.

For example:

```http
HTTP/1.1 200 OK
```

If your endpoint successfully receives the request but processes it asynchronously, it can acknowledge the request first and process the event afterward.

## Failed Webhook Delivery

If Webrevix does not receive a successful response, the event may be retried.

Common reasons for a failed delivery include:

* Server timeout
* Invalid webhook URL
* DNS failure
* Network failure
* Server returning an error status
* SSL/TLS configuration problems

## Respond Quickly

Webhook endpoints should acknowledge requests quickly.

For long-running operations, consider:

1. Receiving the webhook
2. Validating the request
3. Returning a successful response
4. Processing the event asynchronously

This helps prevent unnecessary delivery retries.

## Security

Webhook endpoints should be protected.

Do not assume that every request sent to your endpoint is legitimate.

Production webhook systems should use request-signing or another verification mechanism to allow the receiving application to confirm that the request originated from the expected service.

Webhook URLs should also use HTTPS.

## Testing Webhooks

During development, you can use a temporary webhook endpoint or a local development tool that exposes your application to the internet.

For example:

```text
https://example.com/webhooks/webrevix
```

Send a test event to verify that your application correctly receives and processes the request.

## Example Lead Workflow

A complete lead workflow could look like:

```text
Website
   ↓
Customer submits contact form
   ↓
POST /v1/leads
   ↓
Webrevix creates lead
   ↓
lead.created
   ↓
Webhook
   ↓
CRM
   ↓
Sales notification
```

This allows developers to connect the Webrevix API to other business systems and automation platforms.

## Related Documentation

* [Getting Started](getting-started.md)
* [Authentication](authentication.md)
* [Businesses](businesses.md)
* [Leads](leads.md)
* [Errors](errors.md)
