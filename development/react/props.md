# Props

## Pass Props to a Stateless Functional Component

In React, you can pass **props**, properties, to child components.

You use **custom HTML attributes** created by you and supported by React to be passed to the component.

It is standard to call this value `props` and when dealing with stateless functional components, you basically consider it as an argument to a function which returns JSX.

```jsx
const CurrentDate = (props) => {
  return (
    <div>
      <p>The current date is: {props.date}</p>
    </div>
  );
};

class Calendar extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h3>What date is it?</h3>
        <CurrentDate date={Date()}/>
      </div>
    );
  }
};
```

## Pass an Array as Props

To pass an array to a JSX element, it must be treated as JavaScript and wrapped in curly braces.

Array methods such as `join()` can be used when accessing the property.

```jsx
const ChildComponent = (props) => <p>{props.colors.join(', ')}</p>
```

This will join all array items into a comma separated string.

```jsx
const List = (props) => {
  return <p>{props.tasks.join(", ")}</p>
};

class ToDo extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h1>To Do Lists</h1>
        <h2>Today</h2>
        <List tasks={["discuss desing", "release an issue"]}/>
        <h2>Tomorrow</h2>
        <List tasks={["wash car", "study react", "clarify tasks"]}/>
      </div>
    );
  }
};
```

## Use Default Props

React has an option to set default props. You can assign default props to a component as a property on the component itself and React assign the default prop if necessary.

React assigns default props if props are undefined, but if you pass `null` as the value for a prop, it will remain `null`.

```jsx
const ShoppingCart = (props) => {
  return (
    <div>
      <h1>Shopping Cart Component</h1>
    </div>
  )
};

ShoppingCart.defaultProps = { items: 0 };
```

## Override Default Props

The ability to set default props is a useful feature in React. The way to override the default props is to explicitly set the prop values for a component.

```jsx
const Items = (props) => {
  return <h1>Current Quantity of Items in Cart: {props.quantity}</h1>
}

Items.defaultProps = {
  quantity: 0
}

class ShoppingCart extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return <Items quantity={10}/>
  }
};
```

## Use PropTypes to Define the Props You Expect

React provides useful type-checking features to verify that components receive props of the correct type. The feature will trow a warning when the data passing to the component is of any wrong type.

It's considered a best practice to set `propTypes` when you know the type of a prop ahead of time. You can define a `propType` property for a component in the same way you defined `defaultProps`.

```jsx
MyComponent.propTypes = { handleClick: PropTypes.func.isRequired }
```

Adding `isRequired` tells React that `handleClick` is a required property for that component. You will see a warning if that prop isn't provided.

The `func` represents `function`, and `bool` - `boolean`.

You can declare that a prop is a specific JS type. By default, these are all optional:

```jsx
PropTypes.array
PropTypes.bool
PropTypes.func
PropTypes.number
PropTypes.object
PropTypes.string
PropTypes.symbol
```

In addition to the primitive types, there are other types available, like React element.

`PropTypes` is imported independently from React, like this: `import PropTypes from 'prop-types';`.

```jsx
const Items = (props) => {
  return <h1>Current Quantity of Items in Cart: {props.quantity}</h1>
};

Items.propTypes = { quantity: PropTypes.number.isRequired };

Items.defaultProps = {
  quantity: 0
};

class ShoppingCart extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return <Items />
  }
};
```

## Access Props Using this.props

The ES6 class component uses a slightly different convention to access props.

Anytime you refer to a class component within itself, you use the `this` keyword.
To access props within a class component, you preface the code that you use to access it with `this`.

```jsx
class App extends React.Component {
  constructor(props) {
    super(props);

  }
  render() {
    return (
        <div>
            <Welcome name='John!'/>
        </div>
    );
  }
};

class Welcome extends React.Component {
  constructor(props) {
    super(props);

  }
  render() {
    return (
        <div>
          <p>Hello, <strong>{this.props.name}</strong>!</p>
        </div>
    );
  }
};
```

## Review Using Props with Stateless Functional Components

A *stateless functional component* is any function you write which accepts props and returns JSX. A *stateless component*, on the other hand, is a class that extends `React.Component`, but does not use internal state. Finally, a *stateful component* (aka component or React component) is a class component that does maintain its own internal state.

A common pattern is to try to minimize statefulness and to create stateless functional components wherever possible. This helps contain your state management to a specific area of your application. In turn, this improves development and maintenance of your app by making it easier to follow how changes to state affect its behavior.

```jsx
class CampSite extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <Camper name='Martin'/>
      </div>
    );
  }
};

const Camper = (props) => {
  return (
    <p>{props.name}</p>
  )
};

Camper.defaultProps = {
  name: 'CamperBot'
};

Camper.propTypes = { name: PropTypes.string.isRequired };
```
