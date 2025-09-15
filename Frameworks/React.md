# React JS

## Quick Notes
### Create plain React Project
```
npx create-react-app{@version_number} <app name
example:
  npx create-react-app@5 <app name>
```

### Create React Project via vite:
```
npm create vite@latest my-react-app -- --template react
```

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

## Starting a React Project
Old way:
`npx create-react-app@5 (name of app)`

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

## Handling Events the React way
Event handlers in React are written inline, in other words, they are placed on 
the tag that you'd like the trigger an event handler:
```jsx
<button 
  onClick={() => alert("this happens when the buttong is clicked")}
  onMouseEnter={() => alert("This happens when the mouse goes over this element")}
 >This Button</button>
```

The syntax for the Event handler is as such:
```
<tag eventHandlerKeyWork={() => function()} />
     (Event Handler)      (callback function)
```

Oftentimes, the call back function is not defined inline, but defined in the component:
````
  function handlePrevious() {
    alert("Previous");
  }

    ...


<button onClick={handlePrevious} />
<button onClick={() => handlePrevious()} />  // <- The same as above
````
* Notice that the `handlePrevious` does not have the `()`, as since this is not 
  a function call, but a callback.

## State
### What is State in React?
This section will cover:
* What State is, and why is it needed?
* How to use state in Practce:
  * `useState`
  * `UseReducer`
  * Context API
* Thinking about State:
  * When to use State.
  * Where to place state.
  * Types of state

### What is State
* Data that a component **can hold over time**, necessary for information that 
  it needs to **remember** throughout the app's life cycle
* **"Component's memory"** 
* **"State variable" / "piece of state"**: a single variable in a component (component state)
* Updating **component state* triggers React to **re-render the component**.
* Each component renders a **view**, all view comprise of the User Iterface (UI)

State Allows Developers to:
1. Update the component's view (by re-rendering it)
2. Persist local variables between renders

### How to use State
```jsx
import { useState } from "react";

export default function App() {
  const [defaultValue, setDefaultValue] = useState(1);
        // default value setter function
}
```

* State variables must be defined in the global scope of the component; They can 
  not be set within a statement or a conditional.

* When using the setter function of a state variable, it is good practice to 
  use a **callback function** when changing the value of the state variable.
```jsx
import { useState } from "react";

export default function App() {
  const [defaultValue, setDefaultValue]= useState(1);
        // default value setter function
  
  setDefaultValue((s) => s + 1);
}
```

### Notes about state and Some best practices
* Each component has and **manages its own state**, no matter how many times we 
  render the same component, in other words, when multiple instances of the same 
  component are displayed, a state change in one state will not affect the other
  instances of the component.
* With State, we view UI as a **reflection of data changing over time**

### Practical Guideline about State:
* Use a state variable for any data that the component should keep track of ("remember") over time. **This is data that will change at some point**. In Vanilla JS, that's a `let`, `var` variable, or an `[]`, or `()`
* Whenever you want something in the component to by **dynamic**, create a piece of state related to that "thing", and update the state when the "thing" should be changed.
    * Example: A modal window can be opened or closed. So we create a state
      variable `isOpen` that tracks whether the modal is open or not. On 
      `isOpen = true` we display the window, on `isOpen = false` we hide it
* If you want to change the way a component looks, or the way it displays data,
  **update its State**. This usually happens in an **event handler** function.
* When building a component, imagine its view as a **reflection of state 
  changing over time**.
* For data that should not trigger component re-renders, **dont' use state**. User a regular variable instead. This is a common **beginner mistake**.

### State Vs. Props
#### State
* Internal Data; Data which is owned by the component
* Data which can be considered a Component's memory
* Data which can be updated by the component itself
* Updating state causes the component to re-render
* State is used to make components interactive

#### Props
* External data; Data which is owned by the parent component
* Data which is similar to function parameters
* Data defined in Props is Read-only
* Receiving new props causes components to re-render. Usually when the parent's state has been updated.
* Used by parent components to configure child component "settings"

## Section 7: Thinking in React: State Management
### Section Overview
* Thinking in React
* State Management
* Derived State
* Lifting up state

#### What is "Thinking in React"
Thinking in React:
* React Mindset
* Thinking about components, state, data flow, effects, etc.
* Thinking in **state transitions**, not element mutations

#### The "Thinking in React" Produces
1. Break the desired UI into **components** and establish the **component tree**
2. Build a **static** version in React (without state)
3. Thinking about **state**:          ----------------
  * When to use state                            |
  * Types of state: local vs. global             |
  * Where to place each piece of state        State Management
4. Establish **dataf flow**:                         |
  * One-way data flow                            |
  * Child-to-parent communication                |
  * Accessing global state        ----------------

#### When you know how to "Think in React", you will be able to answer:
* How to break up a UI design into components?
* How to make some components reusable?
* How to assemble UI from reusable components?
* What pieces of state do I need for interactivity?
* Where to place state? (What component should "own" each piece of state?)
* What types of state can or should I use?
* How to make data flow through the app?

### Fundamentals of State Managment
#### Types of State: Local vs Global State
Local State:
* State needed only by one or few components
* State that is defined in a component and only that component and child components have access to it (by prassing via props)

Global State:
* State that many components might need
* Shared state that is accessible to every component in the entire application
* Some tools which can provide global state are:
  * The Context API
  * Redux

## Misc Code
This segment of JSX Produces 20 option tags.

Questions:
* The second attribute for the `Array.from` method contains `(_, i)`, what are purpose of thess two attributes?
```
{Array.from({ length: 20 }, (_, i) => i + 1).map(num => (
  <option value={num} key={num}>
    {num}
  </option>
}
```
