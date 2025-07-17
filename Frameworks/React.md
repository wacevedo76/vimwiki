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

### The job of a React Developer
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
