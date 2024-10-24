# Rest(ful) API Notes
##Fundamentals
The characteristis of **RESTful** apis:
* Uses HTTP and client-server protocol
* Statless (each connection is independent)
* Cacheable
* Resource-based
A *resource* is data that you can distinguish and perform operations on. A web
service provides an *endpoint*- a distinct URL and HTTP verb (action) - for each
feature that it wants to expose. An endpoint is also called a *route*, because
it routes the URL to a function.
* **POST**
  Create (write)
* **PUT**
  Modify completely (replace)
* **PATCH**
  Modify partially (update)
* **GET**
  Get (read, retrieve)
* **DELETE**
  Delete
A client sends a *request* to a RESTful endpoint with data in one of the
following areas of an HTTP message:
* Headers
* The URL string
* Query parameters
* Body values
In turn, an HTTP response returns these:
* An integer ***status code*** indicating the following:
  * 100s - Info, keep going
  * 200s - Success
  * 300s - Redirection
  * 400s - Client error
  * 500s - Server error
* Various headers
* A body, which may be empty, single, or *chunked* (in successive pieces)

