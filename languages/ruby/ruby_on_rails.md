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
Please delete the Rails boilerplate one when starting a new app and start plumbing it with the what’s-where basics.  This page is what’s shown on the Github homepage for the project and is a good launching point to other pages in the documentation. Use Markdown when appropriate to improve formatting.  Always aim for a balance between "enough to handle common tasks" and "too long to effectively find what I need".

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
For sensible suggestions, see https://github.com/bbatsov/ruby-style-guide and https://github.com/bbatsov/rails-style-guide

We enforce some of these guidelines using Rubocop (see [ruby-style-quality-rules.md](ruby-style-quality-rules.md)).  The defaults can be a little stifling so use the rules that work for the team.

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
See our CSS guide at: https://github.com/labzero/guides/blob/master/languages/css

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
* Do not ever monkey-patch base classes.
* Use alias_method_chain when possible to preserve the actual implementations.
* Monkey-patch in initializers, never anywhere else, e.g. config/initializers/paperclip_patch.rb

# Updating Your Gems
When you’re adding new gems or updating some of them try updating others while you’re at it so that we keep all of our gems moving forward.  There is a risk here that we might be bringing in unwanted changes which breaks the app, but use your best judgement on when this is appropriate.  Be sure to know the difference between Major, Minor, and Tiny versions when doing this so that you’re not inadvertently adding non-backward compatible changes.  

For Ruby and/or Rails we should be on the latest patch level (tiny) for the version.

# Javascript

## Unobtrusive JS 

[main principles shamelessly stolen from Wikipedia]
Do not make any assumptions: Defensive programming techniques should allow for the possibilities that JavaScript may not run, the browser may not support expected methods, the HTML may have changed, unexpected input devices may be in use and other scripts may either not be present or may be encroaching on the global namespace.
Find your hooks and relationships, such as IDs and other aspects of the expected HTML.
Leave traversing individual DOM objects to the experts, such as to the CSS handler built into the browser where possible.
Understand browsers and users, particularly how they fail, what assumptions they make, and unusual configurations or usages.
Understand events, including how they 'bubble' and the features of the Event object that is passed to most event handlers.
Play well with other scripts by avoiding global function and variable names.
Work for the next developer by using self-explanatory variable and function names, creating logical and readable code, making dependencies obvious, and commenting any code that still might confuse.

## Stimulus & Turbo (Hotwire)

Tailoring to your product's needs, you might opt for Rails's default JS stack, Hotwire. If your team elects to utilize this, particularly its Turbo Frames or Streams features, it's crucial to determine whether you'll support it as unobtrusive JS. Turbo Frames and Streams can introduce maintenance challenges if a non-JS pathway is also required. Given the tendency to overlook user experience in scenarios where JavaScript is non-functional, it's often prudent to implement tests for both JS and non-JS routes within the app.

Try to keep Stimulus controllers general purpose; don't couple them tightly to a specific page or partial.  If you make good use of data attributes you can ensure that each controller is configurable and reusable.  Try not to re-build functionality that can be accomplished with CSS.  Use Stimulus to tie other JS libraries into the Turbo events life-cycle.

Fetch HTML with Turbo rather than building and injecting it manually in Stimulus.  When determining which tool to use it can be best to consider them in the order of: HTML & CSS, Turbo Frames, Turbo Streams & finally Stimulus.  Avoid packs if using Stimulus.

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


