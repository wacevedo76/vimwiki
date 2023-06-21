--------------------------------------------------------------------------------
= The SED command =
--------------------------------------------------------------------------------
== General notes ==
Sed takes input from the command line or from a file (line by line) and is able
to perform a series of patterns / commands on each like  and output the results

  Options:                   |
    repressing sed's default | -n
    print behavior           |   example:  sed -n '<pattern>'
                             |
  Patterns:                  |
    search and replace       | 's/be/are/'
                             |   example: sed 's/be/are/'
    (similar to vim's search |
     and replace)            |
                             |
    bracket expansion        | {<first-command>; <second-command>; <third-command>}
    (run multiple commands)  |   example: sed -n '2,3 {s/are/be/g; p}' <- replaces are with be
                             |                              and only prints 2sn and 3rd line
                             |
  Delete Specific lines      | sed -i -e '25d' ~/name/of/file
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
