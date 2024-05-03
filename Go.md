# Go(lang) Notes 
## History and features. 

  It is a compiled, statically typesd language in the tradition of Algo
  and C, with garbage collection, limited structual typing, memory 
  safty features and CSP-syle concurrent programming features added.  

  The compiler & other language tools originally developed by Google
  are all free and open source.  

  Go takes a stong position on features that can lead to confusion and 
  bugs. It omits OOP idiom such as inheritance and polymorphism, in 
  favor of composition and simple interfaces. It downplays exception 
  handling in favor of explicit erros in return values. There is exactly
  one correct way to lay out Go code, enfoced by the gofmt tool.  

  Go is also a great language for writing concurrent programs: programs
  with many independently running parts. An obvious example is a
  webserver: Every request runs separately, but requests often need to
  resources suce as sessions, caches, or notification queues. This 
  means skilled Go programmers need to deal with concurrent access to 
  those resources.  

  While the Go language has an excellent set of low-level features for
  handling concurrency, using them directly can become complicated. In
  many cases, a hadful of reusable abstractions over theose low-level 
  mechanisms make like much easier.  

  Programs are constructed using packages, for efficient management of
  dependencies. Go programming implementations use a traditional compile
  and link model to generate executable binaries.  

  Features excluded Intentionally
    * Support for type inheritance
    * Support for method or operator overloading
    * support for circular dependencies among packages
    * support for pointer arithmetic
    * Support for assertions
    * Support for generic programming

## Random notes
  Golang's documentation can be found at https://pkg.go.dev/std

  Go is not and object oriented language.
  Instead of object you make custom types and assign
  functions with recievers that git custom types specific 
  functionality, in essence, functions that belong to instances 
  of custom types


## Go CLI
```
  go build                   | Compiles a bunch of go source code files
                             |
  go run                     | Compiles and executes one or two files
                             |
  go fmt                     | Formats all the code in each file in the 
                             | current directory
                             |
  go install                 | Compiles and "installs" a package.
                             |
  go get                     | Downloads the raw source code of somone 
                             | elses package
                             |
  go test                    | Runs any tests associated with the current
                             | project
```

## Go Packages
```
  There are two types of     | Exacutable (package)
  packages in any given go   | - Generates a file that we can run
  project                    |
                             | Reusable (package)
                             | - Code used as 'helpers'. good place to put
                             |   reusable logic (code dependencise/libraries).
```
```

## Common packages
  io/ioutils                 |
```
(Go Packages) :Summary.  

  A package declaration can be included at the top of any Golang source
  code. Doing so will define the type of packages the source code in 
  questions compiles as. Unless the package name given to the the soure
  code is "Main", the package will compile as a Reusable package.  NOTE:
  if the package "main" is used, indicating that the source code is meant
  to be used to produce and executable file, a "main" function must exist
  in the source code.  
  
  ASSUMTIONS: The "main" package is an entry point for the project

## Go Basic Types
```
  bool                       |
  string                     |
  int                        |
  float64                    |
                             |
  Variable declaration       | var card string = "Ace of Spades"
  Var declareation shortcut  | cart := "Ace of spades"  <-- only used in var declaration
    The ":=" operator allows |
    the Go compiler to       |
    infer its type based     |
    on the value supplied in |
    the var declaration      |
```

## Function Return types
```
  When defining a function   | func newCard() string {    <-- define type after parameters
  you must define the type   |
  the function returns       |
```

## Arrays
```
  There are two types of     |
  arrays:                    |
    * Array                  | Fixed length list of things
    * Slice                  | An array that can grow or shrink
                             |
  Arrays and Slices must be  |
  defined with a data type   |
  (they can not hold mixed   |
    data types)              |
                             |
  Define:                    |
    * Slice                  | cards := []string{'2 spades', newCard(), newCard()}
                             |     (notice that "string" is sigular)
                             |
      Append to slice        | cards = append(cards, "6 Spades")
                             |         append( -slice/array- , -object being added- )
                             |      (NOTE: the append does not changes the original object
                             |       but returns a new copy of the object with modifications.
                             |       No side effect, just return value.)
                             |
  Iterating over slices      | for i(ndex), card := range cards {
                             |   fmt.Println(card)
                             | }
                             |
  Throw away variables       | for i, card :- range cards {
  Iterating over slices      | for _, card :- range cards { <-- throw away variable
  In a loop, or anywhere     |
  a variable is declared     |
  and immediately thrown     |
  and not used in the code   |
  away, you can usd "_"      | NOTE: the reason ':=' is used is because through every 
                             |       iteration of the loop, the previous value is thrown
                             |       away, requiring a new varialble to be declared.
```

## Types
```
  Type declaration           | type (name) (derived type)
                             | type deck []string
   To make a customer type   |
   The new type "inherits"   |
   all the functionality of  |
   the slice of string       |
```

## Receiver functions
```
  reciever function declar.  | func (d deck) print() {
                             | func ( -argument representing given "type"- -given type-) -name of function()- {
                             |   (the first parenthisis aregument is
                             |   makes this a receiver function)
                             |   * func          thisFunction() string {  <-- regular function which returns string
                             |   * func (t type) thisFucntion() string {  <-- receiver function
                             |
  Any variable with the      |
  defined type will recieve  | in the Receiver function declaration, d 
  acces to the definded      | represents the argument which can be 
  "print" function           | used and manipulated within the code
                             | block
  Receiver functions set up  |
  "methods" on custom        | this "argument" is called d because 
  variable / types that are  | , by convention, the arguement is 
  created                    | usually the first or first two letters
                             | of the defined / passed in type (deck
                             | in this situation)
```

## Slice Range syntax
```
  Return a "slice" of a      | slice[ -startIndexIncluding- : -upToNotIncluding ]
  slice                      |
                             |
  If starting from the first | slice[: -upToNotIncluding-]
  leave the first index ref  |
  off                        |
                             |
  If starting from the last  | slice[-startIndexIncluding-:]
  leave the last index ref   | 
  off                        |
```

## Return/assign Multiple values
```
  After the receiver/param   | func deal(d deck, handSize in) (deck, deck) {
  definition, this function  |   return d[:handSize], d[handSize:]
  defines, in parenthisis,   | }
  that the deck.deal function|
  will return two items      |
                             |
  Here, multiple assignment  | hand, remainingDeck := deal(cards, 5)
  works because the function |
  returns multipe values     |
```

## Type Conversion
```
  converting a slice of      | []string(-slice of strings-) --> from the "strings" package
  strings into a single      | []byte("Hi there!")
  string                     | 
```
  
  
  
  

