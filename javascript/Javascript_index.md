# JavaScript Index
* [Document Object Model](DOM)

## Quick Notes

### Object Destructuring
Object example:
* We will assign an object to the variable **"book"**:
```JavaScript
const book = {
    id: 1,
    title: "The Lord of the Rings",
    publicationDate: "1954-07-29",
    author: "J. R. R. Tolkien",
    genres: [
      "fantasy",
      "high-fantasy",
      "adventure",
      "fiction",
      "novels",
      "literature",
    ],
    hasMovieAdaptation: true,
    pages: 1216,
    translations: {
      spanish: "El señor de los anillos",
      chinese: "魔戒",
      french: "Le Seigneur des anneaux",
    },
    reviews: {
      goodreads: {
        rating: 4.52,
        ratingsCount: 630994,
        reviewsCount: 13417,
      },
      librarything: {
        rating: 4.53,
        ratingsCount: 47166,
        reviewsCount: 452,
      },
    },
  }
```

#### Destructuring Objects:
`const {id, title} = book:`
* What this does is assigns a variable "id" the value of "book.id" and "title" to "book.title"

`const {id: bookId, title: bookTitle} = book`
* When destructuring Name / Value pairs, you must use `{}` curly braces.
* This does the same as above, but gives specific variable names for the values which are destructured from "book" (bookID, bookTitle).

#### Destructuring Lists
`const [firstGenre, secondGenre] = book.genres;`
* When destructuring Lists, you must use "[]" angle brackets.
* While the variables that will hold the values from a list object can be any name you choose, the order of the variables will be assigned the values of the order in which the list holds them.

#### Rest Operator (for Lists)
`const [firstGenre, secondGenre, ...otherGenres] = book.genres;`
* The **"Rest"** operator does as its name implies, it assigns any other values which have not been named when destructuring a list the to last defined variable, **"other Genres"** in this case.
* The **Rest** operator is simpley three dots followed by the name you give to hold the other values (, ...otherGenres)
* The **Rest** operator must be the last variable defined.

#### Spread Operator for Lists
`const NewGenres = [...book.genres, "epic Fantasy"]`
* The **"Spread"** operator appears identical to the **Rest** operator, but acts differently in that when defining and new list, you can simply add the values of a predefined list with the **Spread** operating.
* The **Spread** operating will simply add the key / value pairs contained within the predefined list as opposed to embedding a list object within the list you are creating.

#### Spread Operator for Objects
```
const updatedBook = {
  ...book,
  moviePublicationDate: "2001-12-19",
  pages: 1218,  // redefines the pages value predefined within "book"
}
```
* In this case, the Spread operator adds all of the keys / values contained in the "book" object into the newly created "updatedBook" variable.
* You can change the value of any predefined key / value pairs while creating a new object by redefining the value of a predefined key in the object which has been destructured by redefining it after "Srpeading" the object. The last value overwrites any previous values.

### Template Literals
**Template Literals** are an ES6 / JavaScript feature which allows us to interpolate JavaScript variables or valid expressions within JavaScript strings.

```
const bookName = `The tile of the book is ${book.title}`
````
* To create a **Template Literal**, you wrap the string in backtics instead of commas.
* The interpolation happens when you wrap the variable or expression between a dollar sign and curly brackes ( ${variable or expression} )

### Ternaries
Here is the structure of a Ternary statement in JavaScript:  
```JavaScript
(logical expression) ? "True return value" : "Fales return value"
```
* The first expression must be a booleen expression.
* The return values can be any valid data type

### Arrow Functions
Arrow functions are an ES6 feature for writing quick and short one line functions (similar to Lambda Functions). The basic syntax for an Arrow Function is as follows:
```
const functionExpression = (paramaters) => return value (which can use defined parameters, if any);
```
* The parenthesis are only needed if two or more parameters are being called
* If the function only takes up one line, then a `return` statement is not needed, otherwise, you must use curly braces and a `return` keyword.

### Short-Circuiting and Logical Operators: `&&`, `||`, `??`
Some logical operators operate on short-circuit rules, meaning that one value will automatically be returned when a condition is met.

#### `&&` operator
```
(true && "some String");
```
* With the `&&` operator, if the first expression is **true**, it will automatically return result of the second expression
```
(false && "some String");
```
* The same is true with a false statement, if the first expression returns false, the second experssion will **not** be evaluated and the first value will be returned.
* This behavior will also work with "truthy" and "falsey" values.

#### `||` operator
Similar Short-Circuiting behavior applies to the `||` (or) operator.
* It will return the first value, if true, and not evaluate the second value.
* It will return the second value if the first is false, **which may lead to unexpected Behavior**

#### `??` operator (Nullish coalescing Operator)
* It works similarly to the `||` operator but does short-circuit for falsy values, and will only execute the right value with `null` or `undefined`

### Optional Chaining
In JavaScript, Optional Chaining (`?.`) is a safe and concise way to access nested properties of an object
without having to explicitly validate that each reference in the chain is not null or undefined. In other words, if a nested property os an object does not exist, it will return an `undefined` instead of throwing an error.
```
const street = user?.details?.address?.street;
```
* If any value within the object chain, including user, does not exist, the value of street will be `undefined`

* This can be used in conjunction with `??` the Nullish coalescing operator:
```
const books_read = data.books.booksReadTotalCount? ?? "No data Available"
```
* if `||` or was used and the value of `data.books.booksReadTotalCount` returned `0`, it would have used "no data Available" instead of returning the `0`.

### Functional Array Methods
#### The Array Map Method
```
const x = [1, 2, 3, 4, 5].map((el) => el * 2); // -> "el" is a temporary variable 
                                               that represents a single element 
                                               in the array, which can be used 
                                               to perform an operation

x;   // -> [ 2, 4, 6, 8, 10 ]
```
* The Map array function returns the performs an operation on each element in the array, and returns an array with the newly modified elements

#### The Array Filter Method
The Array Filter Method used to filter elements of an object based on criteria defined in a callback function you define as the Filter's parameter.
```
const longBooks = books.filter((book) => book.pages > 500);
```
* 

