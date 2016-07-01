# CSS code guide

Standards for developing buttery-smooth CSS code.



----------



## Table of contents

* [CSS](#css)
   * [Write valid CSS](#write-valid-css)
   * [No IDs](#no-ids)
   * [CSS syntax](#css-syntax)
   * [Shorthand](#shorthand)
   * [Declaration order](#declaration-order)
      * [Positioning properties](#positioning-properties)
      * [Width and height](#width-and-height)
      * [Vendor properties](#vendor-properties)
   * [Formatting exceptions](#formatting-exceptions)
      * [Rules with single declarations](#rules-with-single-declarations)
      * [Prefixed properties](#prefixed-properties)
   * [Human readable](#human-readable)
      * [Comments](#comments)
      * [Classes](#classes)
      * [Selectors](#selectors)
* [Additional guides](#m%C3%A8si)



----------



## CSS

### Write valid CSS

All CSS code should be valid CSS2.1 or CSS3+.  
Terminology used in this guide:

````css
.selector {
   property: "value";
}
````


### No IDs

There is a blanket-ban on IDs in CSS. There is literally no point in them, and they only ever cause harm. Everything that needs styling is done so without using IDs.

**:no_entry_sign: Don't:**

````css
#widget { ... }
````


### CSS Syntax

* When grouping selectors, keep individual selectors to a single line with no space after the commas.
* Include one space before the opening ```{``` of declaration blocks.
* Place closing ```}``` of declaration blocks on a new line.
* Quote attribute values in selectors, e.g., ```input[type="text"]```
* Each declaration should appear on its own line.
* Include one space after ```:``` in each declaration.
* End all declarations with a semi-colon.
* Comma-separated values should include a space after each comma.
* Use double-quotes around appropriate values, e.g., ```background-image: url("../hello.jpg");```
* Avoid specifying units for zero values, e.g., ```margin: 0;``` instead of ```margin: 0px;```
* Unit-less line-height is preferred, e.g., ```line-height: 1.5;``` instead of ```line-height: 1.5em;```
* Avoid RGB colors, RGBa is acceptable where needed.
* Preface floating point values with a leading zero.
* Lowercase all hex values, e.g.,```#fff``` instead of ```#FFF```
* Use shorthand hex values where available, e.g., ```#fff``` instead of ```#ffffff```

**:no_entry_sign: Don't:**

````css
.selector, .selector-secondary, .selector[type=text]{
   font-family: Helvetica,Arial,sans-serif;
   margin:0px 0px 15px;
   line-height:32px;
   color: rgb(0, 169, 224);
   background-color:rgba(0,0,0,.5);
   background-image: url(../hello.jpg);
   border:1px solid #FFFFFF
}
````

**:white_check_mark: Do:**

````css
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
````


### Shorthand

Use shorthand declarations when possible for the following properties:

* background
* border
* font
* list-style
* margin
* padding

````css
margin: 10px 34px 10px 100px;
border: 2px solid #fff;
````


### Declaration order

Properties should be organized alphabetically inside each block (with exceptions noted below).

**:no_entry_sign: Don't:**

````css
.selector {
   font-weight: normal;
   background-color: #000;
   font-family: helvetica, sans-serif;
   color: #fff;
}
````

**:white_check_mark: Do:**

````css
.selector {
   background-color: #000;
   color: #fff;
   font-family: helvetica, sans-serif;
   font-weight: normal;
}
````

#### Positioning properties

Positioning properties (top, right, bottom, left, z-index) should be grouped together outside of alphabetical ordering when paired with a specific type of positioning (relative, absolute, static):

````css
.selector {
   font-size: 1em;
   margin: 2px;
   position: absolute;
   top: 0;
   right: 0;
   bottom: 0;
   left: 0;
   z-index: 1;
}
````

#### Width and height

Where width and height are both declared, height should always follow width.

````css
.selector {
   display: none;
   text-align: center;
   width: 50%;
   height: 200px;
}
````

#### Vendor properties

When using vendor prefixed properties, properties should appear in alphabetical order directly before the respective un-prefixed declaration:

````css
.selector {
   float: left;
   -moz-text-shadow: 1px 3px 3px #000;
   -ms-text-shadow: 1px 3px 3px #000;
   -o-text-shadow: 1px 3px 3px #000;
   -webkit-text-shadow: 1px 3px 3px #000;
   text-shadow: 1px 3px 3px #000;
   visibility: hidden;
}
````


### Formatting exceptions

In some cases, it makes sense to deviate slightly from the default [syntax](#css-syntax).

#### Rules with single declarations

In instances where several rules are present with only one declaration each, consider removing new line breaks for readability and faster editing.

````css
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
````

#### Prefixed properties

When using vendor prefixed properties, indent each property such that the value lines up vertically for easy multi-line editing.

````css
.selector {
   -webkit-border-radius: 3px;
      -moz-border-radius: 3px;
           border-radius: 3px;
}
````


### Human readable

Code is written and maintained by people. Ensure your code is descriptive, well commented, and approachable by others.

#### Comments

* Section comments are separated from the previous block by two lines, and should have one following line of space.
* Prepend section headings with an equal sign (```=```), to make a _Find_ operation easier.

````css
.hello { ... }


/* ================================================================================ *\
   =Main
\* ================================================================================ */

.goodbye { ... }
````

* Section chunks are preceded by only one line of space.

````css
.hello { ... }

/* ==================== *\
   =Main Chunk
\* ==================== */

.goodbye { ... }
````
````css
.hello { ... }

/**
 * For longer, multiple line comments that need more room,
 * add a newline before and after the comment.
 * Leave one line of space before the next block.
 */

.goodbye { ... }
````

````css
/* Short comments: one line with no trailing space. */
.hello { ... }

.goodbye {
   color: #000; /* A short hint can also follow one property/value pair. */
}
````

Great code comments convey context or purpose and should not just reiterate a component or class name.

**:no_entry_sign: Don't:**

````css
/* Modal header */
.modal-header {
  ...
}
````

**:white_check_mark: Do:**

````css
/* Wrapping element for .modal-title and .modal-close */
.modal-header {
  ...
}
````


#### Classes

* Use class names that are as short as possible, but as long as necessary.
* Use meaningful names that describe what element(s) they style.
* Use lowercase and separate words with hyphens when naming selectors.
* Avoid underscores and camelCase.

**:no_entry_sign: Don't:**

````css
.t1-xr { ... }
.red { ... }
.comment_form { ... }
.progressBar { ... }
````

**:white_check_mark: Do:**

````css
.tweet { ... }
.important { ... }
.comment-form { ... }
.progress-bar { ... }
````


#### Selectors

* Use classes over generic element tags.
* Keep them short and limit the number of elements in each selector to three(ish).
* Scope classes to the closest parent when necessary (e.g., when not using prefixed classes).

**:no_entry_sign: Don't:**

````css
span { ... }
.page-container #stream .stream-item .tweet .tweet-header .username { ... }
.avatar { ... }
````

**:white_check_mark: Do:**

````css
.avatar { ... }
.tweet-header .username { ... }
.tweet .avatar { ... }
````



----------



#### Mèsi

General principles and [additional guides](https://github.webapps.rr.com/pages/ux/code-guides#the-guides).
