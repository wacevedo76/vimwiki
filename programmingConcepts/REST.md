--------------------------------------------------------------------------------
= REST API =
--------------------------------------------------------------------------------
HTTP Request Methods
  GET                        | Requests a representation of a specific resource.
                             | This type of request should only receive data
                             |
  HEAD                       | Like a GET request, but only receiving the headers
                             | (no response body)
                             |
  POST                       | Submits data to the application, usually causing
                             | a change in the application's state
                             |
  PUT                        | Replaces the current representation fothe target
                             | resource
                             |
  DELETE                     | Deletes the specified resouce
                             |
  PATCH                      | Partially modifies a resource
                             |
--------------------------------------------------------------------------------
== Application Architecture ==
  MVC (Flask)          Model | It holds onto the data and business logic. Ideally,
                             | the model holds onto "The brains" of our application
                             |
                        view | This is the representation of our business logic.
                             | For our application, the view portion will be the HTML
                             | templates that were rendered and return
                             |
                  Controller | This is the input/output interface for the application.
                             | The controller receives requests, then utilizes the
                             | model and view to display the properties in Flask,
                             | there are a few different ways to create a "controller",
                             | but in its simplest form the controller will actually
                             | Be the Flask application itself
                             |
                             |
                             |
                             |
                             |
                             |
                             |
