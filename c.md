--------------------------------------------------------------------------------
= The C programming language - Notes =
  - Notes collected from "The C Programming Language, 2nd Edition"
      - Brian W. Kernighan and Dennis M. Ritchie
--------------------------------------------------------------------------------
== CH 01. A Tutorial Introduction ==
  printf interpolation types | %d     Decimal
                             | %f     floating point
                             | %o     octal
                             | %x     hexadecimal
                             | %c     character
                             | %s     Character sting
                             | %%     for % itself
                             |
  placing a number between   | %6f    print as a floating point, at least 6
  the percent sign and the   |        characters wide
  interpolated type defines  | %6.1f  Same as above, but 1 character after
  its formatting option      |        the decimal point
                             |
  The printf function will   | printf("%d %6.1f\n", fahr, (5.0/9.0)*(fahr-32));
  perform any statement      |            (interpolated   (statement for
  operation and supply the   |              type)           evaluation)
  value interpolated into    |
  the string, assuming the   |
  correct interpolated type  |
  is supplied                |
                             |
  GENERAL RULE:
  In any context where it is permissible to use the value of a variable of 
  some type, you can use a more complicated expression of that type.

  1.4 Symbolic constants     | #define <name> <replacement text>
    (1.4 - what is meant by  |
    magic numbers?)          |
                             |
    any occurrence of a      |
    defined symbolic constant|
    , not in quotes and not  |
    part of another name will|
    be replaced  by the      |
    corresponding replacement|
    text                     |
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
