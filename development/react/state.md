# State in React

## Create a Stateful Component

State consist of any data your application needs to know about, that can change over time. You want your apps to respond to state changes and present an updated UI when necessary.

You create state in a React component by declaring a `state` property on the component class in its `constructor`. This initializes the component with `state` when it is created. The `state` property must be set to a JavaScript `object`.

You have access to the `state` object throughout the life of your component. You can update it, render it in your UI, and pass it as props to child components. Note that you must create a class component by extending `React.Component` in order to create `state` like this.

```jsx
class StatefulComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = { firstName: 'John' };
  }
  render() {
    return (
      <div>
        <h1>{this.state.firstName}</h1>
      </div>
    );
  }
};
```

## Render State in the User Interface

You have access to the data in `state` in component's `render()` method, using `this.state`.

When accessing the state within the `return` statement, enclose the value in curly braces.

React uses a virtual DOM to keep track of changes behind the scenes. When state data updates, it triggers a re-render of the components using that data - including child components that received the data as a prop. React updates the actual DOM, but only where necessary. You simply declare what the UI should look like.

Note that if you make a component stateful, no other components are aware of its `state`. Its `state` is completely encapsulated, or local to that component, unless you pass state data to a child component as `props`.

```jsx
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: 'freeCodeCamp'
    }
  }
  render() {
    return (
      <div>
        <h1>{this.state.name}</h1>
      </div>
    );
  }
};
```

## Render State in the User Interface Another Way

In the `render()` method, before the `return` statement, you can write JavaScript directly. For example, you could declare functions, access data from `state` or `props`, perform computations on this data, and so on. Then, you can assign any data to variables, which you have access to in the `return` statement.

```jsx
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: 'freeCodeCamp'
    }
  }
  render() {
    const name = this.state.name;
    return (
      <div>
        <h1>{name}</h1>
      </div>
    );
  }
};
```

## Set State with this.setState

React provides a method for updating component `state` called `setState`. You can call `setState` method within your component class like so: `this.setState()`, passing in an object with key-value pairs. The keys are your state properties and the values are the updated state data.

React expects you to never modify `state` directly, instead always use `this.setState()` when state changes occur. For the sake of performance, React state updates can by asynchronous.

```jsx
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: 'Initial State'
    };
    this.handleClick = this.handleClick.bind(this);
  }
  handleClick() {
    this.setState({
      name: "React Rocks!"
    });
  }
  render() {
    return (
      <div>
        <button onClick={this.handleClick}>Click Me</button>
        <h1>{this.state.name}</h1>
      </div>
    );
  }
};
```

## Bind 'this' to a Class Method

In addition to setting and updating `state`, you can also define methods for your component class. A class method typically needs to use the `this` keyword, so it can access properties on the class inside the scope of the method.

One way is to explicitly bind `this` in the constructor so `this` becomes bound to the class methods when the component is initialized.

```jsx
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      text: "Hello"
    };
    this.handleClick = this.handleClick.bind(this);
  }
  handleClick() {
    this.setState({
      text: "You clicked!"
    });
  }
  render() {
    return (
      <div>
        <button onClick={this.handleClick}>Click Me</button>
        <h1>{this.state.text}</h1>
      </div>
    );
  }
};
```

## Use State to Toggle an Element

You can't rely on the previous value of `this.state` or `this.props` when calculating the next value due to React may batch multiple `setState()` calls into a single update, or in other words, due to state updates may be asynchronous.

So, instead of code like this:

```jsx
this.setState({
  counter: this.state.counter + this.props.increment
});
```

you should use this:

```jsx
this.setState((state, props) => ({
  counter: state.counter + props.increment
}));
```

Or you can use a form without `props` if yo need only the `state`:

```jsx
this.setState(state => ({
  counter: state.counter + 1
}));
```

Note that you have to wrap the object literal in parentheses, otherwise JavaScript thinks it's a block of code.

```jsx
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      visibility: false
    };
    this.toggleVisibility = this.toggleVisibility.bind(this);
  }
  toggleVisibility() {
    this.setState(state => ({
      visibility: !state.visibility
    }));
  }
  render() {
    if (this.state.visibility) {
      return (
        <div>
          <button onClick={this.toggleVisibility}>Click Me</button>
          <h1>Now you see me!</h1>
        </div>
      );
    } else {
      return (
        <div>
          <button onClick={this.toggleVisibility}>Click Me</button>
        </div>
      );
    }
  }
}
```

