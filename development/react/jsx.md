# React JSX

## Simple JSX Element

React uses a syntax extension of JavaScript called JSX that allows you to write HTML directly within JavaScript. This introduces programmatic power to HTML and keeps your code readable.

You can write JavaScript directly within JSX. Simply include the code within curly braces.

JSX must be compiled into JavaScript.

```jsx
const JSX = <h1>Hello JSX!</h1>;
ReactDOM.render(JSX, document.getElementById('root'));
```

## A Complex JSX Element

JSX must return a *single* element.

```jsx
const JSX = (
  <div>
    <h1>Nutrition</h1>
    <p>Usually you take meals three times a day.</p>
    <ul>
      <li>Breakfast</li>
      <li>Lunch</li>
      <li>Dinner</li>
    </ul>
  </div>
);
```

## Comments in JSX

For readability you might need to add comments to you code.

To put comments inside JSX, you use the syntax `{/* */}`.

```jsx
const JSX = (
  <div>
    {/* some insightful comment */}
    <h1>This is a block of JSX</h1>
    <p>Here's a subtitle</p>
  </div>
);
```

## Render HTML Elements to the DOM

With React, we can render JSX directly to HTML DOM using React's rendering API known as ReactDOM.

ReactDOM offers method `ReactDOM.render(componentToRender, targetNode)`.

```jsx
const JSX = (
 <div>
    <h1>Hello World</h1>
    <p>Lets render this to the DOM</p>
  </div>
);
ReactDOM.render(JSX, document.getElementById('challenge-node'));
```

## Define as HTML Class in JSX


You cannot use `class` to define HTML classes as it is a reserved keyword in JavaScript. Instead, JSX uses `className`.

The naming convention for all HTML attributes and event references in JSX become camelCase, like `onClick`, `onChange`, etc.

```jsx
const JSX = (
  <div className='myDiv'>
    <h1>Add a class to this div</h1>
  </div>
);
```

## Self-Closing JSX Tags

Any JSX element can be written with a self-closing tag, and every element must be closed.

For example, a `<div>` element can be written as `<div />`. 

```jsx
const JSX = (
  <div>
    <h2>Welcome to React!</h2> <br />
    <p>Be sure to close all tags!</p>
    <hr />
  </div>
);
```
