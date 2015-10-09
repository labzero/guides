## Javascript coding conventions / quality guidelines 

We are using JSHint (for correctness) and JSCS (for style).

Here are a few things to keep an eye on:
- Consistent indentation (2 spaces)
- Keep 'use strict' in function scope
- Consistent quotation marks (single)
- Consistent use of spacing
- Spaces around operators (i.e. + - etc)
- Remove extraneous trailing whitespace

We are *not* enforcing maximum number of function parameters, because that doesn't work well with Angular dependency injection, but if you have more than about 3 in a regular function, that's probably too many.

### JSHint
You can see our recommended JSHint settings in the  [`.jshintrc`](.jshintrc) file. 

You will have to add the appropriate entries for your project to the `globals` section.

The `maxdepth` and `maxcomplexity` settings are extremely generous, and should probably be lower, but that is sometimes a challenge in javascript.

#### Editor Integration
JSHint is built in to RubyMine, so it should honor the project `.jshintrc` and show you violations
There is also a package for Sublime

#### Adding JSHint to your project
Copy this [`.jshintrc`](.jshintrc) file into the root of your project.

You'll need `node` both in your local and ci environments. You'll need your `package.json` to include the current version of `jshint`
Run `npm install` in the project root to make sure you have the library installed
Then run: `./node_modules/jshint/bin/jshint app/assets/javascripts/`
Your CI build needs to include `npm install`, and your build rake task should include:
```
sh './node_modules/jshint/bin/jshint app/assets/javascripts/'
```

#### Running on the command line
`./node_modules/jshint/bin/jshint app/assets/javascripts/`

### JSCS
JSCS comes with presets for several JS style guides. I chose the one that seemed to be the closest to our current practices (out of laziness more than anything else).
I changed/relaxed a few settings (which you can see in [`.jscsrc`](.jscsrc))

#### Editor Integration
There is a plugin for RubyMine and a package for Sublime Text

#### Adding JSHint to your project
Copy this [`.jscsrc`](.jscsrc) file into the root of your project.

You'll need `node` both in your local and ci environments. You'll need your `package.json` to include the current version of `jscs`
Run `npm install` in the project root to make sure you have the library installed
Then run: `./node_modules/jscs/bin/jscs app/assets/javascripts/`
Your CI build needs to include `npm install`, and your build rake task should include:
```
    sh './node_modules/jscs/bin/jscs app/assets/javascripts/'
```

#### Running on the command line
`./node_modules/jscs/bin/jscs app/assets/javascripts/`
