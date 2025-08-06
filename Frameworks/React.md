# React JS

## Key Concepts
* React is **Declarative** not **Imperative**:
  * The DOM is interacted with and manipulated through React using React's Virtual DOM.

* Component Architecture
  * You can think of components like reusable blocks which can be using multiple times within a page, or withing a site.

* One Way Data Flow
  * Once State changes, the change is reflected in the site (interface), which simplifies where bugs may exist.

* UI Library
  * Essentially, all that react is is a UI library. It does not make any assumptions of the technology stack with is being used, making the app usable in various other environments.

## The job of a React Developer
1. Decide on Components.
2. Decide the State and where it lives.
3. What changes when state changes.

## Working with Components, Props, and JSX
### What is a Component
Simply, a Component is an object that appears similar to HTML / XML, Written in a combination of JSX Markup and Javascript, with is transpiled from JavaScript into code which the Browser can use. A component can contain:
* Data
* Logic
* Appearance

### Rending the Root Component and Strict Mode
```
import React from 'react';
import ReactDOM from "react-dom/client";

function App() {
  return <h1>Hello React!</h1>
}


const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(<App />); 
```

### Rending the Root in Strict Mode
```
const root = ReactDOM.createRoot(
  <React.StrictMode>
    <App />
  </React.StrictMode>
)
```

### JSX 
* JSX is a declarative syntax that is used to describe the appearance and behavior of a component.
* Each component must return only one block of JSX, which React will render it on the UI
* While JSX resesembles HTLM, it is an extension of JavaScript that allows the embeding of JavaScript, CSS and other React Components into HTML
* JSX is transpiled / converted into HTML using Babel.

### Imperative vs Declarative
* Imperative code tells the Browser HOW something is one
* A Declarative approach abstracts the complexity away, meaning you can simply describe how the UI should appear based on the current data the component(s) contain.

### Props
* Props (properties) are used to pass data from **parent components** to **child components** (down the component tree)
* Essential too to configure and customize components (like function parameters)
* With props, parent components control how child components look and work
* Anything can be passes as props: single values, arrays, objects, function, even other components
* Props are **immutable**

### Destructuring Props
When creating a component:
```jsx
function NewComponent(props) {
  return (
   <p>
    This is {props.propNam01} and {props.propName02}.
   </p>
  )
}
```
Instead of passing `props` to the function, you can destructure the attributtes of props:
```jsx
function NewComponent({ propName01, propName02 }) {
  return (
   <p>
    This is {propNam01} and {propName02}.
   </p>
  )
...
}
```

### Rules of JSX
* JSX works essentially like HTML, but we can enter "JavaScript mode" by using `{}` (for text and attributes)
* We can place **JavaScript expressions** inside `{}`, Examples: reference variables, create arrays or objects, `[].map()`, ternary operator
* Statements are **not allowed** (if/else, for, switch)
* JSX produces **a JavaScript expression**:
  These two expressions are essentially equivalent:
  * `const el = <h1>Hello React!</h1>;`
  * `const el = React.createElement("h1", null, "Hello React!");`
    1. We can place other pieces of JSX inside `{}`
    2. We can write JSX **anywhere** inside (in if/else, assign to variables, pass it into functions)
* A piece of JSX can only have **one root element**. If you need more, use `<React.Gragment>` (or the short `<?`)

### Difference between JSX and HTML
* `className` instead of HTML's `class`
* `htmlFor` instead of HTML's `for`
* Every tag needs to be closed. If the tag does not come in a pair, then it must self close: `<br />`
* All even handlers and other properties need to be **camelCased**. Examples: `onClick` or `onMouseOver`
* Exceptions: `aria-*` and `data-*` are written with dashes like in HTML
* CSS inline styles are written light this: `{{<style>}}` (to reference a variable, and then an object)
* CSS property names are als camelCased
* Comment need to be in `{}` (because they are JS)

### React Fragments
Since React components can only return one element, the following component will throw an error:
```jsx
function TestComponent() {
  return (
    <p>
      This is a paragraph
    </p>
    <p>
      This is the second paragraph
    </p>
  )
}
```
It will throw an error because it is trying to return two objects, to resolve this issue, you can 
wrap the code segment in a React Fragment, which consists of opening and closing HTML tags (<>, </>):
```jsx
function TestComponent() {
  return (
    <>
      <p>
        This is a paragraph
      </p>
      <p>
        This is the second paragraph
      </p>
    </>
  )
}
```
In the case of lists, which need unique keys:
```jsx
function TestComponent() {
  return (
    <React.Fragment key="anything">
      <p>
        This is a paragraph
      </p>
      <p>
        This is the second paragraph
      </p>
    </React.Fragment>
  )
}
```

### Summary
* Components are the building blocks for any interface in a React App
* Each Component is a self contained piece of the user interface which contains its own data, JavaScript logic and appearance.
* The appearance of the component is made up of a declarative syntax called JSX, which is what is returned from the component. It is this what describes what is seen in the user interface.
* JSX can display: HTML, CSS, and JavaScript code within `{}`
* In order to share data between component, a parent component can share data to child components through `props`
* You can render multiple components using the JavaScript `.map()` method.
* Components can be conditionally rendered using JavaScript tools: `&&`, `?` and multiple `return`
