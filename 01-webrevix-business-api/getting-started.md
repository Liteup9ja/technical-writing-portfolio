# Getting Started

Welcome to the Webrevix Business API.

This guide introduces the API and walks developers through the basic concepts required to make their first request.

## Before You Begin

You should have a basic understanding of:

* HTTP requests
* JSON
* REST APIs
* API authentication

You will also need an API key to make authenticated requests.

## Base URL

All API requests use the following base URL:

```text
https://api.example.webrevixng.com/v1
```

For example:

```text
GET https://api.example.webrevixng.com/v1/businesses
```

## Authentication

The API uses API keys to authenticate requests.

Include your API key in the `Authorization` header:

```http
Authorization: Bearer YOUR_API_KEY
```

Keep your API key private. Do not expose it in frontend JavaScript, public repositories, screenshots, or client-side applications.

## Your First Request

The following example retrieves a list of businesses.

### Request

```bash
curl https://api.example.webrevixng.com/v1/businesses \
  -H "Authorization: Bearer YOUR_API_KEY"
```

### Response

A successful request returns a JSON response similar to:

```json
{
  "data": [
    {
      "id": "biz_12345",
      "name": "Example Business",
      "category": "restaurant",
      "status": "active"
    }
  ]
}
```

## Understanding the Response

The response contains a `data` property containing an array of business objects.

Each business includes:

| Field      | Type   | Description                |
| ---------- | ------ | -------------------------- |
| `id`       | string | Unique business identifier |
| `name`     | string | Business name              |
| `category` | string | Business category          |
| `status`   | string | Current business status    |

## HTTP Status Codes

A successful request returns:

```text
200 OK
```

Common errors include:

```text
401 Unauthorized
403 Forbidden
404 Not Found
429 Too Many Requests
500 Internal Server Error
```

See the Errors guide for more information.

## Next Steps

Continue with:

1. Authentication
2. Businesses
3. Leads
4. Webhooks
