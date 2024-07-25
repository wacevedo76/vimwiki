# The C programming language - Notes
  - Notes collected from "The C Programming Language, 2nd Edition"
    - Brian W. Kernighan and Dennis M. Ritchie
### **Types**
  - `char` - holds character values
  - `int` - holds whole numbers
  - `float` - holds floating-point values of single precision
  - `double` - holds floating-point values of double precision
#### **Character Type**
  - to declare a character variable:
    - `char mychar`  
      `mychar = 'a'`;  
  - The declaration and assignment can be done on a single line
    - `char maychar = 'a';`
  - To print out the characte variable as an actual character:
    - `printf(`**`%format_specifier`**, `variable_name)`  
      
    ##### **`printf`** interpolation (format) types
    - `%f`     floating point
    - `%o`     octal
    - `%x`     hexadecimal
    - `%c`     character
    - `%s`     character sting
    - `%%`      for % itself
#### **Integer Type**
  - To declare and assign an integer variable
    - `int x = 123;`
  - The differnt integer constants that can be assigned to `int` are:

| Integer type                  | value                                                  |
| -------------------------     | --------------------                                   |
| **Decimal integer constants** | Negative or positive                                   |
| **Octal** Constants           | begins with a `0` and can contain `0` to `7`           |
| **Hexadecimal** Constants     | Begins with an `0x` and followed by `0 - 9` and `A -F` |
#### **Floating-Point Types**
  - There are three types for representing floating-point numbers:
    - `float`
    - `double`
    - `long double`
  - To declare and assign a float variable:  
    `float myfloat = 123.456f;`

## **Operators**
### Arithmetic Operators
| Operator | Purpose        |
| ------   | -------------- |
| **+**    | addition       |
| **-**    | subtraction    |
| **\***   | multiplication |
| **/**    | division       |
| **%**    | modulus        |

### Compound assingment operators  
| Compound assignment Operators | Purpose             |
| ----------------------------- | ------------------- |
| `+=`                          | add and assign      |
| `-=`                          | subtract and assign |
| `*=`                          | multiply and assign |
| `/=`                          | divide and assign   |
| `%=`                          | modulus and assign  |
---------------------------------------------------------------------------------
**Formatting required below this line**  
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
