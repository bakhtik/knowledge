# React Components

Everything in React is a component.

There are two ways to create a React component:

- use a JavaScript function
- use a JavaScript ES6 `class` syntax.

## Stateless Functional Component

Defining a component using a JavaScript function creates a *stateless functional component.*
A stateless component can receive data and render it, but does not manage or track changes to that data.

To create a component with a function, write a JavaScript function that returns either JSX or `null`.

React component architecture allows you to compose UI from many separate, isolated components.

```jsx
const MyComponent = function() {
  return (
    <div>
      <p>Some text.</p>
    </div>
  );
}
```

## React Component

The other way to define a react component is with the ES6 `class` syntax.

Component shall 

- extend the `React.Component` class
- have a `constructor` that calls constructor of the parent class using `super()` function

```jsx
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h1>Hello React!</h1>
      </div>
    );
  }
};
```

## Component with Composition

You can create a *parent* component which renders *children* components. To render a component as a child in a React component, you include the component name written as a custom HTML tag in the JSX.

A component name must be wrapped in `< />`. React renders the markup for that component in the location of the tag.

```jsx
const ChildComponent = () => {
  return (
    <div>
      <p>I am the child</p>
    </div>
  );
};

class ParentComponent extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h1>I am the parent</h1>
        <ChildComponent />
      </div>
    );
  }
};
```

## Render Nested Components

In React you breaking down your UI into its basic building blocks, and those pieces become the components. This helps to separate the code responsible for the UI from the code responsible for handling your application logic.

```jsx
const TypesOfFruit = () => {
  return (
    <div>
      <h2>Fruits:</h2>
      <ul>
        <li>Apples</li>
        <li>Blueberries</li>
        <li>Strawberries</li>
        <li>Bananas</li>
      </ul>
    </div>
  );
};

const Fruits = () => {
  return (
    <div>
      <TypesOfFruit />
    </div>
  );
};

class TypesOfFood extends React.Component {
  constructor(props) {
    super(props);
  }

  render() {
    return (
      <div>
        <h1>Types of Food:</h1>
        <Fruits />
      </div>
    );
  }
};
```

## Compose React Components

Rendering ES6 style class components withing other components is no different than rendering the simple components. You can render JSX elements, stateless functional components, and ES6 class components within other components.

```jsx
class Fruits extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h2>Fruits:</h2>
        <NonCitrus />
        <Citrus />
      </div>
    );
  }
};

class TypesOfFood extends React.Component {
  constructor(props) {
     super(props);
  }
  render() {
    return (
      <div>
        <h1>Types of Food:</h1>
        <Fruits />
        <Vegetables />
      </div>
    );
  }
};
```

## Render a Class Component to the DOM

To render React components you shall use this syntax: `ReactDOM.render(componentToRender,  targetNode)`. The first argument is the React component that you want to render. The second argument is the DOM node that you want to render that component within.

For JSX elements, you pass in the name of the element that you want to render. However, for the React components, you need to use the same syntax as if you were rendering a nested component. You use this syntax for both ES6 class components and functional components.

```jsx
class TypesOfFood extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h1>Types of Food:</h1>
        <Fruits />
        <Vegetables />
      </div>
    );
  }
};

ReactDOM.render(<TypesOfFood />, document.getElementById('challenge-node'));
```
