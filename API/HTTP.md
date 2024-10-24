# HTTP Notes
## Headers
HTTP Headers are key-value pairs sent between a client and a server in an HTTP
request or response. They provide important information about the request or
response, allowing the client and server to communicate effectively. Headers
convey metadata, such as the format of the message, authentication details,
caching directives, and more.  

### There are two main types of HTTP headers:
1. **Request Headers**: These are sent from the client (e.g., a browser or an
   API client) to the server to provide additional information about the
   request. Example include:
   * `Content-Type`: indicates the type of content being sent (e.g., `application/json`).
   * `Authorization`: Contains credentials for authentication (e.g., `Bearer <token>`)
   * `User-Agent`: Provides information about the client making the request (e.g., browser version).
   * `Accept`: Indicates what content types the client can understand (`application/json`).  
2. **Response Headers**: These are sent from the server to the client to provide
   additional information about the response. Examples include:
   * `Content-Type`: Specifies the media type of the response body(e.g., `application/json`).
   * `Set-Cookie`: Used by the server to send cookies that should be stored by the client.
   * `Cache-Control`: Provides caching instructions (e.g., `no-cache`, `max-age=3600`).
   * `Access-Control-Allow-Origin`: Indicates if the response can be shared across different origins, used in CORS.

### Common Uses of HTTP Headers:
* **Authentication**: Headers like `Authorization` are used for passing credentials.
* **Caching**: Headers such as `Cache-Control` and `Expires` help manage caching behavior.
* **Content Negotiation**: The client can specify the format it prefers using headers like `Accept`, and the serve can respond accordingly.
* **CORS**: Cross-Origin Resouce Sharing headers (`Access-Control-*`) manage which domains are allowed to interact with the server.

## URL String
In the context of HTTP and APIs, a URL (Uniform Resource Locator) is a string
that specifies the location of a resource on the internet, such as a webpage or
an API endpoint. A URL allows clients (e.g., web browsers, mobile apps, API
clients) to communicate with a server and access a specific resource, such as
data or files.  

### URL Structure
A URL typically has the following structure:
```bash
scheme://host:port/path?query#fragment
```

Let's break down the components:
1. **Scheme**:
  * Specifies the protocol used to access the resource.
  * Common examples are `http` or `https` (e.g., `https://` indicates a secure connection).
2. **Host**:
  * The domain name or IP address of theserver that hosts the resource (e.g., `api.example`).
3. **Port**(optional):
  * Specifies the port number on ther server.
  * Default ports are `80` for `http` and `443` for `https`. If these ports are used, they are often omitted from the URL.
4. **Path**:
  * Indicates the specific resource on the server, like the directory or file (`/api/v1/users`).
  * Paths are used in REST APIs to represent different endpoints. For example:
    * `/api/v1/users` may represent user data.
    * `/api/v1/users/123` may represent a specific user with ID `123`
5. **Query String** (optional):
  * Contains parameters passed to the server, starting with a `?`.
  * It consists of key-value pairs separated by `&` (e.g., `?sort=asc&limit=10`).
  * Query strings are used to filter, sort, or paginate results in APIs.
  * Example: `/api/v1/rpoducts?category=electronics&limit=5` may be used to filter products by category and limit the number of results.
6. **Fragment** (optional):
  * An anchor or fragment identifier, starting with `#`.
  * Primarily used in web pages to identify sections within a document (e.g., `#section2`). Not commonly used in API calls.
