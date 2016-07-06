# HTML code guide

Standards for developing baby-smooth HTML code.

## Write valid HTML

All HTML code should be valid HTML5.  
Terminology used in this guide:

````html
<element attribute="value"></element>
````

## HTML5 doctype

Enforce standards mode in every browser possible with this simple doctype at the beginning of every HTML page.

````html
<!doctype html>
````

## Language attribute

Specify the `lang` attribute on the `root` html element, giving the document's language.

````html
<!doctype html>
<html lang="en-us">
  <head>
  </head>
</html>
````

## IE compatibility mode

Unless circumstances require otherwise, it's most useful to instruct IE to use the latest supported mode with **edge mode**.

````html
<!doctype html>
<head>
  <meta http-equiv="X-UA-Compatible" content="IE=Edge">
</head>
````

## Character encoding

Quickly and easily ensure proper rendering of your content by declaring an explicit character encoding.

````html
<head>
  <meta charset="utf-8">
</head>
````

## CSS and JavaScript includes

Typically there is no need to specify a type when including CSS and JavaScript files as `text/css` and `text/javascript` are their respective defaults.

````html
<!-- External CSS -->
<link rel="stylesheet" href="code-guide.css">

<!-- In-document CSS -->
<style>
  /* ... */
</style>

<!-- JavaScript -->
<script src="code-guide.js"></script>
````

## Pragmatism over semantics

Strive to maintain HTML standards and semantics, but don't sacrifice pragmatism. Use the least amount of markup with the fewest intricacies whenever possible.

## Indentation

Nested elements should be indented once.

**:no_entry_sign: Bad example:**

````html
<!doctype html>
<html>
<head>
<title>Page title</title>
</head>
<body>
<img src="images/company-logo.png" alt="Company">
<h1 class="hello-world">Hello, world!</h1>
</body>
</html>
````

**:white_check_mark: Good example:**

````html
<!doctype html>
<html>
   <head>
      <title>Page title</title>
   </head>
   <body>
      <img src="images/company-logo.png" alt="Company">
      <h1 class="hello-world">Hello, world!</h1>
   </body>
</html>
````

## Elements

* Semantic element tags should be used whenever possible.
* Element names should be lowercase.
* Don't omit optional closing tags, e.g. `</li>` or `</body>`.
* Don't include trailing slash in self-closing elements, the HTML5 spec says they're optional.

**:no_entry_sign: Bad example:**

````html
<div id="header">This Is My Header</div>
<div id="footer">
  <img src="hello.jpg" /><br />
  <hr/>
  All rights reserved.
</div>
````

**:white_check_mark: Good example:**

````html
<header>This Is My Header</header>
<footer>
   <img src="hello.jpg"><br>
   <hr>
   <p>All rights reserved.</p>
</footer>
````

## Attributes

* Attributes should be lowercase.
* Always use double quotes, never single quotes.
* Boolean attributes should be used without quoted values to avoid redundancy.

**:no_entry_sign: Bad example:**

````html
<p class='line note' Data-Attribute=106>This is my paragraph of special text.</p>
<audio src='file.mp3' autoplay='autoplay'></audio>
````

**:white_check_mark: Good example:**

````html
<p class="line note" data-attribute="106">This is my paragraph of special text.</p>
<audio src="file.mp3" autoplay></audio>
````

### Attribute order

HTML attributes should come in this particular order for easier reading of code. Attributes within the wildcard sub-groupings, and attributes not listed below, should appear in alphabetical order, e.g. `aria-label` after `aria-hidden`.

* `class`
* `id`, `name`
* `for`, `href`, `src`, `type`, `value` 
* `alt`, `title`
* `role`, `aria-*`
* `data-*`
* `ng-*`

Classes make for great reusable components, so they come first. Ids are more specific and should be used sparingly (e.g., for in-page bookmarks), so they come second.

````html
<a class="..." id="..." href="#" data-toggle="modal">Example link</a>

<input class="form-control" type="text">

<img src="..." alt="..." ng-if="...">
````

## Reducing markup
Whenever possible, avoid superfluous parent elements when writing HTML. Many times this requires iteration and refactoring, but produces less HTML.

**:no_entry_sign: Not great example:**

````html
<span class="avatar">
  <img src="...">
</span>
````

**:white_check_mark: Better example:**
```html
<img class="avatar" src="...">
```

## Comments

Keep line-length to a sensible maximum, e.g. 60 columns.

````html

<!-- Section comment block
     =================================================== -->

<div class="hello"><div>

<!-- Sub-section comment block
     ===================== -->

<div class="goodbye"></div>

<!--
 For longer, multiple line comments that need more room,
 add a newline before and after the comment.
 Leave one line of space before the next block.
-->

<!-- Basic comments: one line with no trailing space. -->

````

Because all closing tags look the same, commenting the closing tags can be useful. A closing slash followed by a descriptor of the opening tag should be used.

````html
<div class="hello">
   <div class="goodbye"></div>
</div><!-- /.hello -->
````

## JavaScript generated markup

:no_entry_sign: Writing markup in a javascript file makes the content harder to find, harder to edit, and less performant. **Avoid it**.

## Linting

### [HTMLHint](http://htmlhint.com/)

HTMLHint is a fairly capable linting tool for your markup. It doesn't enforce every rule detailed here, but it's better than nothing.

See [`.htmlhintrc`](.htmlhintrc) for a sample configuration.

----------

### Obrigado

General code principles and [additional guides](README.md#the-guides).