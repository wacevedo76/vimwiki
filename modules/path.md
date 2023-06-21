[[../Python|index]]
--------------------------------------------------------------------------------
 pathlib Module
                             | returns a Path object
                             |
                             | the path module is primarily used to form paths
                             | that translate between windows and linux file systems
                             |
  Createing paths            | from pathlib import Path
    pathlib module           | Path('spam', 'bacon', 'eggs')
                             |    *nix --> spam/bacon/eggs
                             |    Windows --> 'spam\\bacon\\eggs'
                             |
                             | myFiles = ['file01', 'file02', 'file03']
                             | for file in myFiles:
                             |     print(Path(r'C:\Users\A1', file'))
                             |
  Joining paths with /       | Path('spam') / Path('bacon', 'egs')
                             |
  Current working directory  | Path.cwd()
                             |
  Get path object of home    | Path.home()
  directory                  |
                             |
  Is the path absolute       | Path.cwd().is_absolute --> True
                             | Path('spam/bacon/eggs').is_absolute --> False
                             |
  Get the parts of a path    | PathObject.drive
                             | PathObject.anchor
                             | PathObject.parent
                             | PathObject.name
                             | PathObject.stem
                             | PathObject.suffix
