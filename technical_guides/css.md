# CSS Guide

## Overview
This is a living document shared by all developers at Lab Zero. We as developers at Lab Zero believe that following these principles produces higher quality software. It’s a pact that we share. Please read and add to it as we find things on our projects that we’d like to make standard for our engineering practice.

## Use a pre/post-processor
Use a preprocessor like [Sass](http://sass-lang.com/), or a set of postprocessors like [PostCSS](http://postcss.org/).

Store all colors, font families, font weights, and font sizes in variables.

Use variable-heavy math. Avoid magic numbers whenever possible (and comment when necessary). Store all variables in a separate file so you can see where it's possible to consolidate.

When using Sass, favor [mixins](https://sass-lang.com/documentation/at-rules/mixin/) over [placeholders/extends](https://sass-lang.com/documentation/style-rules/placeholder-selectors/). (A gzipped CSS file will cut down on the resulting additional filesize.)

## File structure
Keep variables, mixins, and utility classes (if applicable) in separate files so they can be imported at the top of your main stylesheet(s). You might even want to split your helper files into smaller ones for typography, colors, common measurements, etc.

Put rules for elements (without classes) underneath those import statements.

The rest of the rules are generally laid out in an order that matches what's closest to the top of the page, but it's not a hard-and-fast requirement.

## Use semantic classes, not presentational classes

Avoid using class names that include words like `left`, `bold`, `large` or `blue`, especially if they represent one-to-one mappings to single CSS properties.

Use class names that make use of words like `container`, `actions`, `group`, `active`, `disabled`, and other names that represent items or states in a user interface.

## Use [BEM](https://css-tricks.com/bem-101/) to avoid unnecessary nesting...
Attempt to keep nesting to a minimum. Except in the case of modifier classes affecting their children, strive for zero nesting if possible.

Despite the usefulness of BEM, there is no need to apply a class to every single element, especially buttons, links, table elements, or others that have a specific function. For example, `.links a` is as descriptive as `.links__link`.

If using a modifier class, also apply the class without the modifier to that element, e.g. `.block__element.block__element--modified`.

Keep element names as simple as possible. If you have rows inside a `.block__table`, prefer `.block__row` over `.block__table-row`.

## ...or, use [CSS Modules](https://github.com/css-modules/css-modules).
By having a one-to-one ratio of components to CSS files, you can usually eschew the "Block" portion of "Block-Element-Modifier", meaning you are free to use simple component-specific classes like `.section` without fear of conflicts.

You can still achieve a BEM-like class name appearance by specifying a `localIdentName` such as `[name]_[local]__[hash:base64:5]`.

You should still consider applying both non-modifier and modifier classes to elements, though. This can be accomplished using the CSS Modules-specific `composes` property. e.g.:

```css
.section {
  background: blue;
}

.sectionActive: {
  composes: section;
  color: red;
}
```

Using `sectionActive` will result in two classes being applied, e.g.: `Component_section__12345 Component_sectionActive__12345`.

## Favor mobile-first design

If your designer has given you desktop-only mockups, explain the importance and ubiquity of mobile devices. Bring up any potential difficulties from interactions only available via mouse gestures like hovering.

Media queries are good, but percentages and `max-width`s are better, since they eliminate the need for breakpoints.

Do not rely on any so-called "industry standard" media query breakpoints. Add a custom breakpoint for whenever an element begins to look awkward.

## Don't hide focus styling

Another thing to discuss with your designer is the lack of focus styling on inputs. The default focus outline might be garish, but you should not be completely hiding them in response. Ensure the focused element is easily discoverable by tabbing through your page.

## Use as few elements as possible

Don't create `<div>`-stew. Use pseudo-elements for decorative shapes, like arrows, complex borders, circles, etc.

## Headings
Use `<section>` elements wisely and you will be able to regularly reset your heading numbering back to `<h1>`.

Despite this, it is often wise to add classes to heading elements since they can easily become lower-level headings.

## Z-index
`z-index` is relative, which means any element that has a `z-index` will create a new base layer for anything inside it, allowing you to restart numbering. There is no need to use massive numbers like `100`, `2000`, etc. - single-digit increments will suffice.

Adding a comment to your `z-index` declaration will help explain the rationale behind it - what an element specifically needs to be above or underneath.

## !important
Only use `!important` to override inline styles applied by a JS library, with a comment explaining your rationale.

Otherwise, you can write a more specific selector and/or create a new class to override any other rules.

## Bootstrap et al
[Bootstrap](https://getbootstrap.com/) (and similar libraries like [Bulma](https://bulma.io/) or [Foundation](https://foundation.zurb.com/)) can provide a massive head-start for a project that's just starting out, but it's not the right tool for every job. 

### Pros
- Bootstrap helps you start fast
- Comes with a good, responsive grid system
- Great for prototypes
- Can be customized to better suit design/feature needs

### Cons
- Using Bootstrap in its entirety requires undoing a lot of its CSS
- If client has an established, in-depth style guide, do not use Bootstrap
- Some Bootstrap components require a rigid HTML structure, which might be at odds with what the designs specify

## Use Autoprefixer
[Autoprefixer](https://github.com/postcss/autoprefixer) should be used regardless of whether you're using other PostCSS features or not.

## Icons
In most cases, it's more "semantic" to use `<button>` or `<a>` elements rather than `<img>` elements when using icons. You'll need to use a background image and hide the text using an image replacement hack, like [the one provided by Scut](https://ramseyinhouse.github.io/scut/image-replace.html).

Prefer SVGs over PNGs. Bother your designer if they haven't provided vector-based assets.

Prefer SVGs over icon fonts, since you will inevitably need multicolor icons, it is easier to manage separate SVG files.

Inline SVGs inside CSS for fewer HTTP requests. [Here's a Sass solution](https://github.com/franzheidl/sass-inline-svg), or for Webpack, use [URL Loader](https://github.com/webpack-contrib/url-loader) along with [CSS Loader](https://github.com/webpack-contrib/css-loader).

## Units
Pixel measurements are fine - they're great for heights, padding, margin, and other non-responsive box-model-related measurements. Remember to store these measurements as variables as much as is reasonable.

`rem`s and `em`s are useful for type-related measurements, including `font-size`, `line-height`, and some margins.

## Linting

Use [Stylelint](https://stylelint.io/) along with [stylelint-config-standard](https://github.com/stylelint/stylelint-config-standard).

## Resources
- [https://developer.mozilla.org/en-US/docs/Web/CSS](https://developer.mozilla.org/en-US/docs/Web/CSS)
- [https://caniuse.com](https://caniuse.com)
- [https://css-tricks.com/](https://css-tricks.com/)
- [https://developer.mozilla.org/en-US/docs/Learn/Accessibility/CSS_and_JavaScript](https://developer.mozilla.org/en-US/docs/Learn/Accessibility/CSS_and_JavaScript)
