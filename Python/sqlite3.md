sqlite3 for Python
--------------------------------------------------------------------------------
## connecting
import sqlite3               | import sqlite3
                             |
Establish a db Connection    | connection = sqlite3.connect(file_location)
                             |
Create a Cursor Object       | cursor = connection.cursor()
                             |
--------------------------------------------------------------------------------
## Executing SQL Commands
Create a table               | cursor.execute('''CREATE TABLE IF NOT EXISTS users (
                             |                     id INTEGER PRIMAY KEY,
                             |                     name TEXT NOT NULL,
                             |                     age INTEGER)''')
                             |
Insert data into the table   | cursor.execute("INSERT INTO users (name, age) VALUES(?, ?)", )
                             |
Commit the transaction       | connection.commit()
                             |
--------------------------------------------------------------------------------
Fetching Data
Commands                     | fetchone(), fetchall(), fetchmany
                             |
To fetch data, you must      | cursor.execute("SELECT * FROM users")
collect it first             |
                             |
example of fetching all data | rows = cursor.fetchall()
                             |
--------------------------------------------------------------------------------
Close the connection
Close the connection to      | connection.close()
  ensure proper cleanup and  |
  resource release           |
                             |
                             |
                             |
                             |
                             |
                             |
                             |

