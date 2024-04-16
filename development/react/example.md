# React App Example

```html
<div id="app"></div>
```

```jsx
function Person(props) {
  return (
    <div className="person">
      <h1>{props.name}</h1>
      <p>Your Age: {props.age}</p>
    </div>
  );
}

var app = (
  <div>
    <Person name="Max" age="28"/>
    <Person name="Manu" age="29"/>
  </div>
);

ReactDOM.render(app, document.querySelector('#app'));
```

```css
.person {
  display: inline-block;
  margin: 10px;
  border: 1px solid #ccc;
  box-shadow: 0 2px 2px #ccc;
  width: 200px;
  padding: 20px;
}
```
