# FastAPI Notes
## Notes
### Requests
  An HTTP requres consists of a text _header_ followd by one or more _body_ sections.  
  Dat may come from differnt pats of the HTTP message:
  * **Header** - In the HTTP headers
  * **Path** - In the URL
  * **Query** - After the **?** in the URL
  * **Body** - In the HTTP obdy
  * 
  
## Important modules (research) | fastapi
 * pydantic (BaseModel, Field)
 * uuid
 * typing (Optional)
## Response Types  
 * fastapi.responses
   * JSONResponse (the default)
   * HTMLResponse
   * PlainTextResponse
   * RedirectResponse
   * FileResponse
   * StreamingResponse

## Other output formates        | content
(Mime types) generic Response|   String or bytes
Class                        | media_type
                             |   The string MIME type
                             | status_code
                             |   HTTP integer status code
                             | headers
                             |   A dict of strings
                             |
