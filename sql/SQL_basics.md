--------------------------------------------------------------------------------
SQL Basic Commands
--------------------------------------------------------------------------------
Basic Create Table           | CREATE TABLE todos (
                             |         id INTEGER NOT NULL,
                             |         title VARCHAR,
                             |         description VARCHAR,
                             |         priority INTEGER,
                             |         complete BOOLEAN,
                             |         PRIMARY KEY (id)
                             | );
                             |
--------------------------------------------------------------------------------
Basic Inserts                |
  1. Descibe which columns   | INSERT INTO todos (title, description, priority, complete) \
  2. Desribe what values     | VALUES ('Got to store', 'To pick up eggs', 4, False);
                             |
--------------------------------------------------------------------------------
Basic Select queries         | 
  * Select all data          | SELECT * FROM todos;
  * Select data from 1 column| SELECT title FROM todos;
  * Select multiple columns  | SELECT title, description FROM todos;
  * Select based on criteria | SELECT * FROM todos WHERE priority=5; 
      More examples          | SELECT * FROM todos WHERE title='feed dog';
                             | SELECT * FROM todos WHERE id=2;
                             |
--------------------------------------------------------------------------------
Basic Update queries         |
  Update record based on id  | UPDATE todos SET complete=True WHERE id=5;
  UPdate record based on col | UPDATE todos SET complete=True WHERE title='Learn something new';
                             |
--------------------------------------------------------------------------------
Basic Delete                 |
  Delete the 5th record      | DELETE FROM todos WEREE id=5; (safest)
  Delete based on column     | DELETE FROM todos WHERE complete=0; (not safe, may remove multiple records)
                             |
--------------------------------------------------------------------------------
Drop table                   | DROP TABLE todos
                             |
