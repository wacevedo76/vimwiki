# Python Debugger (pdb)

## Take aways:
* Python's standard debugger is called PDB.
* PDB is a standard command-line debugger.
* The pdb.set_trace() method can be used to stop program execution and enter the debugger.
* Your REPL's prompt will change to (Pdb) when you're in the debugger.
* You can access PDB's built-in help system by typing "help".
* You can use `python -m pdb` followed by a script name to run a program under PDB from the start.
* PDB's `where` command shows the current call stack.
* PDB's `next` command lets execution continue to the next line of code.
* PDB's `continue` command lets program execution continue indefinitely, or until you stop it with controll-c.
* PDB's `list` command shows you the source code at your current location.
* PDB's `return` command resumes execution until the end of the current function.
* PDB's `print` command lets you see the values of objects in the debugger.
* Use `quit` to exit PDB.

## Available Commands  

| EOF      | cl      | disable | interact | next     | return |
| u        | a       | clear   | display  | j        | p      |
| retval   | unalias | alias   | commands | down     | jump   |
| l        | print   | rv      | unt      | b        | cont   |
| exit     | list    | q       | s        | until    | break  |
| continue | h       | ll      | quit     | source   | u      |
| p        | bt      | d       | help     | longlist | r      |
| step     | w       | c       | debug    | ignore   | n      |
| restart  | tbreak  | whatis  | where    |          |        |
  
## Commonly Used Commands
| ------------------------- | ------------------------------------------------ |
| automatically load module | python -m pdb <filename>                         |
| within pdb                |                                                  |
|                           |                                                  |
| Include a break point     | import pdb: pdb.set_trace()                      |
|                           |                                                  |
| print pointer location    | where                                            |
| from within pdb           |                                                  |
|                           |                                                  |
| ------------------------- | ------------------------------------------------ |

