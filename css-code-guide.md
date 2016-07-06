# CSS code guide

Standards for developing buttery-smooth CSS code.

## Write valid CSS

All CSS code should be valid CSS2.1 or CSS3+.  
Terminology used in this guide:

````css
.selector {
   property: "value";
}
````

## No IDs

There is a blanket-ban on IDs in CSS. There is literally no point in them, and they only ever cause harm. Everything that needs styling is done so without using IDs.

**:no_entry_sign: Bad example:**

```css
#widget { ... }
```


## CSS Syntax

* When grouping selectors, keep individual selectors to a single line with no space after the commas.
* Include one space before the opening brace of declaration blocks for legibility.
* Place closing braces of declaration blocks on a new line.
* Include one space after `:` for each declaration.
* Each declaration should appear on its own line for more accurate error reporting.
* End all declarations with a semi-colon. The last declaration's is optional, but your code is more error prone without it.
* Comma-separated property values should include a space after each comma.
* Preface floating point values with a leading zero for easier reading for humans, e.g. `-0.5` instead of `-.5`. 
* Lowercase all hex values. Lowercase letters are much easier to discern when scanning a document as they tend to have more unique shapes, e.g. `#fff` instead of `#FFF`.
* Use shorthand hex values where available, e.g. `#fff` instead of `#ffffff`.
* Avoid `rgb()` color declarations, `rgba()` is acceptable where needed.
* Use double-quotes around appropriate values to avoid having to escape single-quotes, e.g. `background-image: url("../hello.jpg");`
* Quote attribute values in selectors, e.g. `input[type="text"]`. They’re only optional in some cases, and it’s a good practice for consistency.
* Avoid specifying units for zero values, e.g. `margin: 0;` instead of `margin: 0px;`.
* Unit-less line-height is preferred, e.g. `line-height: 1.5;` instead of `line-height: 1.5em;`.

**:no_entry_sign: Bad example:**

```css
.selector, .selector-secondary, .selector[type=text]{
   font-family: Helvetica,Arial,sans-serif;
   margin:0px 0px 15px;
   line-height:32px;
   color: rgb(0, 169, 224);
   background-color:rgba(0,0,0,.5);
   background-image: url(../hello.jpg);
   border:1px solid #FFFFFF
}
```

**:white_check_mark: Good example:**

```css
.selector,
.selector-secondary,
.selector[type="text"] {
   font-family: Helvetica, Arial, sans-serif;
   margin: 0 0 15px;
   line-height: 1.5;
   color: #00a9e0;
   background-color: rgba(0, 0, 0, 0.5);
   background-image: url("../hello.jpg");
   border: 1px solid #fff;
}
```

## Shorthand

Use shorthand declarations when possible for the following properties:

* background
* border
* font
* list-style
* margin
* padding

```css
margin: 10px 34px 10px 100px;
border: 2px solid #fff;
```

## Declaration order

Properties should be organized alphabetically inside each block (with exceptions noted below).

**:no_entry_sign: Bad example:**

````css
.selector {
   font-weight: normal;
   background-color: #000;
   font-family: helvetica, sans-serif;
   color: #fff;
}
````

**:white_check_mark: Good example:**

````css
.selector {
   background-color: #000;
   color: #fff;
   font-family: helvetica, sans-serif;
   font-weight: normal;
}
````

## Vendor properties

When using vendor prefixed properties, properties should appear in alphabetical order directly before the respective un-prefixed declaration:

```css
.selector {
   float: left;
   -moz-text-shadow: 1px 3px 3px #000;
   -ms-text-shadow: 1px 3px 3px #000;
   -o-text-shadow: 1px 3px 3px #000;
   -webkit-text-shadow: 1px 3px 3px #000;
   text-shadow: 1px 3px 3px #000;
   visibility: hidden;
}
```


## Formatting exceptions

In some cases, it makes sense to deviate slightly from the default [syntax](#css-syntax).

### Rules with single declarations

In instances where several rules are present with only one declaration each, consider removing new line breaks for readability and faster editing.

```css
.span1 { width: 60px; }
.span2 { width: 140px; }
.span3 { width: 220px; }

.sprite {
   background-image: url("../img/sprite.png");
   display: inline-block;
   width: 16px;
   height: 15px;
}

.icon           { background-position: 0 0; }
.icon-home      { background-position: 0 -20px; }
.icon-account   { background-position: 0 -40px; }
```

### Prefixed properties

When using vendor prefixed properties, indent each property such that the value lines up vertically for easy multi-line editing.

```css
.selector {
   -webkit-border-radius: 3px;
      -moz-border-radius: 3px;
           border-radius: 3px;
}
```

## Comments

Use the general guidelines about writing [human readable](README.md#human-readable) code.

```css
/* Section comment block
   ------------------------------------------------------ */

.hello {
  ...
}

/* Sub-section comment block
   ------------------------ */

.goodbye {
  ...
}

/**
 * For longer, multiple line comments that need more room,
 * add a newline before and after the comment.
 * Leave one line of space before the next block.
 */

/* Basic comments: one line with no trailing space. */

.weather {
  background-color: $overcast;
  line-height: 0.6667em; /* 24/36 */
  /* display: inline-block; */
  font-style: italic;
}
```

Great code comments convey context or purpose and should not just reiterate a component or class name.

**:no_entry_sign: Bad example:**

```css
/* Modal header */
.modal-header {
  ...
}
```

**:white_check_mark: Good example:**

```css
/* Wrapping element for .modal-title and .modal-close */
.modal-header {
  ...
}
```

## Classes

* Use class names that are as short as possible, but as long as necessary.
* Use meaningful names that describe what element(s) they style.
* Use lowercase and separate words with hyphens when naming selectors.
* Avoid underscores and camelCase.

**:no_entry_sign: Bad example:**

```css
.t1-xr { ... }
.red { ... }
.comment_form { ... }
.progressBar { ... }
```

**:white_check_mark: Good example:**

```css
.tweet { ... }
.important { ... }
.comment-form { ... }
.progress-bar { ... }
```

## Selectors

* Use classes over generic element tags.
* Keep them short and limit the number of elements in each selector to three(ish).
* Scope classes to the closest parent when necessary (e.g. when not using prefixed classes).

**:no_entry_sign: Bad example:**

```css
span { ... }
.page-container #stream .stream-item .tweet .tweet-header .username { ... }
.avatar { ... }
````

**:white_check_mark: Good example:**

```css
.avatar { ... }
.tweet-header .username { ... }
.tweet .avatar { ... }
````


----------


### Mèsi

General principles and [additional guides](README.md#the-guides).
