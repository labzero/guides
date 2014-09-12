Chef Cookbook Best Practices
============================

  1. Create a cookbook for every service or application that you have.
  2. Create a public recipe for each component of the service or application (app server, db server, etc.)
  3. Create private recipes for repeatable stuff you want to put in every cookbook
    (not exposed to end user, not in run_list of a node, included in other recipes, documented)
  4. Create data driven cookbooks - Use attributes so the behavior can be changed at runtime.  Databags and encrypted databags can also be used if needed for organization level configuration.  Create an attributes file for each recipe.  Configurable per environment.
  5. Use default recipe so cookbook works out of the box.
  6. Library cookbooks - not really for recipes
  7. Wrapper cookbooks - lightweight - contain mostly attribute overrides.
  8. Iterate often. Make small changes. Use Vagrant VMs to quickly test your changes. `vagrant plugin install vagrant-berkshelf`
  9. Lock down cookbook versions per environment.
  10. Use custom attributes in a wrapper cookbook instead of using roles.

More Information / References
=============================

  * [The Berkshelf Way ~ Jamie Winsor](http://www.getchef.com/blog/chefconf-talks/the-berkshelf-way-jamie-winsor/)
  * [Berkshelf Site](http://berkshelf.com/)
  * [Chef Cookbook Anti Patterns](http://dougireton.com/blog/2013/02/16/chef-cookbook-anti-patterns/)
  * [Getting Started Writing Chef Cookbooks the Berkshelf Way](http://misheska.com/blog/2013/06/16/getting-started-writing-chef-cookbooks-the-berkshelf-way/)