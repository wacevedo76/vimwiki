--------------------------------------------------------------------------------
= Regular expressions =
--------------------------------------------------------------------------------
== Regular expressions in Bash ==
--------------------------------------------------------------------------------
  grep                       |
    -i                       | Allows us to search case-insensitively
    -v                       | Only prints line that are not matched, instead of matche
                             |
  grep regex are enclosed in |
  ''                         | . - matches any one character (except a newline)
                             | * - matches any number of repeats of the preceeding character
                             | + - matches one repeat of preceeding character
                             | ? - matches zero or one time of preceeding character
                             | [] - used to narrow our substitution ot a certain
                             |      character set
                             |      [ao] - maches a or  o
                             |      [a-z] - maches any character between a - z
                             |
                             | {n} - exactly n times
                             |
  Line anchors               | ^ - used to match a pattern at the beginning of
                             |     a line
                             | $ = used to match a pattern at the end of  a
                             |     line
                             |
  Limit to words             | -w
                             |
Character classes            |
  `[[:alnum:`]]                | Matches lowercase and uppercase leters or digents  [a-z A-Z 0-9]
                             |
  `[[:alpha:`]]                | matches lowercase and uppercase letters            [a-z A-Z]
                             |
  `[[:digit:`]]                | Matches digits                                     [0-9]
                             |
  `[[:lower:`]]                | Matches lowercase letters                          [a-z]
  `[[:upper:`]]                | Matches uppercase letters                          [A-Z]
  `[[:blank:`]]                | Matches spaces and tabls                           [\t]
--------------------------------------------------------------------------------
== Regular expressions in Python ==
--------------------------------------------------------------------------------
  import re                  | to use regex, you must first import the library
                             |
  re.compile(r'<pattern>')   | the compile method is used to create a regex object
  -> regex Object (reObject) | (a raw string must be used)
                             |
                             | groupings with parentheses can be used (thus the
                             | need for raw strings).
                             |
  reObject.serch('<str>')    | the regex object's search method will return 'none'
  -> matchObject             | if no match is found, or a 'match' object if a
                             | a pattern is found
                             |
  matchObject.group()        | if no groupings are used, the group() the matchObject,
                             | returned by the search method from a regexObject
                             | will return the actual text of search.
                             | otherwise, you can use you can return he specific
                             | individual groups with .group(1) ....
                             |
  matchObject.group(0)       | .group(0) will return the entire mached search
  matchObject.groups()       | .groups() will return all the groups as a tuple
                             |
                             |
  characters with special    | . ^ $ * + ? { } \ | ( )
  meaning (must be escaped   |
  to be part of the search   |
  string)                    |
                             |
  matchObject.findall()      | * using a "|" can be used to match multiple expressions
                             | * by default, group() will just return the first match
                             |   use .findall() will:
                             |     * return a list of strings if there are no groups
                             |     * return a list of tuples if there are groups
                             |
  re.compile('.*',re.DOTALL) | By default, '.*' will return everything EXCEPT newline
                             | characters... re.DOTALL will return everythin INCLUDING
                             | newline characters
                             |
  re.compile('.*',           | this will make the serch CASE INSENSITIVE
    re.IGNORECASE)           |
                             |
  reObject.sub(sub, 'string')| with the sub() method of the regexObject, the "sub"
                             | attribute replace all maches in the given string
                             |
  reOb.sub(patt, re.VERBOSE) | Verbose allows the pattern to ignore white space
                             | and comments.... for example:
                             | --------------------------------------------------
                             | phoneReex = recompile(r'''(
                             |     (\d{3}|\d{d}\))?              # area code
                             |     (\s|-|\.)?                    # separator
                             |     \d{3}                         # first 3 digits
                             |     (\s|-|\.)?                    # separator
                             |     \d{4}                         # last 4 digits
                             |     (\s*(ext|x|ext.)\s*\d{2,5})?  # extension
                             |     )''', re.VERBOSE)
                             | --------------------------------------------------
  re.IGNORECASE, DOTALL      |
     VERBOSE and "|"         | these arguments can be used together if seperated
                             | by '|'
                             | re.compile('foo', re.IGNORECASE | re.DOTALL | re.VERBOSE)

