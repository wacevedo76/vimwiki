--------------------------------------------------------------------------------
Notes from The Awk Programming language
--------------------------------------------------------------------------------
* Summary of patterns
BEGIN { statements }         | The statements are executed once before any input
                             | has been read
                             |
END { statements }           | The statements are executed once after all input
                             | has been read
                             |
expression { statements }    | The statements are executes at each input line
                             | where the expression is ture, that is nonzero or
                             | nonnull
                             |
/reg ex/ { statements }      | The statements are executed at each input line
                             | that contains a string matched by the reg ex
                             |
compound pattern {statements}| A compound pattern combines expression with &&
                             | (AND), || (OR), ! (NOT), and parentheses; the
                             | statements are executed at each input line where
                             | the compound pattern is true.
                             |
pattern, patters {statements}| A range pattern matches each input line from a
      1        2             | line matched by pattern1 to the next line match
                             | line matched by pattern2, inclusive; the statements
                             | are executed at each matching line.
                             |
NF                           |
                             |
                             |
                             |
                             |
                             |
