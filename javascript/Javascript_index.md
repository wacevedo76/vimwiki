# JavaScript Index
* [Document Object Model](DOM)

## Quick Notes

### Object Descructuring
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
* Since the "body" of the arrow function is the return value, then the body can only be one line, but no return statement is needed.
