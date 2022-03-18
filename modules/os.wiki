[[../Python|index]]
--------------------------------------------------------------------------------
os Module                    | returns a string
                             |
  Change working directory   | import os
                             | os.chdir('/home/<use name>/documents')
                             |
  Create new directory       | os.makedirs('/path/to/new/directory')
                             |
  get list of files in a     | os.listdir(path)
  directory                  |
                             |
  return the absolute path   | os.path.abspath(<path>)
                             |
  is the path Absolute?      | os.path.isabs(<path>)
                             |
  will return the relative   | os.path.relpath(<path>,<start>)
  path                       |
                             |
  Opening files              | fileHandler = open(<path to file>) --> default (read mode)
                             | fileHandler = open(<path to file>, 'r') --> (read mode)
                             |
                             | fileHandler = open(<path to file>, 'w') --> (write mode)
                             | fileHandler = open(<path to file>, 'a') --> (append mode)
                             |
  Reading content            |
    Returns a single large   | fileContent = fileHandler.read()
    string                   |
                             |
    Returns a list of strings| fileContent = fileHandler.readlines()
                             |
  Writing to files           |
    the fileHandler must've  | fileHandler.write(<text content)
    already been opened in   |
    write or append mode     |
                             |
    closing fileHandler      | fileHandler.close()
                             |
  Errors with writing to     |
    PermissionError:         |
                             |
