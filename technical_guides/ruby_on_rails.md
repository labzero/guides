---
title: Ruby on Rails Developer Guide
layout: default
---

* table of contents
{:toc}

# Ruby on Rails Developer Guide

# Overview
This document is a living doc shared by all developers at Lab Zero.  We as developers at Lab Zero believe that following these principles produces higher quality software.  It’s a pact that we share.  Please read and add to it as we find things on our projects that we’d like to make standard for our engineering practice.

# Like Camping ⛺
When camping there is a rule to leave your campsite cleaner than it was when you got there.  The same is true when writing code.  Each commit should be refactoring the minutia as you go such that each commit leaves the code base cleaner than when you started.

# Documentation
There are many things that we will need to communicate and share with others developers during and after we’re done.  Please document the basics that help folks know how to install, configure and deploy the app.

We are committed to keeping documentation updated and relevant. The value of documentation diminishes with redundancy. Avoid excessive details that can render the documentation cluttered which increases the chance it will become outdated. Instead, focus on key information and unique system nuances – if there's a 'dragon' lurking in the system, make sure to document it.  Your first point of reference should be the repository's README.md, but the documentation shouldn't stop there. Depending on the organization, a wiki might also be a suitable medium for extended documentation.

Furthermore, consider the names and structure of your integration tests. Well named tests can act as a form of documentation, providing insights into the systems features, shedding light on our original design intentions, and highlighting edge cases.

## READMEs

Please delete the Rails boilerplate one when starting a new app and start plumbing it with the what’s-where basics.  This page is what’s shown on the Github homepage for the project and is a good launching point to other pages in the documentation. Use Markdown when appropriate to improve formatting.

Always aim for a balance between "enough to handle common tasks" and "too long to effectively find what I need". At the very least, the page should include project setup and any description necessary to find the right repo.

## Wikis

If the organization has a commonly used wiki tool, that's usually a good choice, otherwise a Github wiki is [easy to setup](https://docs.github.com/en/communities/documenting-your-project-with-wikis/about-wikis).  Anything beyond the über-basics should be documented on these technical wiki pages.  Some examples of this might be “Deployment Anatomy,” “Search Architecture,” “Importing + Refreshing Application Content,” etc…  Again, it's easy for documentation to get out of date so it may be wise at times to put a wiki link into a code comment.

## Code Comments
Generally these are to be avoided only because they tend to be out of date if used too heavily.  You should favor using **descriptive variable and method names**.
Rather, please use inline code comments when:

* The following lines of code might use some syntax-fu (ie. anything overly-clever)
* You’re working around a bug in a 3rd party library/api/model that we can’t control, i.e. when we have to write something that seems bad in order to use an external/immutable dependency.
* Magic numbers: Explain your units and why the number exists.
* Class documentation: Consider documenting service and library classes.  They often can interact together in ways that might not be immediately obvious from just the names.  Model classes that are especially meaty can also benefit from documentation, especially as new team members come on-board.
* In the Gemfile when locking a gem to a specific version: Please document why we must use that version. This makes it easier to know when it is safe/reasonable to upgrade the gem.

Remember that easy to read code is easier to maintain and easier for new teammates to jump into.

# Tests
These should be the definition of what the app should do, especially with BDD with Rspec and Capybara.  By reading the integration test names we should be able to get a good idea of what features are present in the app.  Likewise, when reading just the names of the unit tests we should be able to get a good understanding of what the class or module does.

Additionally, when solving a bug its always a good idea to first reproduce it with a test and then check the test in to prevent regressions.

# Code Style
For sensible suggestions, see [https://github.com/bbatsov/ruby-style-guide](https://github.com/bbatsov/ruby-style-guide) and [https://github.com/bbatsov/rails-style-guide](https://github.com/bbatsov/rails-style-guide) but note that the team is free to be more flexible in adopting rules.

We enforce some of these guidelines using Rubocop (see [ruby-style-quality-rules](ruby-style-quality-rules.md)).  The defaults can be a little stifling so use the rules that work for the team.

## Variable Naming
* Spend a few moments to choose an appropriate word.
* Avoid TLAs; spell out words.
* Single character variable names should only be used for local variables that only live in a small block or loop.
* Use snake_case.
* The names shouldn’t be too long. (Perhaps you need to refactor if the name has to be super long.)

## Formatting
Don’t use tabs, ever. Use two spaces.
Max width is 120 chars.
Be consistent.

## Method Length
If you have a method more than 10 lines long it’s time to consider refactoring it.  This isn’t to say that no method can be longer than 10 lines, but this should be a clue that your method may be doing too many things.

## CSS Guidelines

See our [CSS guide](css.md).

## Beyond MVC
### Models vs libs
Use Model and Controller concerns to share common functionality across models or controllers.  Even if you're not sure whether some functionality is going to be re-used, if it makes OOP sense to pull some functionality out, go for it.

You should use lib when the logic is a candidate for gemming up…

### Services
Use Services to handle specific interactions between players within the M&C.  Examples include: Processing & handling an API fetch or modeling complex interactions between multiple other classes.  Adaptor and Mediator patterns are also sometimes a good fit.

### Design Patterns
Think in terms of design “patterns.” If you use one find the appropriate place for the implementations to go.

# Extending 3rd Party Gems
We have to patch 3rd-party gems from time to time, but we want to minimize the impact of ramping folks up on where those dragons lie.

As good open source citizens we should fork third-party gems and contribute back to them with pull-requests for our fixes and additions.  Let’s consider some scenarios when we should fork and when we should patch.

## Forks vs Monkey patches
### Forking best practices:
Use forks as much as possible over monkey-patches
Use the Labzero account for forking those repos
Submit pull requests and be a good OSS citizen
Watch for your pull request to be released in a new release.  When it has been accepted clean up the Gemfile to use the new official version and delete your fork.

### Monkey-patching best practices:
* Try not to.
* Do not ever monkey-patch base classes. Inherit from them, then modify and change other classes to inherit from that.
* Use modules and inheritance to inject behavior.  [`prepend` a module with overrides](https://www.justinweiss.com/articles/rails-5-module-number-prepend-and-the-end-of-alias-method-chain/) if needed.
* Monkey-patch libraries in initializers, never anywhere else, e.g. config/initializers/paperclip_patch.rb

# Updating Your Gems
When you’re adding new gems or updating some of them try updating others while you’re at it so that we keep all of our gems moving forward.  There is a risk here that we might be bringing in unwanted changes which breaks the app, but use your best judgement on when this is appropriate.  Be sure to know the difference between Major, Minor, and Tiny versions when doing this so that you’re not inadvertently adding non-backward compatible changes.

For Ruby and/or Rails we should be on the latest patch level (tiny) for the version.

# Javascript

## Import maps vs. JS bundling

For new Rails (version 7+) apps, decide between a JS bundling tool and import maps. For apps requiring minimal JS use, import maps are efficient and easy. Transitioning to a bundler, later on if needed, is straightforward.

For JS-intensive apps, especially with React, Vue, or Angular, start with a bundler and consider using Typescript.  See also our [JS guides listed here](../technical_guides) and the official [Rails guides](https://guides.rubyonrails.org/working_with_javascript_in_rails.html#choosing-between-import-maps-and-a-javascript-bundler).

## Stimulus & Turbo (Hotwire)

Try to keep Stimulus controllers general purpose; don't couple them tightly to a specific page or partial.  By making good use of data attributes you can ensure that each controller is configurable and reusable.

When determining which tool to use it can be best to consider them in the order of: HTML & CSS, Turbo Frames, Turbo Streams & finally Stimulus. Try not to re-build functionality in Stimulus that can be accomplished with CSS.  Build pages first without Turbo, then upgrade them for better user experience as needed.  Prefer fetching partials with Turbo over generating HTML in Stimulus Controllers.

Consider also whether you need to maintain functionality when JS has not loaded or does not work.  See Unobtrusive JS below.

## Unobtrusive JS

In today's digital landscape, many applications lean heavily on JavaScript, resulting in the unobtrusive JavaScript (UJS) approach becoming less prevalent than in the early days of Rails. When embarking on a new project, it's crucial to consider the demographics of your target users, the nature of their internet connections, and the browsers they prefer. This will help determine whether the added time and effort required to implement and test for UJS is justified. For applications with minimal JavaScript dependency, such as those utilizing import maps, integrating UJS is comparatively straightforward.

If engaged in a project that has adhered to unobtrusive JS principles, it's important to remain consistent. Leverage the UJS capabilities inherent in Rails as extensively as you can. Additionally, test both with and without JavaScript to validate that all pathways function as anticipated.

Rails 7 still allows you to [switch back to UJS from previous versions](https://guides.rubyonrails.org/working_with_javascript_in_rails.html#replacements-for-rails-ujs-functionality), however their recommendation is now to use Turbo.

# OOP
This is always the destination, but we often have to crossover from chaos and the simplest code to the code that could work to the best code we know how to write.

# Fat Model - Skinny Controller
This is a fancy way of saying that your views and controller code is not the place for capturing business logic, i.e. that stuff belongs in our models and other supporting classes.  The primary role of a controller is to help manage inbound requests, delegation to the domain that knows how to manage the actual details, and packaging a response.

## Smells to watch for:
Controller actions that set attributes on a variety of objects, i.e. your controller should not understand how one model relates to another and how they should be orchestrated.
Controller actions that are longer than 10 lines of code (there’s no magic number here, but consider that when you see long actions.

7 Patterns to Refactor Fat ActiveRecord Models include:

- extract value objects (and place in app/models)
- extract service objects (and place in app/services)
- extract form objects (and place in app/forms)
- extract query objects (and place in app/models)
- introduce view objects (helpers, ViewComponents and Decorators are all good directions to think in)
- extract decorators (consider using the draper gem)
- extract policy objects (there are a number of good gems for this)

# Security

As a starting point, please read https://guides.rubyonrails.org/security.html and become familiar with the concepts.  We must adhere to all of the points mentioned there.

## Brakeman
We include brakeman in our CI runs on both PRBuilder jobs and on commit-level jobs on develop when we can't use CodeClimate.

The brakeman CI job should be configured to fail if any new security vulnerabilities are found.

Remember to keep this gem updated to catch the latest list of vulnerabilities.
