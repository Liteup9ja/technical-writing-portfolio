# Leads

The Leads API allows applications to create, retrieve, and update leads associated with a business.

A lead represents a potential customer who has expressed interest in a business, product, or service.

## Lead Object

A lead contains information about a potential customer.

Example:

```json
{
  "id": "lead_12345",
  "name": "John Doe",
  "email": "john@example.com",
  "phone": "+2348012345678",
  "source": "website",
  "status": "new"
}
```

## Lead Status

A lead can have one of the following statuses:

| Status      | Description                                      |
| ----------- | ------------------------------------------------ |
| `new`       | Newly created lead                               |
| `contacted` | Business has contacted the lead                  |
| `qualified` | Lead has been identified as a potential customer |
| `converted` | Lead became a customer                           |
| `lost`      | Lead is no longer active                         |

---

# Create a Lead

Creates a new lead for a business.

## Endpoint

```http
POST /v1/leads
```

## Request Body

```json
{
  "business_id": "biz_12345",
  "name": "John Doe",
  "email": "john@example.com",
  "phone": "+2348012345678",
  "source": "website"
}
```

## Parameters

| Field         | Type   | Required | Description                      |
| ------------- | ------ | -------- | -------------------------------- |
| `business_id` | string | Yes      | ID of the associated business    |
| `name`        | string | Yes      | Full name of the lead            |
| `email`       | string | Yes      | Email address                    |
| `phone`       | string | No       | Phone number                     |
| `source`      | string | No       | Source where the lead originated |

## cURL Example

```bash
curl -X POST https://api.example.webrevixng.com/v1/leads \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "business_id": "biz_12345",
    "name": "John Doe",
    "email": "john@example.com",
    "phone": "+2348012345678",
    "source": "website"
  }'
```

## Response

```json
{
  "id": "lead_12345",
  "business_id": "biz_12345",
  "name": "John Doe",
  "email": "john@example.com",
  "phone": "+2348012345678",
  "source": "website",
  "status": "new"
}
```

A successful request returns:

```text
201 Created
```

---

# List Leads

Returns a list of leads associated with a business.

## Endpoint

```http
GET /v1/leads
```

## Query Parameters

| Parameter     | Type    | Required | Description               |
| ------------- | ------- | -------- | ------------------------- |
| `business_id` | string  | Yes      | Filter leads by business  |
| `status`      | string  | No       | Filter leads by status    |
| `limit`       | integer | No       | Number of leads to return |

## Example Request

```bash
curl "https://api.example.webrevixng.com/v1/leads?business_id=biz_12345&status=new" \
  -H "Authorization: Bearer YOUR_API_KEY"
```

## Response

```json
{
  "data": [
    {
      "id": "lead_12345",
      "business_id": "biz_12345",
      "name": "John Doe",
      "email": "john@example.com",
      "status": "new"
    },
    {
      "id": "lead_12346",
      "business_id": "biz_12345",
      "name": "Jane Smith",
      "email": "jane@example.com",
      "status": "new"
    }
  ]
}
```

---

# Get a Lead

Returns information about a specific lead.

## Endpoint

```http
GET /v1/leads/{lead_id}
```

Replace `{lead_id}` with the ID of the lead.

## Example

```bash
curl https://api.example.webrevixng.com/v1/leads/lead_12345 \
  -H "Authorization: Bearer YOUR_API_KEY"
```

## Response

```json
{
  "id": "lead_12345",
  "business_id": "biz_12345",
  "name": "John Doe",
  "email": "john@example.com",
  "phone": "+2348012345678",
  "source": "website",
  "status": "new"
}
```

---

# Update a Lead

Updates information associated with an existing lead.

## Endpoint

```http
PATCH /v1/leads/{lead_id}
```

## Request Body

For example, to change the lead status:

```json
{
  "status": "contacted"
}
```

## Example

```bash
curl -X PATCH https://api.example.webrevixng.com/v1/leads/lead_12345 \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "status": "contacted"
  }'
```

## Response

```json
{
  "id": "lead_12345",
  "business_id": "biz_12345",
  "name": "John Doe",
  "email": "john@example.com",
  "phone": "+2348012345678",
  "source": "website",
  "status": "contacted"
}
```

A successful update returns:

```text
200 OK
```

---

# Lead Workflow

A typical lead workflow might look like this:

```text
Website Form
     ↓
POST /v1/leads
     ↓
Lead Created
     ↓
status: new
     ↓
Business Contacts Lead
     ↓
status: contacted
     ↓
Lead Becomes Customer
     ↓
status: converted
```

This workflow can be connected to external automation systems using webhooks.

See the Webhooks documentation for more information.

---

# Common Errors

| Status | Description                |
| ------ | -------------------------- |
| `400`  | Invalid lead data          |
| `401`  | Invalid authentication     |
| `404`  | Lead or business not found |
| `422`  | Validation failed          |
| `429`  | Rate limit exceeded        |
| `500`  | Internal server error      |

---

# Related Documentation

* [Getting Started](getting-started.md)
* [Authentication](authentication.md)
* [Businesses](businesses.md)
* [Webhooks](webhooks.md)
* [Errors](errors.md)
