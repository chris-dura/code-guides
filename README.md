# General principles

General principles for developing flexible, durable and sustainable code.

## Golden rule

> All code in any code base should look like a single person typed it, no matter how many people contributed.

This means strictly enforcing these agreed upon guidelines at all times. For additions or contributions, please [file an issue on GitLab](https://gitlab.spectrumxg.com/dura/code-guides).

## Clean up

Working on a development team is kind of like having roommates... messy roommates... every so often, you're going to have to wash the dishes that _they_ left in the sink while you were out of town.  
  
Generally, you should leave _**all**_ code better off than when you started, so if you find code that violates any of the rules in these guides while completing your story... clean it up. And, *if practical*, clean up commits should be separate from story commits.

## Human readable
Code is written and maintained by people. Ensure your code is descriptive, well commented, and approachable by others.

Great code comments convey context or purpose. Be sure to write in complete sentences for larger comments and succinct phrases for general notes.

## Indentation

Soft tabs of four (4) spaces should be used to indent code.

## TODOs

Opinions vary, but this can be a very pragmatic way of flagging non-urgent code issues.  
The next time someone touches that file, they can consider opportunistically addressing the refactor.  
TODO comments should start with ```TODO``` and include the author of the comment:

````javascript
// TODO(ekapowski): Stop referring to this private field in subclasses.
var _foo = bar;
````

## Sentence case

Always write copy, including headings and code comments, in [sentence case](http://en.wikipedia.org/wiki/Letter_case#Usage). In other words, aside from titles and proper nouns, only the first word should be capitalized.

## Editor preferences

Set your editor to the following settings to avoid common code inconsistencies and dirty diffs:

- Use soft-tabs set to four spaces.
- Trim trailing white space on save.
- Set encoding to UTF-8.
- Add new line at end of files.

Consider documenting and applying these preferences to your project's [.editorconfig](.editorconfig) file.

## The guides

* [HTML code guide](html-code-guide.md)
* [CSS code guide](css-code-guide.md)
* [SASS code guide](sass-code-guide.md)
* JavaScript code guide

----------

### Regards
Heavily inspired by [mdo](http://codeguide.co), the [GitHub Styleguide](https://github.com/styleguide) and [css-tricks](http://css-tricks.com/sass-style-guide/).