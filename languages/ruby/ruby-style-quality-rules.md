# Ruby coding conventions / quality guidelines

* table of contents (auto inserted)
{:toc}

We use Rubocop, which adheres to this Ruby style guide (https://github.com/bbatsov/ruby-style-guide). See also the related Rails style guide (https://github.com/bbatsov/rails-style-guide) for some good tips (some of which are enforced by Rubocop).
We generally leave the Rubocop defaults alone, but we have made some changes.

### Where we depart from the defaults:

- No max line length (always makes you do something wonky with at least one line somewhere in your code base). That said, if you go significantly over 100 expect to be dinged during PR review unless you have a really good reason / no good alternative.

- Changed the max method length from 10 to 15.

- Relax some whitespace rules (extra new lines at the beginning / end of blocks) for specs and cukes since block based DSLs are more readable if you can break some rules that work for regular ruby code.


### Common mistakes:

DON'T | DO
 ------- | -----
Omit parens around arguments in method definitions | Always use them
Use spaces inside parens in i.e. foo( 5 ) | foo(5)
Use spaces inside of []'s i.e. list = [ 1, 2, 3 ] | [1, 2, 3]
Omit spaces inside of {}'s i.e {\|x\| x.foo} | { \|x\| x.foo }
Use double quotes when not necessary | Only use for strings with interpolation
Use explicit `self` when not necessary | Only use when attribute may be shadowed by local var / parameter etc. (i.e. almost never)

### Adding Rubocop to your project
Copy this [`.rubocop.yml`](.rubocop.yml) file into the root of your project

Your gemfile should contain:
```
gem 'rubocop', require: false
gem 'rubocop-checkstyle_formatter', require: false
```
Your project's CI rake task should include `sh 'rubocop'`

Feel free to add reasonable `Exclude`s to your `.rubocop.yml`. For example, `schema.rb`, database migrations, cucumber and rspec configuration files (drivers.rb, env.rb, rails_helper.rb etc.). But please, not anything in `app` or `lib` (other than maybe some gnarly rake tasks).

### What this means for you

These checks are run during our CI process. To avoid build failures during your PR process, you will want to run the checks yourself locally before submitting a PR (just like specs and cukes).
To do this, run `rubocop -R` at your project root.
There are plugins for both Sublime Text (https://github.com/pderichs/sublime_rubocop)
and RubyMine (you can install it via Preferences > Plugins > Browse in RubyMine), which will allow you to see violations as you make them.
