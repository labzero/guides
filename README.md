# Lab Zero Guides
Ahoy! You are welcome to access Lab Zero's guides for our best practices for processes, playbooks, languages and tools.

**If this is your first time here we recommend checking out the [Github Pages site](https://guides.labzero.com) or starting with [index.md](index.md).**

## This README

This README.md describes how to write for and update the Lab Zero Guides site.  If you're here to see site content, **we recommend [visiting the site directly](https://guides.labzero.com)**.  If you're here to update or add a guide, *welcome*, you're in the right place :-)

The Lab Zero Guides site is a Github Pages site.  It is automatically generated from the Markdown files in this (the guides) repository.

This README file will **not** show in the Github Pages site.  The `index.md` is shown instead.  Please see `index.md` for the root page of the site.

## Writing

When adding a new page simply create a new `.md` file!  Then you can proceed to write your article.  When you're ready, add a link on the main `index.md` page.

After you're done open a PR.  Once the PR is merged it will automatically show up on the site (~3min).  Please double-check that it looks correct.

### Markdown

Markdown pages here use kramdown + some Jekyll & theme based enhancements.  Kramdown is very similar to Github flavored markdown but there are some small differences like:

* URLs are not automatically converted to links. (Use the `[text](http://url)` syntax instead.)
* Links to a specific part of a page (e.g. `#heading-1`) must be in lower case.  (GFM allows mixed case)
* You can automatically generate a Table of Contents for a long page. (see below)

The first `h1` or `#` will automatically become the page title.  You can override this with some `headmatter` (see that section below).

#### Links

Use relative links to other pages.  Don't use github based links.  In general internal links should not start with `http`.  Instead they should either start with a directory or a file name.  External links should start with `https://`.  Links to other guides should end in `.md`, not `.html`.

These rules ensure the links work from the both the github markdown side, and are properly converted to HTML links for the guides website.

*Don't:*
```md
- [How to Write User Stories](https://github.com/labzero/guides/blob/master/product_design/how_we_write_user_stories.md)
- [How to conduct a presentation](process/presentation.html)
- [File in the same directory](/languages/sibling-document.md)
- [Our Website](labzero.com)
```

Do:
```md'
- [How to Write User Stories](/product_design/how_we_write_user_stories.md)
- [How to conduct a presentation](/process/presentation.md)
- [File in the same directory](sibling-document.md)
- [Our Website](https://labzero.com)
```


For intra-page links to headings (e.g. `my-page#some-heading`).  Use the heading name in all lower case with dashes for spaces.

Example:

```md
If this page is `meetings.md`, one can link to the section below like:
[online meetings](meetings.md#conducting-an-online-meeting)


### Conducting an Online Meeting
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

Any file named with the extension `.md` or `.html` is automatically included in the site.  You can link directly to it.  Other file types may or may not require custom config.

#### Table of Contents

You can have Jekyll automatically generate a table of contents for you.  Where you want the TOC add the following markdown:

```md
* list to be automatically populated with TOC by Jekyll
{:toc}
```

#### adding `headmatter`

Headmatter is a special type of configuration placed at the top of a file.  Jekyll uses this to set or control certain document properties.

**It is optional for nearly all pages**  However, here are a few pieces of headmatter you might choose to use:

```
---
title: The differences between Crocodiles and Alligators
layout: page
---
```

The above sets the article title (the 1st `h1` if unset).  And it switches to the `page` layout.  The `page` layout does *not* display the "Pages" section with related pages at the bottom.

#### index pages

Our breadcrumbs necessitate an index.md file in each sub-directory.  This page is only linked to via ntermediary breadcrumbs.  Without it, users will see a 404 page.  

To avoid this, we have a simple script that lists out the files in a directory with their titles.  You can copy `index.md` from most sub-directories into any new subdirectory and it will work.  

It relies on a partial in `_includes` which contains a small bit of liquid code.

### Working with Pull Requests and editing on github.com

You can work directly on github.com to add & edit articles.  

_In short the steps are:_

1. edit or add a file
2. commit the change to a **new branch**
3. github guides you to open a pull request
4. open the branch from the repo index page and edit additional files to add them to the same pull request

<details><summary>Click here to open a more in-depth editing guide</summary>

> Note that the UI you see may differ from the screenshots below. Github continues to refine their UI.

After you've made your first edit commit the change.

![Commit Changes button](https://github.com/labzero/guides/assets/1916144/b55e0311-138a-4f5d-a120-d9c88b924e37)

You'll note that it says you're creating a new commit and branch.  Copy the branch name for later use.  In this image the branch name is `tgaff-patch-1` (github created that for me).

![Commit changes dialog](https://github.com/labzero/guides/assets/1916144/4b07bf72-b2ab-4315-a03f-61b67aec412f)

Github will direct you to open a Pull Request (PR).  

</details>

#### Adding files, or edits to an existing PR or branch

You likely want to **add a link to the index.md** file after you've created a **new guide**.  

![Branch name on PR](https://github.com/labzero/guides/assets/1916144/39bf97fa-96e3-40c7-9276-8046ef9e9448)

To add additional files, open up the **same branch** from the repository [index page](https://github.com/labzero/guides/).

![Open up a branch](https://github.com/labzero/guides/assets/1916144/057be955-5557-4aa6-ab38-08a87cc82745)

From there you can edit any file (e.g. index.md) and follow the same procedure as before to commit a change.  When committing your next change be sure you're still on your previous branch or you'll have to open a new PR.

![Branch name while editing a file](https://github.com/labzero/guides/assets/1916144/85443f43-f773-4cbb-8e56-bd3fa35b42f9)

## Technology

This a Github Pages site built with Github's automatic Jekyll setup.

In short you're looking at:

[github-pages](https://docs.github.com/en/pages/getting-started-with-github-pages/about-github-pages) + [Jekyll](https://jekyllrb.com/) + [hydejack (theme)](https://hydejack.com/docs/) + kramdown (md parser).

### Deployment

Deployment is automatic when a new commit is merged into the master branch.  It is performed by a Github action with no customization.

### Config

Most of the config lives in [_config.yml](/_config.yml).  Let's try to keep config specific comments there.

Worth noting: the sidebar and footer links are both in the config.

### Running the site locally

This is not supported.  Github has instructions for doing this but we haven't set up the repo for it.  (Attempting to keep the repo easy to use for all team members.)

### Tests

There are two github actions.  

1) PRs are tested to verify their links are correct and pointing to a real page.

2) Site Deploys are tested post-deploy to verify links all point to a real page/address.

Both of these use [Lychee](https://github.com/lycheeverse/lychee-action/) to do the testing.

Be aware of these differences:

  * SUT:
    * the PR tester tests Markdown files **directly** - that means the links need to be properly relative to work correctly.  It **does not use Jekyll** to build first.
    * the post-deploy site tester fetches from https://guides.labzero.com, testing the deployed HTML pages.
  * running the site tester too often might annoy github :shrug: not sure
  * use `.lycheeignore` to ignore files - it applies to both testers