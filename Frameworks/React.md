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

### Deriving State
* **Derived state**: state ths is computed from an existing piece of state or from props

### Derived state is useful because:
* It minimizes the amount of States you have to keep within a component, minimizing state variables having to be kept in sync
* Minimizes the number of times a component is re-rendered
**example**:

```
const [cart, setCart] = useState(
  [
    { name: "Javascript Course", price: 15.99},
    { name: "Node.js Bootcamp", price: 14.99},
  ]
);

const [numItems, setNumItems] = useState(2);                       // Values can be derived, making this state variable necessary
const [totalPrice, setTotalPrice] = useState(30.98);               // Values can be derived, making this state variable necessary


---- Using derived State

const [cart, setCart] = useState(
  [
    { name: "Javascript Course", price: 15.99},
    { name: "Node.js Bootcamp", price: 14.99},
  ]
);

const numItems = cart.length;                                     //
const totalPrice =
  cart.reduce((acc, cur) => acc + cur.price)

```
**This is useful because**:
* You use regular variables
* A state object is used as a single source of truth from the related data
* It works because re-rendering component will automatically re-calculate derived state

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

## How to Split a UI Into Components
### Component size matter
#### When components are too small:
* We end up with 100x of mini-components
* Confusing codebase
* Too **Abstracted**

#### When Components ar too big
* Components have too many responsibilities
* Might need too many props
* Hard to reuse
* Complex cod, hard to understand

Gemerally, component size is finding the right balance between too specific and too broad.

### The 4 criteria for splitting a UI into components:
* Logical separation of content / layout
    - Does the component contain pieces of content or layout that **don't belong together**?
* Reusability
    - Is it possible to reused part of the component?
    - Do you want or need to reuse it?
* Responsibilities / Complexity
    - Is sthe component doing too many different things?
    - Does the component rely on too many props?
    - Does the component have too many pieces of state and / or effects?
    - Is the code, including the JSX, too complex / confusing?
* Personal Coding Style
    - Do you prefer smaller functions /components

### Some More General Guideline
* 💰 Be aware that creating a new component creats a new abstraction. abstractions have a cost, because more abstractions require more mental energy to switch back and forth between components. So try not to create new components too early.
* 🏷️ Name a component according to **what it does** or what it displays**. Don't be afraid of using long component neames
* Never declare a new component **inside another component**!
* **Co-locate related components inside the same file**. Don't separate components into different files too early.
* It's completely normal that an app has components of **many different sizes**, including very small and huge ones.

## Component Categories
Most of your components will naturally fall into one of three categories:
* Stateless /presentational components
    * No state
    * Can receive props and simply present received data or other content
    * Usually small and reusable
* Stateful Components
    * Have state
    * Can still be reusable
* Structural components
    * "Pages", "layouts", or "screens" of the app
    * Result of composition
    * Can be huge and non-reusable (but don't have to).

## Component Composition
### What is Component Composition
Component composition: combining different componets using the **children** prop  (or explicitly defined props)

With Component composition, we can:
1. create highly reusable and flexible components
2. Fix prop drilling (great for layouts)  

## Component vs Instance vs Element
### Component
* A component is what is written to describe a piece of generic UI
* It is a regular JavaScript function that returns React elements (element tree) usually written in JSX.
* It can be considered a "Blueprint" or "Template"

### Component Instance
* Instances are created when a component (function) is used.
* An Instance is the "physical" manifestation of a component
* It's the Instance itself that holds state; Each Instance maintains its own state during its lifecycle.

### React Element
* A React Element is what a Component Instance Returns; it is the result of the function call.
* It contains all the information necessary to create DOM elements
* It is the element that creates and returns the actual DOM element

### How Components are Displayed on the screen

1. Render is Triggered (by updating state somewhere)
2. The Render Phase (React calls component functions and figures out how the DOM should be updated)
3. Commit Phase (React actually writes to the DOM, updateing, inserting and deleting elemens)
4. Browser Paint (at this point the browser takes over and updates the DOM)

**In React, rendering is NOT updateing the DOM or displaying elements on the screen. Rendering only happens internally inside React, it does not produce visual changes.**

#### The two Situations that trigger Renders:
1. **Initial render** of the application
2. **State is updated** in one or more component instances (re-render)

* 👉 The render process is triggered for the **entire application**
* 👉 **In practice**, it looks like React only re-renders the component where the state update happens, but that's not how it **works behind the scenes**.
* 👉 Renders are **not** triggered immediately, but **scheduled** for when the JS engine has some "free time". There is also batching of multiple `setState` calls in event handlers.

## The Mechanics of State in React
### The **Render** Phase
* At the beginning of the of the render phase, React will go through the entire component tree, take all the component instances that triggered a re-render and actually render them, which simply means to call the corresponding component functions that we have written in our code
* This will create updated React elements which altogether make up the so-called virtual DOM.

### The "Virtual DOM" (React Element Tree)
On the initial render, React will take the entire component tree and transform it into one big React element which will basically be a React element tree. This is what is referred to as "The Virtual DOM"
* The Virtual DOM is just a tree of all React elements created from all instance in the component tree.
* It's relatively fast and cheap to make such a tree, even if many iterations of this have to be made, simply because it's just a JavaScript object.
* Whenever there is a State update, this means that React will re-render, which creates a new React element Tree in a new React element tree so in a new Virtual DOM.
* Whenever React renders a component, that render will cause all of its child components to be rendered as well, regardles of whether the props that the child elements hold have changed or not. The changed component and all of its nested components will be re-rendered all the way down the component tree.
* This change place happens in the React "virtual" DOM and not the actual DOM because rerendering items directly to the DOM is expensive.
* The new Virtual DOM that was created after the state update will get reconciled, this reconciliation process happens within the React Reconciler, called FIBER.
* Once reconciliation is complete, then the actual DOM is updated.
* This makes it that only the elements that have changed are re-renderd on the Actual DOM

### The Reconciler: **FIBER**
* Fiber takes the entire React element tree (the Virtual DOM), builds yet another tree which is the Fiber tree.
* The Fiber tree is a special internal tree where for each component instance and DOM element in the app, there is one so-called Fiber, Fibers are **NOT** re-created on every render. The Fiber tree is never destroyed, but instead, it's a mutable data structure, which is simply mutated over and over again for each future reconciliation step.
* This makes Fibers the perfect place for keeping track of things like the current component state, props, side effects, list of hooks and more.

## Rules for render logic
### The two types of logic in React Components
1. Render Logic
    * Code that lives at the **top level** of the component function.
    * Participates in **describing** how the component view appears
    * Executed **Every time** the component renders
2. Event Handler Functions
    * Executed as a **consequence of the event** for which the handler is listening
    * Code that actually **does things**: update state, perform an HTTP request, read an input field, navigate to another page, etc

### **Refresher**: Functional Programming Principles
* **Side effect**: dependency on or modification of any data outside the function scope. "Interaction with the outside world". Examples: mutating external variables, HTTP requests, writing to DOM
    * **Side effects are not bad**

* **Pure function**: a function that has **no** side effects.
    * Does **not** change any variables outside its scope
    * Given the **same input**, a pure function always returns the **same output**

👆**Components must be pure when it comes to render logic**: given the same props (input), a component instance should always return the same JSX (output)

👆**Render logic must produce no side effects**: no interaction with the "outside world" is allowed". So, in render logic:
    * 👆Do NOT perform **newort requests** (API calls)
    * 👆Do NOT start **timers**
    * 👆Do NOT directly **use the DOM API**
    * 👆Do NOT **mutate objects or variables** outside the function scope

* Side effects are allowed (and encouraged) in **event handler functions!** There is also a special hook to **register side effects** (`useEffect`)

## How Events work in React
### **DOM Refresher**: EVent Propagation and Delegation
  * When an event happens (a button click for example), as soon as the event triggers an    **Event Object** is created at the DOM root (`<html>`), then the event object travels down the tree, this is called the "**Capture Phase**", until it reaches the **Target Element**
  * You can choose to handle the event by placing an event handler function on that element.
  * Then the Event Object travles all the way up the DOM tree, this is called the **Bubble Phase**.
  * Since the Event Object traverses the entirle DOM tree, during the **Capturing Phase** and the **Bubbling Phase**. every single event handler in a the parent elements of the Target element will also trigger, so long as it's also listening for the same type of event.
  * This leads to the concept of **Event Delegation**
  
### Event Delegation
* Handling events for multiple elements centrally in **one single parent element**
* It is Better for performance and memory, as it needs only one handler function
    1. Add handler to parent (`.options`)
    2. Check for target element (`e.target`)
    3. if target is one of the of the lements, it handles the event.

## React 3rd-party Library Ecosystem
1. Routing (for SPAs): - React Router - React Location
2. HTTP requests: - `fetch()` - AXIOS
3. Remote State Management: - React Query - SWR - Apollo
4. Global State Managment: - Context API - Redux - Zustand
5. Styling: - CSS Modules - tailwindcss
6. Form Managment: React Hook Form - Formik
7. Animations/transitions: - Motion - react-spring
8. UI Components: - MJ - chakra - Mantine

## Frameworks built on top of React
* NextJS
* Remix
* Gatsby

## Section Summary
* 🧩 **A Component** is a like a blueprint for a piece of UT that will eventually exist on the screen. When we "use" a component, React creats a component instance, which is like an actual physical manifestation of a component, containg props, state, and more. A component instance, when rendered, will return a React element.  
* ☎️"**Rendering**" only means calling component functions and calculating what DOM elements need to be inserterd, deleted, or updated. It has nothing to do with writing to the DOM. Therefore, each time a  component instance is rendered and re-rendered, the function is called again.  
* 🔃 Only the **initial app render** and **state updates** can cause a render, which happens for the **entire application**, not just one single component.  
* 👨‍👩‍👧 When a component instance gets re-rendered, **all its children will get re-rendered as well**. This doesn't mean that all children will get updated in the DOM, thanks to reconciliation, which checks which elements have actually changed between two renders. But all this re-rendering can still have an impact on performance.  
* 🧬 Diffing is how React decides which DOM elements need to be added or modified. If, between renders, a certain REact element **stays at the same position in the element tree**, the corresponding DOM element and component state stay the same. If the element **changed to a different position**, or if it's a **different element type**, the DOM element and state will be destroyed.  
* 🗝️ Giving elements a key prop allows React to distinguish between multiple component instance. **When a key stays the same across renders**, the element is kept in the DOM. This is why we need to use keys in lists. **When we change the key between renders**, the DOM element will be destroyed and rebuilt. We use this as a trick to reset state.
* ⚠️ **Never declare a new component inside another component!** Doing so will re-create the nested component every time the parent component re-renders. React will always see the nested component as **new**, and therefore **reset its state** each time the parent state is updated.
* 🔮 The logic that produces JSX output for a component instance ("render logic") is ** not allowed to produce any side effects**: no API calls, no timers, no object or variable mutations, no state updates. **Side effects are allowed in event handlers** and `useEffect`.
* 📱 The Dom is updated in the commit phase, **but not by React, but by a "renderer" calld ReactDOM**. That's why we always need to include both libraries in a React web app project. We can use other renderers to use React on different platforms, for example to build mobile or native apps.
* 🗃️ Multiple state updates inside an even handler function are **batched**, so they happen all at once, **causing onoy one re-render**. This means we can **not access a state variable immediately after updating it**: state updates are **asynchronous**. Since React 18, batching also happens in timeouts, promises, and native event handlers.
* 🌐 When using events in event handlers, we get access to a **synthetic event object**, not the browser's native object, so that **events work the same way across all browsers**. The difference is that **most synthetic events bubble** including focus, blur, and change, which do not bubble as native browser event. Only the scroll event does not bubble
* 🛠️ **React is a library, not a framework**. This means that you can assemble your application using your favorite third-party libraries. The downside is that you need to find and learn all these additional libraries. No problem, as you will learn about the most commonly used libraries in this course.

## Component (Instance) Lifecycle
### Mount / Initial Render
* Component instance is rendered for the first time
* Fresh State and props are created

### Re-Render (optional)
This happens when:
* State changes
* Props change
* Parent re-renderxs
* Context changes

### Unmount
* Component instance is destroyed and resolve
* State and props are destroyed

👆 Code can be defined to run at any point in the component lifecycle using the `useEffect` hook

## `useEffect`
`useEffect` is used when you want a side effect to run, not as the component renders, after the component is painted on the screen, after it renders. Which means it is not run during each re-render, but only when the component mounts.

```
useEffect(function() { the effect you want it to run }, []); ---> The second argument is a Dependency Array (?)
```

## Where to create **Side Effects**
**Review**: A **side effect** is basically any "interaction between a React component and the world outside the component". We cal also think of a side effect as "code that actually does something". **Examples**: Data fetching, setting pu subscriptions, setting up timers, manually accessing the DOM, etc.

* Side Effects should never happen in Render logic. The two places that side effects should be placed in are:
  * Event handlers
  * Effects (using `useEffect`). Effects allow us to write code that will run at **different moments**: (mount, re-render, or unmount)
### Event Handlers
* Executed when the corresponding event happens

```
function handleClick() {
  fetch(`http://www.ombapi.com/?s=inception`)
    .then((res) => res.json())
    .then((data) => setMovies(data.Search))
}
```


### Effects (using `useEffect`)
* Executed **after the component mounts** (initial render), and after **subsequent  re-renders** (according to dependency array)
* Used to keep a component **synchronized with some external system** (in this example, with the API movie data)

```
useEffect(function () {
  fetch(`http://www.ombapi.com/?s=inception`)
    .then((res) => res.json())
    .then((data) => setMovies(data.Search));

  return () => console.log('Cleanup');
}, []);
```

