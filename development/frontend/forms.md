# HTML Forms

## Viewport height

The `vh` unit stands for viewport height, and is equal to 1% of the `height` of the viewport. This makes it relative to the viewport height.

```css
body {
  width: 100%;
  height: 100vh;
}
```

## Remove scroll-bars

You can get rid of the scroll-bars, by setting the `body` default `margin` added by some browsers to `0`.

## Form tag

To create a form you need to insert a `form` with an `action` targeting specific URL.

```html
<form action="https://register-demo.freecodecamp.org">
</form>
```

## Method

The `method` attribute specifies how to send form-data to the URL specified in the `action` attribute. The form-data can be sent via a `GET` request as URL parameters (with `method="get") or via a `POST` request as data is the request body (with `method="post").

```html
<form action="https://register-demo.freecodecamp.org" method="post">
</form>
```

## Form sections - fieldset

You can divide form into distinct sections by using `fieldset` elements.

```html
<form method="post" action="https://register-demo.freecodecamp.org">
  <fieldset></fieldset>
  <fieldset></fieldset>
  <fieldset></fieldset>
</form>
```

## Labels

You can use `label` elements to provide information to the user about what data is needed to be provided.

```html
<form method="post" action="https://register-demo.freecodecamp.org">
  <fieldset>
    <label>Enter Your First Name:</label>
    <label>Enter Your Last Name:</label>
    <label>Enter Your Email:</label>
    <label>Create a New Password:</label>
  </fieldset>
</form>
```

## Display inline elements as a block and rem units

The `rem` unit stands for root `em`, and is relative to the font size of the `html` element.

As `label` elements are inline by default, they are all displayed side by side on the same line. To make them appear on separate lines, add `display: block` to the `label` element, and add a `margin` of `0.5rem 0`, to separate them from each other.

```css
label {
  display: block;
  margin: 0.5rem 0;
}
```

## Input elements

You can nest an `input` element within `label` element. For the sake of readability you can add a space at the end of the label text.

```html
<fieldset>
  <label>Enter Your First Name: <input /></label>
  <label>Enter Your Last Name: <input /></label>
  <label>Enter Your Email: <input /></label>
  <label>Create a New Password: <input /></label>
</fieldset>
```

Following accessibility best practices, link the `input` elements and the `label` elements togther using the `for` attribute.

```html
<fieldset>
  <label for="first-name">Enter Your First Name: <input id="first-name"/></label>
  <label for="last-name">Enter Your Last Name: <input id="last-name"/></label>
  <label for="email">Enter Your Email: <input id="email"/></label>
  <label for="new-password">Create a New Password: <input id="new-password"/></label>
</fieldset>
```

## Input type

By specifying the `type` attribute of a form element we notify browser about the kind of data it should expect. If the `type` is not specified, the browser will default to `text`.

The `email` type only allows emails with a `@` and a `.` in the domain. The `password` type obscures the input, and warns if the site does not use HTTPS.

```html
<fieldset>
  <label for="first-name">Enter Your First Name: <input id="first-name" type="text" /></label>
  <label for="last-name">Enter Your Last Name: <input id="last-name" type="text" /></label>
  <label for="email">Enter Your Email: <input id="email" type="email" /></label>
  <label for="new-password">Create a New Password: <input id="new-password" type="password" /></label>
</fieldset>
```

## Submit

The first `input` element with a `type` of `submit` is automatically set to submit its nearest parent `form` element.

```html
<input type="submit" value="Submit" />
```

## Required fields

You can add the `required` attribute to the `input` elements in the form.

Now, if you try to submit the form without filling in the required fields, you will see an error message.

## Custom validation

Certain `type` attribute values come with built-in form validation. For example, `type="email"` requires that the value be a valid email address.

You can add custom validation to the password `input` element, by adding a `minlength` attribute with a value of `8`. Doing so prevents inputs of less than 8 characters being submitted.

```html
<label for="new-password">Create a New Password: <input id="new-password" type="password" minlength="8" required /></label>
```

With `type="password"` you can use the `pattern` attribute to define a regular expression that the password must match to be considered valid.

```html
<label for="new-password">Create a New Password: <input id="new-password" type="password" pattern="[a-z0-5]{8,}" required /></label>
```

The above is a regular expression which matches eight or more lowercase letters or the digits `0` to `5`.

## Radio buttons

Use `radio` type for the radio buttons. To relate the radio buttons, so that you can select only one radio input at a time, give them the same `name` attribute.

```html
<fieldset>
  <label><input type="radio" name="account-type" /> Personal</label>
  <label><input type="radio" name="account-type" /> Business</label>
</fieldset>
```

## Fieldset legend element

The `legend` element provides a label for the `fieldset`.

`checked` attribute selects specified input element.

```html
<fieldset>
  <legend>Account type (required)</legend>
  <label><input type="radio" name="account-type" checked /> Personal</label>
  <label><input type="radio" name="account-type" /> Business</label>
</fieldset>
```

## Link input with label

Follow accessibility best practices by linking the `input` elements and the `label` elements.

The `for` attribute of the `label` element shall be equal to the `id` attribute of the corresponding `input` element.

```html
<fieldset>
  <legend>Account type (required)</legend>
  <label for="personal-account"><input id="personal-account" type="radio" name="account-type" checked /> Personal</label>
  <label for="business-account"><input id="business-account" type="radio" name="account-type" /> Business</label>
</fieldset>
```

## Checkbox

Here is an example of getting user confirmation that he has read the terms and conditions using `checkbox` input type.

```html
<label for="terms-and-conditions"><input id="terms-and-conditions" type="checkbox" required/>I accept the <a href="https://www.freecodecamp.org/news/terms-of-service/">terms and conditions</a></label>
```

## Uploading file

The `input` type `file` allows you to upload file from your computer.

```html
<label for="profile-picture">Upload a profile picture: <input id="profile-picture" type="file"></lable>
```

## Type number

The `input` type `number` allows you to restrict input to just integer values within specified range.

```html
<label for="age">Input your age (years): <input id="age" type="number" min="13" max="120"></label>
```

## Dropdown list

Adding a dropdown to the form is easy with the `select` element. The `select` element is a container for a group of `option` elements, and the `option` element acts as a label for each dropdown option. Both elements require closing tags.

```html
<label> How did you hear about us?
  <select>
    <option>(select one)</option>
    <option>freeCodeCamp News</option>
    <option>freeCodeCamp YouTube Channel</option>
    <option>freeCodeCamp Forum</option>
    <option>Other</option>
  </select>
</label>
```

Each `option` needs to be given a `value` attribute. Without which, the text content of the `option` will be submitted to the server.

```html
<label for="referrer"> How did you hear about us?
  <select id="referrer">
    <option value="">(select one)</option>
    <option value="1">freeCodeCamp News</option>
    <option value="2">freeCodeCamp YouTube Channel</option>
    <option value="3">freeCodeCamp Forum</option>
    <option value="4">Other</option>
  </select>
</label>
```
 

## Textarea

The `textarea` element acts like an `input` element of type `text`, but comes with the added benefit of being able to receive multi-line text, and an initial number of text rows and columns.

To give it an initial size, you can add the `rows` and `cols` attributes.

```html
<label for="bio">Provide a bio:
  <textarea id="bio" rows="3" cols="30"></textarea>
</label>
```

### Placeholder

To give users an idea of what to put in their bio, the `placeholder` attribute is used. The `placeholder` accepts a text value, which is displayed until the user starts typing.

```html
<label for="bio">Provide a bio:
  <textarea id="bio" rows="3" cols="30" placeholder="I like coding on the beach..."></textarea>
</label>
```

## Name

With form submissions, it is useful, and good practice, to provide each submittable element with a `name` attribute. This attribute is used to identify the element in the form submission.

```html
<label for="bio">Provide a bio:
  <textarea id="bio" name="bio" rows="3" cols="30" placeholder="I like coding on the beach..."></textarea>
</label>
```

## Removing fieldset default borders

During development, it is useful to see the `fieldset` default borders. However, they make the content appear too separated.

```css
fieldset {
  border: none;
}
```

## Add separation to fieldset elements

To give the `fieldset` elements a bit of separation, give them a `broder-bottom` style.

```css
fieldset {
  border: none;
  border-bottom: 3px solid #3b3b4f;
}
```

## Last element of specific type

You can select the last element of a specific type using the `last-of-type` CSS pseudo-class.

```css
fieldset:last-of-type {
  border-bottom: none;
}
```

## Elements with full width of their parents

You can make elements to take up the full width of their parent elements by using `width: "100%"`.

```css
input, textarea, select {
  width: 100%;
}
```

## Set label and input element on the same line

You can set the `input` and `label` text to appear on the same line by following actions:

- add class "inline" to the input element
- set `.inline` with the property `width: unset`. This will remove the earlier rule which set all the `input` elements to `width: 100%`

```css
.inline {
  width: unset;
}
```

## Vertical alignment

You can tweak element's vertical alignment by setting the `vertical-align` property to specific value.

```css
.inline {
  width: unset;
  vertical-align: middle;
}
```

## Adjust input elements background color

You can make the `input` and `textarea` elements blend in with the background theme, by setting `background-color` property.

```css
input, textarea {
  background-color: #0a0a23;
  border: 1px solid #0a0a23;
}
```

In order to make text visible, you also need to adjust `color` property.

```css
input, textarea {
  background-color: #0a0a23;
  border: 1px solid #0a0a23;
  color: #ffffff;
  min-height: 2em;
}
```

## Attribute selector

To style the submit button, you can use an *attribute* selector, which selects an element based on the given attribute value. For example, `input[name="password"]`.

```css
input[type="submit"] {
  display: block;
  width: 60%;
  margin: 0 auto;
}
```

## Project files

- [index.html](forms/index.html.md)
- [styles.css](forms/styles.css.md)
