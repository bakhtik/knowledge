# CSS Colors

Here you can see different ways to set color values and how to pair colors with each other.

## Color keywords

One way to add color to an element is to use a *color keyword* like `black`.

```css
.marker {
  background-color: red;
}
```

## Margin shorthand

The `margin` *shorthand property* sets `margin-top`, `margin-right`, `margin-bottom`, and `margin-left` all to the same value.

```css
.marker {
  margin: auto;
}
```

When the shorthand `margin` property has two values, it sets `margin-top` and `margin-bottom` to the first value, and `maragin-left` and `margin-right` to the second value.

```css
.marker {
  margin: 10px auto;
}
```

## Multiple classes

Multiple classes can be added to an element by listing them in the `class` attribute and separating them with a space.

If you add multiple classes to an HTML element, the styles of the first classes you list may be overridden by later classes.

```html
<div class="marker one">
</div>
```

## Color models

There are two main color models: the *additive* RGB (red, green, blue) model used in electronic devices, and the *subtractive* CMYK (cyan, magenta, yellow, black) model used in print.

CSS `rgb` function uses the RGB model where colors begin as black, and change as different levels of red, green, and blue are introduced.

```css
.container {
background-color: rgb(0, 0, 0); /* black color */
}
```

## RGB function

The CSS `rgb` function accepts values, or *arguments*, for red, green, and blue, and produces a color:

```css
rgb(red, green, blue);
```

Each red, green, and blue value is a number from 0 to 255. 0 means there's 0% of that color, and is black. 255 means that there's 100% of that color.

```css
.one {
  background-color: rgb(255, 0, 0); /* red color */
}

.two {
  background-color: rgb(0, 127, 0); /* same color as a 'green' keyword */
}

.three {
  background-color: rgb(0, 0, 255); /* blue color */
}
```

## Padding shorthand

You can use the shorthand `padding` property to set one value for the top and bottom, and another for the left and right padding:

```css
.container {
  padding: 10px 0;
}
```

## Primary colors

In the additive RGB color model, *primary* colors are colors that, when combined, create pure white. But for this to happen, each color needs to be at its highest intensity.

```css
.one {
  background-color: rgb(255, 0, 0); /* primary red */
}

.two {
  background-color: rgb(0, 255, 0); /* primary green */
}

.three {
  background-color: rgb(0, 0, 255); /* primary blue */
}

.container {
  background-color: rgb(255, 255, 255); /* white color as a combination of primary colors */
}
```

## Secondary colors

*Secondary colors* are the colors you get when you combine primary colors.


```css
.one {
  background-color: rgb(255, 255, 0); /* secondary color, yellow */
}

.two {
  background-color: rgb(0, 255, 255); /* secondary color, cyan */
}

.three {
  background-color: rgb(255, 0, 255); /* secondary color, magenta */
}
```

## Tertiary colors

*Tertiary colors* are created by combining a primary with a nearby secondary color.


```css
.one {
  background-color: rgb(255, 127, 0); /* tertiary color, orange as a combination of red and yellow */
}

.two {
  background-color: rgb(0, 255, 127); /* tertiary color, spring green, a combination of cyan with green */
}

.three {
  background-color: rgb(127, 0, 255); /* tertiary color, violet, a combination of magenta with blue */
}
```

```css
.one {
  background-color: rgb(127, 255, 0); /* tertiary color, chartreuse green (green + yellow) */
}

.two {
  background-color: rgb(0, 127, 255); /* tertiary color, azure (blue + cyan) */
}

.three {
  background-color: rgb(255, 0, 127); /* tertiary color, rose (red + magenta) */
}
```

## A color wheel

A color wheel is a circle where similar colors, or *hues*, are near each other, and different ones are further apart. For example, pure red is between the hues roes and orange.

Two colors that are opposite from each other on the color wheel are called *complementary colors*. If two complementary colors are combined, they produce gray. But when they are placed side-by-side, these colors produce strong visual contrast and appear brighter.

This contrast (like between red and cyan) can be distracting if it's overused on a website, and can make text hard to read if it's placed on a complementary-colored background.

It's better practice to choose one color as the dominant color, and use its complementary color as an accent to bring attention to certain content on the page.

If, for example, you enclose red between black segments, you eyes are naturally drawn to the red color in the center. When designing a site, you can use this effect to draw attention to important headings, buttons, or links.

## Hexadecimal values

A very common way to apply color to an element with CSS is with *hexadecimal* or hex values. They're really just another form of RGB values.

Hex values start with a `#` character and take six characters from 0-9 and A-F. The first pair of characters represent red, the second pair represent green, and the third pair represent blue.

```css
.green {
  background-color: #00FF00;
}
```

Hexadecimal, or base 16 values, go from 0 - 9, then A - F.

With hex colors, `00` is 0% of that color, and `FF` is 100%.

```css
.green {
  background-color: #007F00;
}
```

## HSL Color Model

The *HSL* color model, or hue, saturation, and lightness, is another way to represent colors. 

The CSS `hsl` function accepts 3 values: a number from 0 to 360 for hue, a percentage from 0 to 100 for saturation, and a percentage from 0 to 100 for lightness.

If you imagine a color wheel, the hue red is at 0 degrees, green is at 120 degrees, and blue is at 240 degrees.

Saturation is the intensity of a color from 0%, or gray, to 100% for pure color. You must add the percent sign `%` to the saturation and lightness values.

Lightness is how bright a color appears, from 0%, or complete black, to 100%, complete white, with 50% being neutral.

```css
.blue {
  background-color: hsl(240, 100%, 50%);
}
```

## Color transition - Gradient

A gradient is when one color transitions into another. The CSS `linear-gradient` function actually creates an `image` element, and is usually paired with the `background` property which can accept an image as a value.

The `linear-gradient` function is very flexible:

```
linear-gradient(gradientDirection, color1, color2, ...);
```

`gradientDirection` is the direction of the line used for the transition. `color1` and `color2` are color arguments, which are the colors that will be used in the transition itself. These can be any type of color, including color keywords, hex, `rgb`, or `hsl`.

The degree starts from the top and goes clockwise direction.

```css
.red {
  background: linear-gradient(90deg, rgb(255, 0, 0), rgb(0, 255, 0));
}
```

While the `linear-gradient` function needs a minimum of two color arguments to work, it can accept many color arguments.

```css
.red {
  background: linear-gradient(90deg, rgb(255, 0, 0), rgb(0, 255, 0), rgb(0, 0, 255));
}
```

### Color-stops

Color-stops allow you to fine-tune where colors are placed along the gradient line. They are a length unit like `px` or percentages that follow a color in the `linear-gradient` function.

```css
.red {
  background: linear-gradient(90deg, rgb(255, 0, 0) 75%, rgb(0, 255, 0), rgb(0, 0, 255));
}
```

## Opacity

*Opacity* describes how opaque, or non-transparent, something is.

With the CSS `opacity` property, you can control how opaque or transparent an element is. With the value `0`, or 0%, the element will be completely transparent, and at `1.0`, or 100%, the element will be completely opaque like it is by default.

```css
.sleeve {
  opacity: 0.5;
}
```

Another way to set the opacity for an element is with the *alpha channel.* Similar to the `opacity` property, the alpha channel control how transparent or opaque a color is.

To add an alpha channel to an `rgb` color, use the `rgba` function instead. It takes one more number from `0` to `1.0` for the alpha channel:

```css
rgba(redValue, greenValue, blueValue, alphaValue);
```

To add an alpha channel into the hex value, add the forth hexadecimal value for the alpha channel.

`hsl` has `hsla` function for adding alpha channel value, the same way as in the `rgba` function.

```css
.red {
  background-color: rgb(255, 0, 0, 0.8);
}
.green {
  background-color: #3B7e20CC;
}
.blue {
  background-color: hsla(223, 59%, 31%, 0.8);
}
```

## Display property

The default `display` property for `div` elements is `block`. So when two `block` elements are next to each other, they stack like actual blocks.

To position two `div` elements on the same line, set their `display` properties to `inline-block`.

```css
.cap, .sleeve {
  display: inline-block;
}
``` 

## Borders

All HTML elements have borders, though they're usually set to `none` by default. With CSS, you can control all aspects of an element's border, and set the border on all sides, or just one side at a time. 

For a border to be visible, you need to set its width and style.

Borders have several styles to choose from. You can make your border:

- a solid line (the most common)
- a double line
- a dashed line
- a dotted line

If no color is set, black is used by default.
But to make your code more readable, it's better to set the border color explicitly.

```css
.sleeve {
  border-left-width: 10px;
  border-left-style: solid;
  border-left-color: black;
}
```

The `border-left` shorthand property lets you to set the left border's width, style, and color at the same time.

```css
border-left: width style color;
```

```css
.sleeve {
  border-left: 10px double black;
}
```

## Shadow

The `box-shadow` property lets you apply one or more shadows around an element.

```css
box-shadow: offsetX offsetY color;
```

- both `offsetX` and `offsetY` accept number values in `px` and other CSS units.
- a positive `offsetX` value moves the shadow right and a negative value moves it left.
- a positive `offsetY` value moves the shadow down and a negative value moves it up.
- if you want a value of zero (0) for any or both `offsetX` and `offsetY`, you don't need to add a unit. Every browser understand that zero means no change.

The height and width of the shadow is determined by the height and width of the element it's applied to. You can also use and optional `spreadRadius` value to spread out the reach of the shadow.

```css
.red {
  box-shadow: 5px 5px red;
}
```

### Blurring shadow

There is an optional `blurRadius` value for the `box-shadow` property that changes default sharp edges of the shadow.

```css
box-shadow: offsetX offsetY blurRadius color;
```

If a `blurRadius` value isn't included, it defaults to `0` and produces sharp edges. The higher the value of `blurRadius`, the greater the blurring effect is.

```css
.green {
  box-shadow: 5px 5px 5px green;
}
```

### Expanding the shadow

You can expand the shadow our further with the optional `spreadRadius` value:

```css
box-shadow: offsetX offsetY blurRadius spreadRadius color;
```

`spreadRadius` defaults to `0` if it isn't included.

```css
.blue {
  box-shadow: 0 0 0 5px blue;
}
```

## Project files

- [index.html](csscolors/index.html.md)
- [styles.css](csscolors/styles.css.md)
