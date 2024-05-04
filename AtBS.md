# AtBS
## Chapter 7
  * this notes makes the assumtion that the reader has a sold understanding of
    the basics of regular expressions
    
  * [Regular expressions](programmingConcepts/re)

## Chapter 9
```
  file path separator        | from pathlib import Path
  (Windows \, Unix /)        | Path('Documents', 'Testfiles', 'exeFiles')
                             |   WindowsPath('Documents/Testfiles/exeFiles')
  Path() returns an          | str(Path('Documents', 'Testfiles', 'exeFiles))
  PathObject                 |   'Documents\\Testfiles\\exefiles'
                             |
                             | *Use Case*
                             |  ------------------------------------------------
                             |  >>> From pathlib import Path
                             |  >>> myFiles = ['accounts.txt', 'details.csv', 'invite.docx']
                             |  >>> for filename in myFiles:
                             |          print(Path(r'C:\Users\A1', filename))
                             |
                             |  C:\Users\A1\accounts.txt
                             |  C:\Users\A1\details.csv
                             |  C:\Users\A1\invite.docx
                             |  ------------------------------------------------
                             |
  Concatinate PathObjects    |
    with '/'                 |
                             |
  The 'os' libraray          |
    get absolute path        | os.path.abspath('.')
    of cwd                   |
                             |
Reading and writing with     |
```
