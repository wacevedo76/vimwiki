--------------------------------------------------------------------------------
# FastAPI
--------------------------------------------------------------------------------
Important modules (research) | fastapi
                             | pydantic (BaseModel, Field)
                             | uuid
                             | typing (Optional)
                             |
--------------------------------------------------------------------------------
Response Types               |
fastapi.responses            | * JSONResponse (the default)
                             | * HTMLResponse
                             | * PlainTextResponse
                             | * RedirectResponse
                             | * FileResponse
                             | * StreamingResponse
                             |
Other output formates        | content
(Mime types) generic Response|   String or bytes
Class                        | media_type
                             |   The string MIME type
                             | status_code
                             |   HTTP integer status code
                             | headers
                             |   A dict of strings
                             |
