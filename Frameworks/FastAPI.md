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

## HTTP Requests
```python
Import FastAPI              | from fastapi import FastAPI
                            | 
                            | app = FastAPI
                            | 
Endpoint Creatiion          |
(decorator.REST_VERB)       | @app.get("/hi")
function to be decorated    | def greet():
                            |     return "Hello world"
                            | 
URL PATH                    | @app.get("/hi/{who}")
URL PATH Parameter          | def greet(who):
                            |     return f"Hello {who}"
                            | 
Query Parameter             | @app.get("/hi/{who}")
(indicated as lack of param)| def greet():
                            |     return f"Hello {who}"
                            | 
Passed in Body              | 
Import fastapi.Body         | from fastapi import FastAPI, Body
Post request                | @app.post("/hi")
Body(embed=True)            | def greet(who:str = Body(embed=True)):
obtained from JSON request  |     return f"Hello {who}"
                            | 
Passed in from HEADER       | 
Import fastapi.Header       | from fastapi import FastAPI, Header
Post request                | @app.post("/hi")
Header assigned to who      | def greet(who:str = Header()):
                            |     return f"Hello {who}"
                            | 
Return User-Agent           | 
Import fastapi.Header       | from fastapi import FastAPI, Header
Post request                | @app.post("/agent")
User-agent assigned from HE | def greet(user_agent:str = Header()):
                            |     return user_agent
                            | 
                            | 
                            | 
                            | 
                            | 
                            | 
                            | 
                            | 
                            | 
                            | 
                            | 
                            | 
```
