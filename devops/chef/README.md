Chef Cookbook Best Practices
============================

General

  1. Create a cookbook for every service or application that you have.
  1. Create a public recipe for each component of the service or application (app server, db server, etc.)
  1. Create private recipes for repeatable stuff you want to put in every cookbook
    (not exposed to end user, not in run_list of a node, included in other recipes, documented)
  1. Create data driven cookbooks - Use attributes so the behavior can be changed at runtime.  Databags and encrypted databags can also be used if needed for organization level configuration.  Create an attributes file for each recipe.  Configurable per environment.
  1. Use default recipe so cookbook works out of the box.
  1. Library cookbooks - not really for recipes
  1. Wrapper cookbooks - lightweight - contain mostly attribute overrides.
  1. Iterate often. Make small changes.
  1. Lock down cookbook versions per environment.
  1. Use custom attributes in a wrapper cookbook instead of using roles.
  1. Use Berkshelf to manage third party libraries.

Testing

  1. Embrace test driven development by writing Kitchen tests using ServerSpec before cookbook code is written.
  1. Add tests for complete coverage after cookbook code is written.
  1. Use Kitchen and ServerSpec to test all changes to cookbooks before uploading to Chef server or checking into Git, adding tests for complete coverage.
  1. Use Foodcritic for linting of all changes to cookbooks before uploading to Chef server or checking into Git.

Source Control

  1. Branch in Git for changes to cookbooks.
  1. Set up Continuous Integration for testing of Chef cookbook merge / pull requests.

More Information / References
=============================

  * [The Berkshelf Way ~ Jamie Winsor](http://www.getchef.com/blog/chefconf-talks/the-berkshelf-way-jamie-winsor/)
  * [Berkshelf Site](http://berkshelf.com/)
  * [Chef Cookbook Anti Patterns](http://dougireton.com/blog/2013/02/16/chef-cookbook-anti-patterns/)
  * [Getting Started Writing Chef Cookbooks the Berkshelf Way](http://misheska.com/blog/2013/06/16/getting-started-writing-chef-cookbooks-the-berkshelf-way/)
  * [Test Kitchen](http://kitchen.ci/)
  * [ServerSpec](http://serverspec.org/)