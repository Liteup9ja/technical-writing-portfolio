# Errors

The Webrevix Business API uses standard HTTP status codes to indicate whether an API request was successful.

When a request fails, the API returns a JSON response containing information about the error.

## HTTP Status Codes

| Status Code | Meaning               | Description                                                |
| ----------- | --------------------- | ---------------------------------------------------------- |
| `200`       | OK                    | The request was successful                                 |
| `201`       | Created               | A new resource was successfully created                    |
| `204`       | No Content            | The request succeeded without returning a response body    |
| `400`       | Bad Request           | The request contains invalid data                          |
| `401`       | Unauthorized          | Authentication credentials are missing or invalid          |
| `403`       | Forbidden             | The authenticated application does not have permission     |
| `404`       | Not Found             | The requested resource does not exist                      |
| `409`       | Conflict              | The request conflicts with the current state of a resource |
| `422`       | Unprocessable Entity  | The request contains valid JSON but fails validation       |
| `429`       | Too Many Requests     | The API rate limit has been exceeded                       |
| `500`       | Internal Server Error | An unexpected server error occurred                        |

## Error Response Format

When an API request fails, the response contains an error object.

Example:

```json
{
  "error": {
    "code": "invalid_request",
    "message": "The email field is required.",
    "details": {
      "field": "email"
    }
  }
}
```

## Error Fields

| Field     | Type   | Description                            |
| --------- | ------ | -------------------------------------- |
| `code`    | string | Machine-readable error identifier      |
| `message` | string | Human-readable explanation             |
| `details` | object | Additional information about the error |

## Authentication Errors

If an API key is missing or invalid, the API returns:

```http
HTTP/1.1 401 Unauthorized
```

Example response:

```json
{
  "error": {
    "code": "invalid_api_key",
    "message": "The provided API key is invalid."
  }
}
```

Check that your request contains a valid authorization header:

```http
Authorization: Bearer YOUR_API_KEY
```

See the [Authentication](authentication.md) documentation for more information.

## Validation Errors

If a request contains invalid or missing data, the API may return:

```http
HTTP/1.1 422 Unprocessable Entity
```

Example:

```json
{
  "error": {
    "code": "validation_error",
    "message": "The request contains invalid fields.",
    "details": {
      "email": "Must be a valid email address.",
      "status": "Invalid lead status."
    }
  }
}
```

Correct the invalid fields and submit the request again.

## Resource Not Found

If you request a resource that does not exist, the API returns:

```http
HTTP/1.1 404 Not Found
```

Example:

```json
{
  "error": {
    "code": "resource_not_found",
    "message": "Business biz_12345 was not found."
  }
}
```

Verify that the resource ID is correct.

## Rate Limit Errors

The API may limit the number of requests an application can make within a specific period.

When the rate limit is exceeded, the API returns:

```http
HTTP/1.1 429 Too Many Requests
```

Example:

```json
{
  "error": {
    "code": "rate_limit_exceeded",
    "message": "Too many requests. Please try again later."
  }
}
```

Applications should wait before retrying the request.

## Server Errors

A `500 Internal Server Error` indicates that the server encountered an unexpected problem.

Example:

```json
{
  "error": {
    "code": "internal_server_error",
    "message": "An unexpected error occurred."
  }
}
```

If the problem continues, contact the API support team and provide the request details and error response.

## Recommended Error Handling

Applications should handle API errors explicitly.

For example:

```javascript
if (!response.ok) {
  const error = await response.json();

  console.error(error.error.message);
}
```

A production application should also log useful information such as:

* HTTP status code
* Error code
* Request ID, if available
* Endpoint
* Time of the request

Avoid logging sensitive credentials such as API keys.

## Retryable Errors

Some errors may be temporary and can be retried.

Examples include:

* `429 Too Many Requests`
* `500 Internal Server Error`

Applications should use a controlled retry strategy rather than repeatedly sending requests without delay.

## Non-Retryable Errors

Errors caused by invalid request data generally should not be retried without changing the request.

Examples include:

* `400 Bad Request`
* `401 Unauthorized`
* `403 Forbidden`
* `404 Not Found`
* `422 Unprocessable Entity`

Correct the underlying problem before submitting the request again.

## Troubleshooting Checklist

If an API request fails:

1. Check the HTTP status code.
2. Read the error `code`.
3. Read the error `message`.
4. Inspect the `details` object when available.
5. Verify your authentication credentials.
6. Confirm that the endpoint and resource ID are correct.
7. Check whether you have exceeded the rate limit.
8. Retry only when the error is potentially temporary.

## Related Documentation

* [Getting Started](getting-started.md)
* [Authentication](authentication.md)
* [Businesses](businesses.md)
* [Leads](leads.md)
* [Webhooks](webhooks.md)
