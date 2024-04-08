# Basic CSS

CSS tells the browser how to display your webpage. You can use CSS to set the color, font, size, and other aspects of HTML elements.

## A `style` element

You can add style to an element by specifying it in the `style` element and setting property for it:

```css
<style>
 element {
  property: value;
 }
</style>
```

## Type selector

For example:

```css
<style>
 h1 {
  text-align: center;
 }
</style>
```

The `h1` in the previous example is a *type selector* to style the `h1` element.

## Grouping selectors

You can add the same group of styles to many elements by creating a list of selectors. Each selector is separated with commas.

```css
h1, h2, p {
  text-align: center;
}
```

## styles.css file

You can style HTML elements by writing CSS inside the `style` tags.

But more convenient is to put all the styles in a separate file called `styles.css`.

You need to nest self-closing `link` element in the `head` element. Give it a `rel` attribute value `stylesheet` and an `href` attribute value of `styles.css`.

```html
<head>
  <link rel="stylesheet" href="styles.css" />
</head>
```

## Styling of the page for mobile web

For the styling of the page to look similar on mobile as it does on a desktop or laptop, you need to add a `meta` element with a special `content` attribute within the `head` element:

```html
<head>
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
</head>
```

## Background color

To change background color use `background-color` property.

```css
body {
  background-color: brown;
}
```

## Div - Design layout element

The `div` element is used mainly for design layout purposes.

```html
<body>
  <div id="menu">
  <main>
    <section>
    </section>
  </main>
  </div>
</body>
```

## id selector

You can use the `id` selector to target a specific element with an `id` attribute. An `id` selector is defined by placing the hash symbol `#` directly in front of the element's `id` value.

```css
#menu {
  width: 300px;
}
```

## Comments is CSS

Comments in CSS look like this:

```css
/* comment here */
```

## Specifying width in percentage of parent element

Instead of specifying the width of the element in pixels (`px`), you can use percentage of the width of its parent element.

```css
#menu {
  width: 80%; /* 80% of its parent element (body) */
}
```

## Center element horizontally

You can center element horizontally by setting its `margin-left` and `margin-right` properties to `auto`. Think of the margin as invisible space around an element.

```css
#menu {
  margin-left: auto;
  margin-right: auto;
}
```

## Class selector

It is more common to use different from id selector - a class selector.

A *class selector* is defined by a name with a dot directly in front of it. This selector targerts all elements with specified `class` attribute.

```css
.menu {
  background-color: burlywood;
}
```

```html
<body>
  <div class="menu">
  ...
  </div>
</body>
```

## Background image

You can use a `background-image` property to set an image as an element background.

```css
body {
  background-image: url(https://cdn.freecodecamp.org/curriculum/css-cafe/beans.jpg);
}
```

## Place two block-level elements in one row 

The task is to set two `p` elements in one row.

`p` elements are *block-level* elements, so they take up the entire width of their parent element. 

To get them on the same line, you need to apply some styling so that block-level elements behave like *inline* elements. You can do this by setting `display` property with value `inline-block`.

```html
<article>
  <p class="flavor">French Vanilla</p>
  <p class="price">3.00</p>
</article>
```

```css
.flavor {
  display: inline-block;
  text-align: left;
}

.price {
  display: inline-block;
  text-align: right;
}
```

## Apply styling to nested elements

You can style specific nested elements inside element with specific class by listing selectors.

```html
<article class="item">
  <p class="flavor">French Vanilla</p>
  <p class="price">3.00</p>
</article>
```

```css
.item p {
  display: inline-block;
}

.flavor {
  text-align: left;
}

.price {
  text-align: right;
}
```

## Align inline elements

`inline-block` elements only take up the width  of their content. You can use a `width` property to control their size.

For example, to spread `p` elements within the row, you can set width to `50%` each. To avoid shifting of second element to the next row pay attention that there is no white spaces in the HTML markup between two `p` elements, like newlines.

```html
<article class="item">
  <p class="flavor">French Vanilla</p><p class="price">3.00</p>
</article>
```

```css
.item p {
  display: inline-block;
}

.flavor {
  width: 50%;
  text-align: left;
}

.price {
  width: 50%;
  text-align: right;
}
```

## Prevent long strings wrapping around in case of smaller page width

You can rearrange the width percentage between `p` elements on the same row taking into account their average width. This will prevent unnecessary wrapping of the `p` element in case in page width become smaller.

```css
.flavor {
  width: 75%;
  text-align: left;
}

.price {
  width: 25%;
  text-align: right;
}
```

## Set CSS rules for several selectors

You can set the CSS rule for several selectors, listing them with comma separator.

```css
.flavor, .dessert {
  text-align: left;
  width: 75%;
}
``` 

## Padding

You can separate content of the element from the element border with various `padding` properties.

```css
.menu {
  padding-left: 20px;
  padding-right: 20px;
  padding-top: 20px;
  padding-bottom: 20px;
}
```

Since all 4 sides of the menu have the same internal spacing, you can use a single `padding` property:

```css
.menu {
  padding: 20px;
}
```

## Prevent element's growing

You can use a `max-width` property to the specific element to prevent it from growing too wide if it's `width` property depends on the size of the parent element.

```css
.menu {
  width: 80%;
  max-width: 500px;
}
```

## Font

You can make change the `font-family` of text, to make it look different from the default font of your browser.

```css
body {
  font-family: sans-serif;
}
```

You can ad a *fallback* value for the font-family by adding another font name separated by comma. Fallbacks are used in instances where the initial is not found/available.

```css
h1, h2 {
  font-family: Impact, serif;
}
```

You can ad a *fallback* value for the font-family by adding another font name separated by comma. Fallbacks are used in instances where the initial is not found/available.

```css
h1, h2 {
  font-family: Impact, serif;
}
```

## Font styles

You can change font styles using `font-style` property.

```css
.established {
  font-style: italic;
}
```

## Font size

You can use the `font-size` property to adjust the size of font.

```css
h1 {
  font-size: 40px;
}
```

## Height property

You can change the height of the element by specifying a value for the `height` property.

```css
hr {
  height: 3px;
}
```

## Borders

The edges of an elements are known as *borders*.

You can control color of the borders using the `border-color` property.

```css
hr {
  height: 3px;
  border-color: brown;
}
```

You can adjust borders' thickness via `border-width` property. It's default value is `1px` for `hr` element.

## Pseudo-selectors

You can change properties of a link when the link has actually been visited by using a *pseudo-selector* that looks like `a:visited { propertyName: propertyValue ; }`.

```css
a:visited {
  color: grey;
}
```

You can change properties of a link when the mouse hovers over them by using a *pseudo-selector* that looks like `a:hover { propertyName: propertyValue; }`.

```css
a:hover {
  color: brown;
}
```

You can change properties of a link when the link is actually being clicked by using a *pseudo-selector* that looks like `a:active { propertyName: propertyValue; }`.

```css
a:active {
  color: white;
}
```

## Center inline elements

To make the inline-level element (i.e. image) to behave like a block-level elements, use `display` property with the value `block`.

To center the block-level element, use value `auto` for the 'margin-left` and 'margin-right` properties.

```css
img {
  display: block;
  margin-left: auto;
  margin-right: auto;
}
```

## Negative margin

You can add a negative margin to an element to pull them to specific direction from their current position.

```css
img {
  margin-top: -25px;
}
```

## Project files

- [index.html](cssbasic/index.html.md)
- [styles.css](cssbasic/styles.css.md)
