# Basic HTML

## HTML Tags

HTML elements have opening tags like `<h1>` and closing tangs like `</h1>`.
The text an element will display goes between its opening and closing tags.

```html
<h1>Hello World</h1>
```

## Heading Elements

The `h1` through `h6` heading elements are used to signify the importance of content below them. Only use one `h1` element per page.

## Paragraph

The `p` element is used to create a paragraph of text.

```html
<p>See more cat photos in our gallery</p>
```

## Commenting

Commenting allows you to leave messages without affecting the browser display.

```html
<!-- TODO: Add link to cat photos -->
```

## HTML5 Content Areas Tags

HTML5 has some elements that identify different content areas.

```html
<main>
  <section>
    <article>
    </article>
  </section>
</main>
```

An `acticle` element commonly contain multiple elements that have related information.

## Indenting Nested Elements

Placing one HTML elements inside other HTML element called *nesting*. Nested elements should be indented with two white spaces.

## Images

You can add images to your website by using *self-closing* `img` tag. A tag for an element without a closing tag is known as a self-closing tag.

### Images `src` attribute

HTML *attributes* are special words used inside the opening tag of an element to control the element's behavior. The `src` attribute in an `img` element specifies the image's URL.

```html
<img src="https://cdn.freecodecamp.org/curriculum/cat-photo-app/relaxing-cat.jpg" />
```

### Images `alt` attribute

All `img` elements should have an `alt` attribute. The `alt` attribute's text is used for screen readers to improve accessibility and is displayed if the image fails to load.

```html
<img src="https://cdn.freecodecamp.org/curriculum/cat-photo-app/relaxing-cat.jpg" alt="A cute orange cat lying on its back"/>
```

## Anchor

You can link to another page with the anchor (`a`) element. A link's text must be placed between the opening and closed tags of an anchor element.

```html
<a href='https://freecodecamp.org'>click here</a>
```

You can turn any text into a link, such as the text inside of a `p` element.

```html
<p>I think <a href="http://www.freecodecamp.org">freeCodeCamp</a> is great.</p>
```

### Anchor's `target` attribute

You can add a `target` attribute with the value `_blank` to the anchor element's opening tag, so that link opens in a new tab.

```html
<a href="http://www.freecodecamp.org" target="_blank">freeCodeCamp</a>
```

### Image as a link

You can turn other types of content into a link by wrapping it in anchor tags, say image element.

```html

<a href="https://freecatphotoapp.com"><img src="https://cdn.freecodecamp.org/curriculum/cat-photo-app/relaxing-cat.jpg" alt="A cute orange cat lying on its back"/></a>
```

## Section

When you add a lower rank heading element to the page, it's implied that you're starting a new subsection.

```html
<section>
  <h2>Cat Lists</h2>

</section>
```

## Unordered list

Unordered lists can be added using `ul` element.

Use list item (`li`) elements to create items in a list.

```html
<ul>
  <li>cat nip</li>
  <li>laser pointers</li>
  <li>lasagna</li>
</ul>
```

## Figure element

The `figure` element represents self-contained content and will allow you to associate an image with a caption.

A figure caption (`figcaption`) element is used to add a caption to describe the image contained within the `figure` element.

```html
<figure>
  <img src="https://cdn.freecodecamp.org/curriculum/cat-photo-app/lasagna.jpg" alt="A slice of lasagna on a plate.">
  <figcaption>Cats love lasagna.</figcaption>
</figure>
```

## Emphasizing a word

You can emphasize a word by wrapping it in an emphasis `em` element. By default it make it appeared as an *italic*.

```html
  <figcaption>Cats <em>love</em> lasagna.</figcaption>
```

## Ordered list

The code for an ordered list )`ol`) is similar to an unordered list, but list items in an ordered list are numbered when displayed.

```html
<ol>
 <li>flea treatment</li>
 <li>thunder</li>
 <li>other cats</li>
</ol>
```
  
## Strong importance of a word

The `strong` element is used to indicate that some text is of strong importance or urgent. By default the word is appeared in **bold** typeface.

```html
<figcaption>Cats <strong>hate</strong> other cats.</figcaption>
```

## A web form

You can use a web form to collect information from users with the help from `form` element.

The `action` attribute indicates where form data should be sent.

```html
<form action="https://freecatphotoapp.com/submit-cat-photo">

</form>
```

## Input elements

A self-closing `input` element allows you several ways to collect data from a web form.

There are many kinds of inputs you can create using the `type` attribute:

- `text`: for creating a text field
- `password`: for creating a password field
- `file`: selecting a file in the filesystem 

### Name attribute

In order for a form's data to be accessed by the location specified in the `action` attribute, you must give the input field a `name` attribute and assign it a value to represent the data being submitted. 

```html
<form action="https://freecatphotoapp.com/submit-cat-photo">
	<input type="text" name="catphotourl">
</form>
```

### Placeholder attribute

Placeholder text is used to give people a hint about what kind of information to enter into an input. Use `placeholder` attribute for setting this.

```html
<form action="https://freecatphotoapp.com/submit-cat-photo">
	<input type="text" name="catphotourl" placeholder="cat photo URL">
</form>
```

### Required attribute

To prevent a user from submitting your form when required information is missing, you need to add the `required` attribute to an `input` element. There's no need to set a value to the `required` attribute.

```html
<form action="https://freecatphotoapp.com/submit-cat-photo">
	<input type="text" name="catphotourl" placeholder="cat photo URL" required>
</form>
```

## Button

Use the `button` element to create a clickable button.

The default behavior of clicking a form button without any attributes submits the form to the location specified in the form's `action` attribute.

```html
<form action="https://freecatphotoapp.com/submit-cat-photo">
	<input type="text" name="catphotourl" placeholder="cat photo URL" required>
	<button>Submit</button>
</form>
```

In order to avoid confusion and introduce clear intent, you can add the `type` attribute with the value `submit` to the `button`.

```html
<form action="https://freecatphotoapp.com/submit-cat-photo">
	<input type="text" name="catphotourl" placeholder="cat photo URL" required>
	<button type="submit">Submit</button>
</form>
```

## Radio buttons

You can use radio buttons for the questions where you want only one answer out of multiple options.

```html
<input type="radio"> Indoor
```

### Label

`label` elements are used to help associate the text for an `input` element with the `input` element itself. Thus clicking the text also select the corresponding radio button.

```html
<label><input type="radio"> Indoor</label>
```

### id attribute

The `id` attribute is used to identify specific HTML elements. Each `id` attribute's value must be unique from all other `id` values for the entire page.

```html
<label><input id="indoor" type="radio"> Indoor</label>
```

### Grouping radio buttons

To make it so selecting one radio button automatically deselects the other, both buttons must have a `name` attribute with the same value.

```html
<label><input id="indoor" name="indoor-outdoor" type="radio"> Indoor</label>
<label><input id="outdoor" name="indoor-outdoor" type="radio"> Outdoor</label>
```

### Radio button value attribute

The form data for the button is based on its `name` and `value` attributes. If radio buttons do not have a `value` attribute, the form data will include `{name}=on`, which is not useful when you have multiple buttons.

You shall specify `value` attribute for each of the radio buttons that share the same `name` attribute.

```html
<label><input id="indoor" type="radio" name="indoor-outdoor" value="indoor"> Indoor</label>
<label><input id="outdoor" type="radio" name="indoor-outdoor" value="outdoor"> Outdoor</label>
```

## Fieldset

The `fieldset` element is used to group related inputs and labels together in a web form. `fieldset` elements are *block-level elements*, meaning that they appear on a new line.

```html
<fieldset>
  <label><input id="indoor" type="radio" name="indoor-outdoor" value="indoor"> Indoor</label>
  <label><input id="outdoor" type="radio" name="indoor-outdoor" value="outdoor"> Outdoor</label>
</fieldset>
```

### Fieldset Legend

The `legend` element acts as a caption for the content in the `fieldset` element. It gives users context about what they should enter into that part of the form.

```html
<fieldset>
  <legend>Is your cat an indoor or outdoor cat?</legend>
  <label><input id="indoor" type="radio" name="indoor-outdoor" value="indoor"> Indoor</label>
  <label><input id="outdoor" type="radio" name="indoor-outdoor" value="outdoor"> Outdoor</label>
</fieldset>
```

## Checkboxes

Forms commonly use checkboxes for questions that may have more than one answer.

```html
<fieldset>
  <legend>What's your cat's personality?</legend>
  <input id="loving" type="checkbox"> Loving
</fieldset>
```

There is a way to associate an `input` element's text with the element itself. You can nest the text within a `label` element and add a `for` attribute with the same value as the `input` element's `id` attribute.

```html
<fieldset>
  <legend>What's your cat's personality?</legend>
  <input id="loving" type="checkbox"> <label for="loving">Loving</label>
</fieldset>
```

For the sake of uniting selection for further processing by the web server you shall add `name` attribute with the same value for the checkboxes that related to each other.

```html
<fieldset>
  <legend>What's your cat's personality?</legend>
  <input id="loving" type="checkbox" name="personality"> <label for="loving">Loving</label>
  <input id="lazy" type="checkbox" name="personality"> <label for="lazy">Lazy</label>
</fieldset>
```

Form data for selected checkboxes are `name`/`value` attribute pairs. While the `value` attribute is optional, it's best practice to include it with any checkboxes or radio buttons on the page.

```html
<fieldset>
  <legend>What's your cat's personality?</legend>
  <input id="loving" type="checkbox" name="personality" value="loving"> <label for="loving">Loving</label>
  <input id="lazy" type="checkbox" name="personality" value="lazy"> <label for="lazy">Lazy</label>
</fieldset>
```

## Default selection of radio button or checkbox element

In order to make a checkbox checked or radio button selected by default, you need to add the `checked` attribute to it. There's no need to set a value to the `checked` attribute.

```html
<fieldset>
  <legend>What's your cat's personality?</legend>
  <input id="loving" type="checkbox" name="personality" value="loving" checked> <label for="loving">Loving</label>
  <input id="lazy" type="checkbox" name="personality" value="lazy"> <label for="lazy">Lazy</label>
</fieldset>
```

## Title

The `title` element determines what browsers show in the title bar or tab for the page. The element is nested inside the `head` tag.

```html
<head>
  <title>CatPhotoApp</title>
</head>
```

## The language of the page

To specify the language of the page, add two-letter language code as a value to the `lang` attribute of the `html` element.

```html
<html lang="en">
</html>
```

## Doctype

All pages should begin with `<!DOCTYPE html>`. This special string is know as a *declaration* and ensures the browser tires to meet industry-wide specifications.

```html
<!DOCTYPE html>
<html lang="en">
</html>
```

## Meta tags

You can set browser behavior by adding self-closing `meta` elements in the `head`, like `<meta attribute="value">.

For example, you can tell the browser how to encode characters for the page using `charset`  meta tag:

```html
<head>
  <meta charset="utf-8">
</head>
```

## Project files

- [index.html](basichtml/index.html.md)
- [site screenshot](basichtml/catphotoapp.png)
