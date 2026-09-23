# Authentication

The Webrevix Business API uses API keys to authenticate requests.

An API key identifies your application when it communicates with the API.

## API Keys

Each application should use its own API key.

API keys should be treated as sensitive credentials.

Do not:

* Share API keys publicly
* Commit API keys to GitHub
* Include API keys in screenshots
* Expose API keys in frontend JavaScript
* Send API keys to untrusted third parties

## Authorization Header

Send your API key using the HTTP `Authorization` header.

The format is:

```http
Authorization: Bearer YOUR_API_KEY
```

Replace `YOUR_API_KEY` with your actual API key.

## Example Request

The following example retrieves businesses using an authenticated request:

```bash
curl https://api.example.webrevixng.com/v1/businesses \
  -H "Authorization: Bearer YOUR_API_KEY"
```

## JavaScript Example

You can also authenticate requests using JavaScript:

```javascript
fetch("https://api.example.webrevixng.com/v1/businesses", {
  headers: {
    "Authorization": "Bearer YOUR_API_KEY"
  }
});
```

## Python Example

The same request can be made using Python:

```python
import requests

response = requests.get(
    "https://api.example.webrevixng.com/v1/businesses",
    headers={
        "Authorization": "Bearer YOUR_API_KEY"
    }
)

print(response.json())
```

## Invalid API Key

If the API key is missing or invalid, the API returns:

```text
401 Unauthorized
```

Example error response:

```json
{
  "error": {
    "code": "invalid_api_key",
    "message": "The API key provided is invalid."
  }
}
```

## Security Best Practices

Keep API keys secure at all times.

For server-side applications, store API keys in environment variables rather than directly inside source code.

For example:

```text
WEBREVIX_API_KEY=your_api_key
```

Applications should load the value from the environment when making API requests.

## Next Steps

After configuring authentication, continue to the [Businesses](businesses.md) documentation to learn how to create and manage business records.
