# Lab Zero Guides
Ahoy! You are welcome to access Lab Zero's guides for our best practices for processes, playbooks, languages and tools.

**If this is your first time here we recommend checking out the [Github Pages site](https://labzero.github.io/guides) or starting with [index.md](index.md).**

## This README

This README.md describes how to write for and update the Lab Zero Guides site.

The Lab Zero Guides site is a Github Pages site.  It is automatically generated from the Markdown files in this (the guides) repository.

This README file will **not** show in the Github Pages site.  The `index.md` is shown instead.  Please see `index.md` for the root page of the site.

## Writing

When adding a new page simple create a new `.md` file!  Then you can proceed to write your article.  When you're ready add a link on the main `index.md` page.

After you're done open a PR.  Once the PR is merged it will automatically show up on the site (~3min).  Please double-check that it looks correct.

### Markdown

Markdown pages here use kramdown + some Jekyll & theme based enhancements.  Kramdown is very similar to Github flavored markdown but there are some small differences like:

* URLs are not automatically converted to links
* Links to a specific part of a page (e.g. `#heading-1`) must be in lower case.  (GFM allows mixed case)
* You can automatically generate a Table of Contents for a long page. (see below)

The first h1 or `#` will automatically become the page title.  You can override this with some `headmatter` (see that section below).

#### Links

Use root relative links to other pages.  Don't use github based links.  In general internal links should start with `/`, not `http`.  External links should start with `https`

**Don't**
```md
- [How to Write User Stories](https://github.com/labzero/guides/blob/master/process/how_we_write_user_stories.md)
- [Our Website](labzero.com)
```

Do:
```md'
- [How to Write User Stories](/process/how_we_write_user_stories.md)
- [Our Website](https://labzero.com)
```

#### Images

* Place images in assets/images
* Reference them using their root relative URL.
* As with links, don't use the github or full site name

Don't:
```
https://github.com/labzero/guides/blob/master/assets/images/lz-logo.svg
```

Do:
```
assets/images/lz-logo.svg
```

#### file naming

Any file named with the extension `.md` or `.html` is automatically picked up and you can link to it.

#### Table of Contents

You can have Jekyll automatically generate a table of contents for you.  Where you want the TOC add the following markdown:

```md
* list to be populated with toc
{:toc}
```

## Technology

This a Github Pages site built with Github's automatic Jekyll setup.

In short you're looking at:

github-pages + Jekyll + hydejack (theme) + kramdown (md parser)

### Deployment

Deployment is automatic when a new commit is merged to the master branch.

### Config

Most of the config lives in [_config.yml](/_config.yml).  Let's try to keep config specific comments there.

### Running the site locally

This is not supported.  Github has instructions for doing this but we haven't set the repo up for it.  (It may add more complication than most users of this repo would prefer.)
