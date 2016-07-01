# SASS code guide

Standards for developing silky-smooth SASS code.


## Use vanilla CSS code guide

This page is about Sass specific stuff, but you should use the regular [CSS formatting guidelines](css-code-guide.md) as a basis.


## File organization

* Fundamental styles like resets, and global utility partials like mixins and variables go in ```sass/global/```.
* Individual or logical groups of mixins are separated into their own files in `sass/global/mixins/`.
* Styles related to components/modules/views go in ```sass/components/```.
* Sass and CSS from other projects goes in ```sass/vendor/```.

```
sass/
├── application.scss
├── global/
|   ├── _mixins.scss
|   ├── _variables.scss
|   ├── _normalize.scss
|   ├── _scaffolding.scss
|   └── mixins/
|       ├── _my-mixin.scss
|       └── _my-other-mixin.scss
├── components/
|   ├── _btn.scss
|   ├── _list.scss
|   ├── _nav.scss
|   ├── _thumbnail.scss
└── vendor/
    └── _jquery.ui.core.scss
```

### Application stylesheet

All files get compiled into the ```application.scss``` stylesheet, and should be scoped accordingly.  
The application Sass file serves as a "table of contents" and the ```@import``` directives should be listed with vendor dependencies first, then author dependencies and core stylesheets, then components and utility classes, and finally [shame](#shame).  
Organize the components imports in a manner that makes sense, in other words, group components with the component they extend or inherit from.

```css
/* Vendor dependancies */
@import "compass";

/* Authored Dependencies */
@import "global/variables";
@import "global/mixins";

/* Core styles */
@import "global/normalize";
@import "global/scaffolding";

/* Components */
@import "components/btn";
@import "components/list";
@import "components/nav";
@import "components/thumbnail";

/* Utility classes */
@import "global/utilities";

/* Shame */
@import "shame";
```

The dependencies like Compass, variables, and mixins generate no compiled CSS at all, they are purely code dependancies. Listing the core styles next means that more specific "components", which come after, have the power to override patterns without having a specificity war.

### Mixins

The `_mixins.scss` file serves as a T.O.C. of the individual mixin files. This allows separation of mixins into logical groupings and is easier to maintain.

```css

/* Mixins */

@import "mixins/my-mixin.scss";
@import "mixins/my-other-mixin.scss";
@import "mixins/another-mixin.scss";
@import "mixins/some-mixins.scss";

```


### Partials are named _partial.scss

This is a common naming convention that indicates this file isn't meant to be compiled by itself. It likely has dependancies that would make it impossible to compile by itself. Use dashes in the "actual" filename though, like ```_dropdown-menu.scss```.


## SCSS syntax instead of SASS syntax
Use [SCSS (Sassy CSS) Syntax](http://thesassway.com/articles/sass-vs-scss-which-syntax-is-better) when writing your code instead of the [SASS (Indented) Syntax](http://thesassway.com/articles/sass-vs-scss-which-syntax-is-better).

## Code structure

```@extends``` and ```@includes``` are likely to be overwritten by future elements, placing them at the top of the property list calls them out and avoids the beginning of a [specificity war](http://www.stuffandnonsense.co.uk/archives/css_specificity_wars.html).

* ```@extends``` should be grouped together at the top of the selector.
* ```@includes``` should be grouped together after ```@extends```.
* Regular styles for the current selector should be after ```@includes```.
* Nested selectors appear last.
* Nested selectors using ```&``` should appear above child (```>```) nested selectors.

```scss
.weather {
  @extends %module; 
  @include transition(all 0.3s ease);
  background-color: $sky-light;
  &.selected {
    color: #89c;
  }
  > h3 {
    border-bottom: 1px solid #fff;
    @include transform(rotate(90deg));
  }
}
```

### @extend
Be cautious when using ```@extend``` in a way that causes unseemly, and unnecessary CSS bloat.  
Usually, you'll want to only use ```@extend``` with [placeholders](http://8gramgorilla.com/mastering-sass-extends-and-placeholders/).


## All vendor prefixes use @mixins

Vendor prefixes are a time-sensitive thing. As browsers update over time, the need for them will fall away. You can update mixins (or the libraries you use will update) to reflect those changes. Even if the mixin ends up being a one-liner, that's OK.  
The only time you shouldn't @mixin a vendor prefix is when it's super proprietary, unlikely to be standardized as is, and so including other vendor prefixes or the non-prefixed version is likely to cause more harm that good. For example, things like ```-webkit-line-clamp``` or ```-ms-content-zoom-chaining```.


## Limit nesting to 3 levels and 50 lines

Nesting selectors more than three levels deep and the code is at risk of being to reliant on HTML structure, overly-specific and difficult to understand.

```scss
.weather {
  .module {
    > h3 {
      ...
    }
  }
}
```

50 lines is reasonable length for keeping an entire block on a code editor screen without having to scroll.

```scss
1.   .weather {
2.     .module {
3.       > h3 {

...

48.      }
49.    }
50.  }
51.
52.  .widget { ... }
```


## Class (Component) naming conventions

* Adhere to the general CSS principles of [Human readable](https://github.webapps.rr.com/pages/ux/css-code-guide/#classes) class names.  
* For fans of [SMACSS](http://smacss.com): Don't use weird prefixes such as ```l-``` and ```is-``` ... they are a little overwrought.

**Those are the only hard and fast naming rules, what follows are some gentle guidelines...**  

When considering class names relative to *UI Components*, there is no perfect solution for all scenarios.  
*When it makes sense,* try to use class names and composition with prefixes that mirror the real inheritance structure of your Components. For example, if you have a ```Button``` UI Component, you might create other extending Components using appropriate class names like so:
```html
<div class="btn">Basic Button</div>
<div class="btn btn-alert">Alert Button</div>
<div class="btn btn-alert btn-alert-flashing">Flashing Alert Button</div>
```
From the example above, you could reasonably assume that there's a ```Button``` base Component, which is extended by an ```Alert Button``` Component, which *may* in turn be extended by a ```Flashing Alert Button```.  
But, there is no way to know for sure how Components are related *just* by their class names alone, so, above is a good starting point to follow, when appropriate; however, you should always: 

> Strive to maintain semantics, but don't sacrifice pragmatism.

So, don't worry too much if you encounter the example below where ```.btn-label``` isn't actually a ```Label Button``` that extends ```Button```, but rather a ```Label``` within a ```Button```. The surrounding markup should be enough for the developer to figure it out with their own common sense.

```html
<div class="btn">
   <div class="btn-label">The Label</div>
</div>
```

## Compass

[Use it!](http://compass-style.org/)
In general, it's preferable to use Compass functions over home-grown solutions.


## Variablize everything

* Variablize all colors.
* Numbers (other than 0 or 100%) with strong meaning or frequent use should be variables.
* Use hyphens (```-```) in variable names.
* Name variables based on what they represent, not their values, e.g. ```$text-size-large``` instead of ```$text-size-24```.
* 
Colors, fonts, and base measurements are all great candidates for variables.  
If you find yourself writing a number other than 0 or 100% more than once, make it a variable.

```scss
/* .../global/_variables.scss */

$sky: #0088ce;
$text-color: $sky;
$rounded-corners: 6px;
```

* Most variables should be stored in the ```_variables.scss``` partial; however, it's acceptable to define component specific variables in the component files.
* In this case, the variables should be stored at the top of the file.

```scss
/* .../components/btn.scss */

$btn-width: 10px;
$btn-color: $text-color-secondary;

...

.btn {
  color: $btn-color;
  width: $btn-width;
}
```


## Comments

Try to stick with standard [CSS comments](https://github.webapps.rr.com/pages/ux/css-code-guide#comments), but you can use the Sass style (```//```) comments for trivial comments or quickly debugging.

```scss
.weather {
  background-color: $overcast;
  line-height: 0.6667em; // 24/36
  // display: inline-block;
  font-style: italic;
}
```

## Shame

In the application stylesheet, ```@import``` the ```_shame.scss``` file last.  
If you need to make a quick fix, you can do it here. Later when you have proper time, you can move the fix into the proper structure/organization.
[Read more...](http://csswizardry.com/2013/04/shame-css/)

```css
@import "compass";

...

@import "shame";
```

## SCSS Lint

[SCSS Lint](https://github.com/causes/scss-lint) is a great scss linting tool that can be configured to inform you when you don't adhere to these rules.
Included in this repo is an example `scss-lint.yml` configuration file which is already set up to enforce most of these guidelines.


----------

### Mahalo

General principles and [additional guides](https://github.webapps.rr.com/pages/ux/code-guides#the-guides).