# The Dart Programming Language

## Notes from Dart Crash Course 

### Dart Crash Course #1 - What is Dart?
* Dart is a language used to make *multi-platform* applications

  >**Dart Code** ---compiled-----> Machine code or Javascript for the web
* Dart is a **statically typed language** 

#### Course outline
* Dart basics - strings, integers, booleans, etc
* Functions, Lists, sets, Maps & Control Flow
* Classes & Generics
* Futures & HTTP Requests

### Dart Crash Course #2 - Dart Basics
* The Dart entry point is `void main() {}`
* C style for loop - `for (var i = 0; i < 4; i++){}`
* Statements **must** end with a semi-colon

##### Variables
* The `var` keyword is used the initialize a variable *without* an initial type. Once set, the value type can not be changed .
* The `final` keyword is used to set a **constant** without an initial type and is used to create ***runtime constants*** variable.
* The `const` keyword is used to set a **constant** with or without an initial type, and sets an ***compile time***  variable.
* **String iterpolation** is used by appending a dollar sign to a previously set variable:  
  ```
  var name = 'william`;
  print("My first name is $name")
  ```

##### Comments
* Single line comment: `//`
* Multiline comment: `/*     */`

### Dart Crash Course #3 - Type Annotations
* Instead of the `var` keywork, type annotations can be used
* If type annotations are used to initialize a variable, the value **must** be set, unless explicitly set to a **null** value.
* So far, the course teaches 4 basic types: `String` (uppercase S), `int`, `double` (for floating point values), and `bool`
  ```
  String name = 'William';
  int age = 47;
  double averageTax = 0.33;
  bool isOpen = false
  ```
* If you do not want to initialize the variable with a Type annotation, the value **must** initially be set to **null** by simply suffixing a question mark '**?**' to the end of the type annotation:
  ```
  String? name;
  double? average;
  ```

##### Setting constants with type annotations
* You can initialize constants with type annotations by simply preceding the constant type before the type annotation:
  ```
  const String name = 'William';   <-- results in a constant string with the value 'william'
  final double averageTax = 0.33;  <-- results in a constant double with the value '0.33'
  final String? queryResult;       <-- results in a constant unset string
  ```

### Dart Crash Course #4 - Functions
#### Function Creating
Functions are created similarly to variables, however a function name must end with two parenthesis which will contain 0 or more parameters which the function takes
  `testfunc() {}`

#### Function Type Anotations
Function parameters can take type annotations by adding the type before the parameter:  
  `testfunc(String name, int age} {}`

#### Function return type
You can define the function's return type by preceeing the function name with the desired return type:  
  `String testfunc(String name, int age} {}`

#### Positional parameters vs Named parameters:
Parameters which are not named are ***positional paramaters***, meaning that the order in which a function receives its arguments must match the order in which the parameters were defined.  
***Named parametes*** are defined much like you would define a **map**:
  * They must be enclosed within a set of curly braces **{}**

  > **Optional Parameters**: The Type Annotation of parameters must be suffixed with a question mark **?**
  > **Required Paramaters**: The Type Annotation of parameters must be preceded with the "**required**" keyword
  > **Named Arguments**: Named Arguments are defined similarly to key-value pairs:  
    `testfunc(name: "william", age: 22)`

### Dart Crash Course #5 - Lists and Sets
#### Lists
Lists are defined similalry to other programming languages similar to dart (Python, Ruby):  
  `var scores = [50, 74, 20]` --> in this instance, the list can contain multiple types
  
###### Explicitly set List value types
When setting the type of data types a list will accept, you used the **List** keyword and enclose the type withing angled brackets **<>**:  
  `List<int> scores = [50, 74, 20]` --> adding any other type except integers in the case will throw an error.

###### Some List methods
 >score.add()  
  score.remove()  
  score. removeLast()  
  score.shuffle()  
  score.indexOf()  

#### Sets
**Sets** are defined by adding values within a set of curly braces
  `var names = {'Mario', 'Harold'}`

##### Type annotations for Set vaules
Like with lists, Type annotations for Sets are defined by using the **Set** keyword and enclosing the type within angled brackets **<>**
  `Set<String> names = {'Mario', 'Harold'}`

##### Some Set methods
 >names.add("bowser")
  names.remove("mario")

[^1]:(https://www.youtube.com/watch?v=QGqMJzywasg&list=PL4cUxeGkcC9iVGY3ppchN9kIauln8IiEh)
