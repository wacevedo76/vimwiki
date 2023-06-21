--------------------------------------------------------------------------------
Linux Admin Bootcamp
--------------------------------------------------------------------------------
= Wildcards =
== Match 0 or more characters ==
                             | *
                             | *.txt    - all text ending with .txt
                             | a*       - all text begining with a
                             | a*.txt   - all text begining with a
                             |            and ending with .txt
== Match exactly on character ==
                             | ?
                             | ?.txt    - match all single letter ending in .txt
                             |
== Character class ==
                             | []
  matches any of the chara-  | [aeiou]  - matches one character a or e or i or o
  ters included between the  | can[nt]* - can, cat, candy, catch
  brackets. Matches exactly  |
  one characters             |
                             |
  to excule characerts       | [!]
                             | [!aeiou]* - matches all words NOT begining with a vowel
== Character Ranges ==
  Use two character seperated| [a-g]*    - matches all files that begin with an a though g
  by hyphen                  | [3-6]*    - matches all files that start with 3, 4, 5, 6
                             |
== Named Character Classes ==
                             |  `[[:alpha:]]`
                             |  `[[:alnum:]]`
                             |  `[[:digit:]]`
                             |  `[[:lower:]]`
                             |  `[[:space:]]`
                             |  `[[:upper:]]`
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

