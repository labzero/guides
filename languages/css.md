# CSS Guide

## Overview
This document is a living doc shared by all developers at Lab Zero.  We as developers at Lab Zero believe that following these principles produces higher quality software.  It’s a pact that we share.  Please read and add to it as we find things on our projects that we’d like to make standard for our engineering practice.

## Use Sass
Even if it's a small project, you should be preprocessing your code using [Sass](http://sass-lang.com/).

Store all colors, font families, font weights, and font sizes in variables.

Use variable-heavy math. Avoid magic numbers whenever possible (and comment when necessary). Store all variables in a separate file so you can see where it's possible to consolidate.

Use [Scut](https://davidtheclark.github.io/scut/) for common utilities and tricks.

Favor [placeholders/extends](http://sass-lang.com/documentation/file.SASS_REFERENCE.html#placeholders) over [mixins](http://sass-lang.com/documentation/file.SASS_REFERENCE.html#mixins).

## File structure
Keep variables, mixins, and placeholders, and utility classes (if applicable) in separate files so they can be imported at the top of your main stylesheet(s).

Put rules for elements (without classes) underneath those import statements.

The rest of the rules are generally laid out in an order that matches what's closest to the top of the page, but it's not a hard-and-fast requirement.

## Favor mobile-first design

If your designer has given you desktop-only mockups, explain the importance and ubiquity of mobile devices. Bring up any potential difficulties from interactions only available via mouse gestures like hovering.

Media queries are good, but percentages and `max-width`s are better, since they eliminate the need for breakpoints.

Do not rely on any so-called "industry standard" media query breakpoints. Add a custom breakpoint for whenever an element begins to look awkward.

## Use as few elements as possible

Don't create `<div>`-stew. Use pseudo-elements for decorative shapes, like arrows, complex borders, circles, etc.

## Use semantic classes, not presentational classes

Avoid using class names that include words like `left`, `bold`, `large` or `blue`, especially if they represent one-to-one mappings to single CSS properties.

Use class names that make use of words like `container`, `actions`, `group`, `active`, `disabled`, and other names that represent items or states in a user interface.

## Use [BEM](https://css-tricks.com/bem-101/) to avoid unnecessary nesting.
There is no need to apply a class to every single element, especially buttons, links, table elements, or others that have a specific function.

If using a modifier class, also apply the class without the modifier to that element, e.g. `.block__element.block__element--modified`.

Keep element names as simple as possible. If you have a `.block__table`, prefer `.block__row` over `.block__table-row`.

[Sass 3.3+ has BEM syntax support](http://visuellegedanken.de/2014-03-29/using-bem-syntax-with-sass-3-3/).

## Z-index
`z-index` is relative, which means any element that has a `z-index` will create a new base layer for anything inside it, allowing you to restart numbering. There is no need to use massive numbers like `100`, `2000`, etc - single-digit increments will suffice.

CSS comments will help explain the rationale behind a specific z-index - what specifically an element needs to on top of or underneath.

## !important
Only use `!important` to override inline styles applied by a JS library, with a comment explaining your rationale.

Otherwise, you can write a more specific selector and/or create a new class to override any other rules.

## Modernizr

[Modernizr](https://modernizr.com/) is helpful if you are creating HTML5 elements and need to support IE8 or below. Otherwise, consider using graceful degradation rather than feature detection when writing your CSS.

## Bootstrap
[Bootstrap](http://getbootstrap.com/) (and similar libraries like [Foundation](http://foundation.zurb.com/)) can provide a massive head-start for a project that's just starting out, but it's not the right tool for every job. 

### Pros
- Bootstrap helps you start fast
- Comes with a good, responsive grid system
- Great for prototypes

### Cons
- Using Bootstrap in its entirety requires undoing a lot of its CSS
- If client has an established, in-depth style guide, do not use Bootstrap
- Some Bootstrap components require a rigid HTML structure, which might be at odds with what the designs specify

## Headings
Use `<section>` elements wisely and you will be able to regularly reset your heading numbering back to `<h1>`.

Despite this, it is wise to add classes to heading elements since they can easily become subheadings.

## Use Autoprefixer
Do not use Compass's vendor prefix mixins - [Autoprefixer](https://github.com/postcss/autoprefixer) takes care of all vendor prefixes.

## Icons
Prefer SVGs over PNG sprites (again, no need for Compass). Bother your designer if they haven't provided vector-based assets.

Prefer SVGs over icon fonts, since you will inevitably need multicolor icons, and it is easier to manage separate SVG files.

[Inline SVGs inside CSS](https://github.com/franzheidl/sass-inline-svg) for fewer HTTP requests.

## Units
Pixels are not the devil - they're great for heights, padding, margin, and other non-responsive box-model-related measurements. Remember to store these measurements as variables as much as is reasonable.

`rem`s are useful for type-related measurements, including `font-size`, `line-height`, and some margins.

## Resources
- https://developer.mozilla.org/en-US/docs/Web/CSS
- http://caniuse.com
- https://css-tricks.com/
