# HTML code guide
Standards for developing baby-smooth HTML code.



----------



## Table of contents


* [HTML](#html)
   * [Write valid HTML](#write-valid-html)
   * [HTML5 doctype](#html5-doctype)
   * [HTML indentation](#html-indentation)
   * [Pragmatism over semantics](#pragmatism-over-semantics)
   * [Elements](#elements)
   * [Attributes](#attributes)
      * [Attribute order](#attribute-order)
   * [Comments](#html-comments)
   * [JavaScript generated markup](#javascript-generated-markup)
* [Additional guides](#obrigado)



----------

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


















### HTML indentation

* Nested elements should be indented once.

**:no_entry_sign: Don't:**

````html
<!DOCTYPE html>
<html>
<head>
<title>Page title</title>
</head>
<body>
<img src='images/company-logo.png' alt='Company' />
<h1 class='hello-world'>Hello, world!</h1>
</body>
</html>
````

**:white_check_mark: Do:**

````html
<!DOCTYPE html>
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


### Pragmatism over semantics

Strive to maintain HTML standards and semantics, but don't sacrifice pragmatism. Use the least amount of markup with the fewest intricacies whenever possible.


### Elements

* Semantic element tags should be used whenever possible.
* Element names should be lowercase.
* Elements should always have a closing tag.
* Self-closing tags should have a space preceding the closing slash (```/```).

**:no_entry_sign: Don't:**

````html
<div id="header">This Is My Header</div>
<div id="footer">
  <img src="hello.jpg"/><br>
  All rights reserved.
</div>
````

**:white_check_mark: Do:**

````html
<header>This Is My Header</header>
<footer>
   <img src="hello.jpg" /><br />
   <p>All rights reserved.</p>
</footer>
````


### Attributes

* Attributes should be lowercase.
* Always use double quotes (```"```), never single quotes.
* Boolean attributes should be used without quoted values to avoid redundancy.

**:no_entry_sign: Don't:**

````html
<p class='line note' Data-Attribute=106>This is my paragraph of special text.</p>
<audio src="file.mp3" autoplay="autoplay"></audio>
````

**:white_check_mark: Do:**

````html
<p class="line note" data-attribute="106">This is my paragraph of special text.</p>
<audio src="file.mp3" autoplay></audio>
````

#### Attribute order

HTML attributes should come in this particular order for easier reading of code. Attributes within the wildcard sub-groupings, and attributes not listed below, should appear in alphabetical order, e.g. `aria-label` after `aria-hidden`.

* id
* class | name
* for | href | src | type | value | ...
* aria-*
* data-*
* ng-*

Such that your markup looks like:

````html
<a id="" class="" href="" aria-label="" data-modal="" ng-if="" >Example link</a>
<input id="" class="" name="" type="" value="" />
````


### HTML Comments

* Section comments are separated from the previous block by two lines, and should have one following line of space.
* Prepend section headings with an equal sign (```=```), to make a _Find_ operation easier.

````html
<div class="hello"><div>


<!-- ================================================================================ -->
<!-- =Main -->
<!-- ================================================================================ -->
 
<div class="goodbye"></div>
````

* Section chunks are preceded by only one line of space.

````html
<div class="hello"><div>

<!-- ==================== -->
<!-- =Main chunk -->
<!-- ==================== -->
 
<div class="goodbye"></div>
````

````html
<div class="hello"></div>

<!--
 For longer, multiple line comments that need more room,
 add a newline before and after the comment.
 Leave one line of space before the next block.
-->
 
<div class="goodbye"></div>
````

````html
<!-- Short comments: one line with no trailing space. -->
<div class="hello">
   <p>Hello, World!</p>
</div>
````

* Because all closing tags look the same, commenting the closing tags can be useful.  
* A closing slash followed by a descriptor of the opening tag should be used.

````html
<div class="hello">
   <div class="goodbye"></div>
</div><!-- /.hello -->
````


### JavaScript generated markup

:no_entry_sign: Writing markup in a javascript file makes the content harder to find, harder to edit, and less performant. Don't do it.



----------



#### Obrigado

General principles and [additional guides](https://github.webapps.rr.com/pages/ux/code-guides#the-guides).