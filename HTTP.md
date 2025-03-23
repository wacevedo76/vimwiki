# HTTP Notes

## Key Propterties of an HTTP POST Header
1. `Host`:
    * Specifies the domain name of the server.
    *  Example: `Host: example.com`
2. `Content-Type`:
    * Describes the type of data being sent in the request body.
      * Common Values:
         * `application/json` (for JSON data)
         * `application/x-www-form-urlencoded` (for form data)
         * `multipart/form-data` (for file uploads)
    * Example: `Content-Type: application/json`
3. `Content-Length`:
    * Specifies the size of the request body in bytes.
    * Examle: `Content-Length: 120`
4. `User-Agent`:
    * Identifies the client making the request (e.g., browser, API client)
    * Example: `User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64)`
5. `Authorization`:
    * Contains authentication credentials (e.g., API key, Bearer token)
    * Example: `Authorization: Bearer your-access-token`
6. `Accept`:
    * Informs the server about the response formats the client can handle
    * Example `Accept: application/json`
7. `Accept-Encoding`:
    * Defines whether to keep the connection open for further request
    * Example: `Accept-Encoding: gzip, deflate`
8. `Connection`:
    * Defines whether to keep the connection open for further request
    * Example: `Connection: keep-alive`
9. `Cache-Control`:
    * Controls caching behavior (e.g., no-cache, max-age)
    * Example: `Cache-Control: no-cache`
10. `Refere`:
    * Indicates the URL the request originated from
    * Example: `Referer: https://example.com/form`
11. `Origin`:
    * Specifies the origin of the request (important for CORS)
    * Example: `Origin: https://client.com`
12. `Cookie`:
    * Contains stored session data for the request
    * Example: `Cookie: sessionid=abc123`

### Example HTTP POST Request
```
POST /api/login HTTP/1.1
Host: example.com
Content-Type: application/json
Content-Length: 50
Authorization: Bearer your-access-token
User-Agent: PostmanRuntime/7.29.0
Accept: application/json
Accept-Encoding: gzip, deflate
Connection: keep-alive

{
    "username": "user123",
    "password": "mypassword"
}
```
