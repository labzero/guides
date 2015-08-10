# Ruby on Rails Style Guide

# Overview
This document is a living doc shared by all developers at Lab Zero.  We as developers at Lab Zero believe that following these principles produces higher quality software.  It’s a pact that we share.  Please read and add to it as we find things on our projects that we’d like to make standard for our engineering practice.

# Like Camping
When camping there is a rule to leave your campsite cleaner than it was when you got there.  The same is true when writing code.  Each commit should be refactoring the minutia as you go such that each commit leaves the code base cleaner than when you started.

# Documentation
There are many things that we will need to communicate and share with others developers during and after we’re done.  Please document the basics that help folks know how to install, configure and deploy the app.  We are committed to updating these documents when things change to keep them useful.  Given that’s a hard task, please use documentation wisely.  Too much and it’s unusable and all out of date.  If a dragon hides in the system, write about it.  There are three places that we’ll likely want to send folks.  The app’s README, the repo’s Github wiki, and inline code comments. 

## README’s
Please delete the Rails boilerplate one when starting a new app and start plumbing it with the what’s where basics.  This page is what’s shown on the Github homepage for the project and is a good launching point to other pages on the wiki. Use Markdown when appropriate to improve formatting.

## Github Wiki
Anything beyond the uber basics should be documented on the Github wiki pages.  Some examples of this might be “Deployment Anatomy”, “Search Architecture”, “Importing+Refreshing Application Content” etc…

## Code Comments
Generally these are to be avoided only because they tend to be out of date if used too heavily.  You should favor using descriptive variable and method names.  Rather, please use inline code comments when:
The following lines of code might use some syntax-fu (aka anything sufficiently clever)
You’re working around a bug in a 3rd party library/api/model that we can’t control. i.e. When we have to write something that seems bad in order to use an external/immutable dependency.
Magic numbers, explain your units and why the number exists.
Class documentation, consider documenting the controller or model to give the big picture so that folks can find their bearing.
In your Gemfile and you’re locking a gem down to a specific version, please document why we must use that version.  This makes it easier to know when it is safe/reasonable to upgrade the gem.
 
# Tests
These should be the definition of what the app should does, especially with BDD with Rspec and Cucumber… 

# Code Style
For sensible suggestions, see https://github.com/bbatsov/ruby-style-guide and https://github.com/bbatsov/rails-style-guide 

## Variable Naming
Spend a few moments to choose an appropriate word
Avoid tla’s, use words.
Snake case
The names shouldn’t be too long.  (Perhaps you need to refactor if the name has to be super long)

## Formatting
Don’t use tabs, ever.  Use spaces.
Max width is 120 chars max.
Be consistent.

## Method Length
If you have a method more than 10 lines long it’s time to consider refactoring it.  This isn’t to say that no method can be longer than 10 lines, but this should be a clue that your method may be doing too many things.

## CSS Guidelines
[TODO link to CSS guidlines]

## Beyond MVC
### Models vs lib
There are things like concerns that is neither model nor lib candidates.  In a case like that you might use a folder app/models/concern or app/controllers/concern.

You should use lib when the logic is a candidate for gemming up…

### Design Patterns
Think in terms of design “patterns”, if you use one find the appropriate place for the implementations to go. 

# Extending 3rd Party Gems
We have to patch 3rd party gems from time to time, but we want to minimize the impact of ramping folks up on where those dragons lie.  

As good open source citizens we should fork third-party gems and contribute back to them with pull-requests for our fixes and additions.  Let’s consider some scenarios when we should fork and when we should patch. 

# Forks vs Monkey patches
## Forking best practices:
Use forks as much as possible over monkey-patches
Use the Labzero account for forking those repos
Submit pull requests and be a good OSS citizen
Watch for your pull request to be released in a new release.  When it has been accepted clean up the Gemfile to use the new official version and delete your fork.

## Monkey-patching best practices:
* Try not to.
* Do not ever monkey-patch base classes.
* Use alias_method_chain when possible to preserve the actual implementations.
* Monkey-patch in initializers, never anywhere else.  e.g. config/initializers/paperclip_patch.rb

# Updating Your Gems
When you’re adding new gems or updating some of them try updating others while you’re at it so that we keep all of our gems moving forward.  There is a risk here that we might be bringing in unwanted changes which breaks the app, but use your best judgement on when this is appropriate.  Be sure to know the difference between Major, Minor, and Tiny versions when doing this so that you’re not inadvertently adding non-backward compatible changes.  

For Ruby and/or Rails we should be on the latest patch level (tiny) for the version

# Unobtrusive Javascript
[main principles shamelessly stolen from Wikipedia]
Do not make any assumptions: Defensive programming techniques should allow for the possibilities that JavaScript may not run, the browser may not support expected methods, the HTML may have changed, unexpected input devices may be in use and other scripts may either not be present or may be encroaching on the global namespace.
Find your hooks and relationships, such as IDs and other aspects of the expected HTML.
Leave traversing individual DOM objects to the experts, such as to the CSS handler built into the browser where possible.
Understand browsers and users, particularly how they fail, what assumptions they make, and unusual configurations or usages.
Understand events, including how they 'bubble' and the features of the Event object that is passed to most event handlers.
Play well with other scripts by avoiding global function and variable names.
Work for the next developer by using self-explanatory variable and function names, creating logical and readable code, making dependencies obvious, and commenting any code that still might confuse.

# OOP
This is always the destination, but we often have to crossover from chaos and the simplest code to the code that could work to the best code we know how to write.

# Fat Model - Skinny Controller
This is a fancy way of saying that your views and controller code is not the place for capturing business logic, that stuff belongs in our models and other supporting classes.  The primary role of a controller is to help manage inbound requests, delegation to the domain that knows how to manage the actual details, and packaging a response.

## Smells to watch for:
Controller actions that set attributes on a variety of objects.  i.e. your controller should not understand how one model relates to another and how they should be orchestrated.
Controller actions that are longer than 10 lines of code (there’s no magic number here, but consider that when you see long actions.
7 Patterns to Refactor Fat ActiveRecord Models include:
extract value objects (and place in app/models)
extract service objects (and place in app/services)
extract form objects (and place in app/forms)
extract query objects (and place in app/models)
introduce view objects
extract policy objects
extract decorators (consider using the draper gem)

# Security

As a starting point, please read http://guides.rubyonrails.org/security.html and become familiar with the concepts.  We must adhere to all of the points mentioned there.

Another useful, quick read is Rails' Insecure Defaults:13 Security Gotchas You Should Know About

