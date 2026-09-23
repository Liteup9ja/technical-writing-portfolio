# Businesses

The Businesses API allows applications to create, retrieve, update, and delete business records.

A business record represents a company, organization, or local business managed through the Webrevix platform.

## Business Object

A business object contains information such as its name, category, location, and current status.

Example:

```json
{
  "id": "biz_12345",
  "name": "Example Restaurant",
  "category": "restaurant",
  "location": "Lagos, Nigeria",
  "status": "active"
}
```

## List Businesses

Returns a list of businesses associated with your account.

### Endpoint

```http
GET /v1/businesses
```

### Request

```bash
curl https://api.example.webrevixng.com/v1/businesses \
  -H "Authorization: Bearer YOUR_API_KEY"
```

### Response

```json
{
  "data": [
    {
      "id": "biz_12345",
      "name": "Example Restaurant",
      "category": "restaurant",
      "location": "Lagos, Nigeria",
      "status": "active"
    }
  ]
}
```

### Response Fields

| Field      | Type   | Description                        |
| ---------- | ------ | ---------------------------------- |
| `id`       | string | Unique identifier for the business |
| `name`     | string | Name of the business               |
| `category` | string | Business category                  |
| `location` | string | Business location                  |
| `status`   | string | Current business status            |

## Create a Business

Creates a new business record.

### Endpoint

```http
POST /v1/businesses
```

### Request Body

```json
{
  "name": "Example Restaurant",
  "category": "restaurant",
  "location": "Lagos, Nigeria"
}
```

### cURL Example

```bash
curl -X POST https://api.example.webrevixng.com/v1/businesses \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Example Restaurant",
    "category": "restaurant",
    "location": "Lagos, Nigeria"
  }'
```

### Response

```json
{
  "id": "biz_12345",
  "name": "Example Restaurant",
  "category": "restaurant",
  "location": "Lagos, Nigeria",
  "status": "active"
}
```

A successful request returns:

```text
201 Created
```

## Get a Business

Returns information about a specific business.

### Endpoint

```http
GET /v1/businesses/{business_id}
```

Replace `{business_id}` with the ID of the business you want to retrieve.

### Example

```bash
curl https://api.example.webrevixng.com/v1/businesses/biz_12345 \
  -H "Authorization: Bearer YOUR_API_KEY"
```

### Response

```json
{
  "id": "biz_12345",
  "name": "Example Restaurant",
  "category": "restaurant",
  "location": "Lagos, Nigeria",
  "status": "active"
}
```

## Update a Business

Updates an existing business record.

### Endpoint

```http
PATCH /v1/businesses/{business_id}
```

### Request Body

```json
{
  "name": "Example Restaurant Lagos",
  "location": "Ikeja, Lagos"
}
```

### Example

```bash
curl -X PATCH https://api.example.webrevixng.com/v1/businesses/biz_12345 \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Example Restaurant Lagos",
    "location": "Ikeja, Lagos"
  }'
```

### Response

```json
{
  "id": "biz_12345",
  "name": "Example Restaurant Lagos",
  "category": "restaurant",
  "location": "Ikeja, Lagos",
  "status": "active"
}
```

A successful update returns:

```text
200 OK
```

## Delete a Business

Permanently deletes a business record.

### Endpoint

```http
DELETE /v1/businesses/{business_id}
```

### Example

```bash
curl -X DELETE https://api.example.webrevixng.com/v1/businesses/biz_12345 \
  -H "Authorization: Bearer YOUR_API_KEY"
```

A successful deletion returns:

```text
204 No Content
```

## Common Errors

| Status | Error                 | Description                           |
| ------ | --------------------- | ------------------------------------- |
| `400`  | Bad Request           | The request contains invalid data     |
| `401`  | Unauthorized          | Authentication failed                 |
| `404`  | Not Found             | The requested business does not exist |
| `429`  | Too Many Requests     | Rate limit exceeded                   |
| `500`  | Internal Server Error | An unexpected server error occurred   |

## Related Documentation

* [Getting Started](getting-started.md)
* [Authentication](authentication.md)
* [Leads](leads.md)
* [Webhooks](webhooks.md)
* [Errors](errors.md)
