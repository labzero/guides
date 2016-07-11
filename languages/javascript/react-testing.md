# Testing React applications

## Overview

The React testing ecosystem is constantly evolving, and like many areas of the Node world, it is made up of many small tools rather than an all-encompassing test-running solution. This guide is intended to describe what decisions we've made for unit-testing our React apps, and is not intended to be a thorough how-to guide on setting up an app for testing. It should be seen solely as a snapshot of what we're doing as of mid 2016.

Since we like to live on the cutting edge, our Node apps make use of ES2015/2016 features which are then transpiled using Babel. This complicates certain factors in regards to testing that we'll try to cover.

## Unit testing: Mocha

We use [Mocha](https://mochajs.org/) as our unit-testing framework. It provides us with an easy command-line interface, hooks, and dead-simple callbacks for asynchronous tests.

In order to test transpiled files, we need to pass [`babel-register`](https://babeljs.io/docs/usage/require/) as a compiler, like so:

```shell
$ mocha --compilers js:babel-register
```

## Assertions: Chai

We use [Chai](http://chaijs.com/) as our assertion library. Its expectation grammar is flexible and easy to understand.

## Fakers: Sinon

[Sinon](http://sinonjs.org/) provides spies, stubs, and mocks, each of which provide a robust API for providing fake data.

## Shallow rendering: Enzyme

Instead of using Jest or ReactTestUtils, we use [Enzyme](http://airbnb.io/enzyme/) to shallow render our React components without the need for a virtual DOM. We especially like its ability to pass context into its shallow render call, which allows us to more easily test components that are `connect`ed to a Redux store, if necessary.

## Import stubbing: Proxyquire

Since many modules import other modules, we often want to stub those imports so we're not inadvertently testing half our app. We use [Proxyquire](https://github.com/thlorenz/proxyquire) for this purpose. Specifically, we use `proxyquire.noCallThru()` to ensure that the original imports are not called.

Behind the scenes, we use Babel to transpile our `import` statements into `require` statements, which do not have the built-in concept of a "default" export. We often need to create a helper that modifies our stubbed imports to work well within Proxyquire's `require`-based ecosystem, like so:

```js
/* test/mockEsmodule.js */

export default (obj) => {
  const esModule = obj || {};
  Object.defineProperty(esModule, '__esModule', {
    value: true,
  });
  return esModule;
};
```

The following code for `foo.js` demonstrates how it imports a module, `bar.js`, then we stub this import within the `beforeEach` statement in its test. Note how `mockEsmodule` receives an object with a key of `default` (since `bar.js` contains a default export), and how we access the `default` property from our `proxyquireStrict` result (as `foo.js` has an `export default` statement).

```js
/* bar.js */

export default 'hello';
```

```js
/* foo.js */

import bar from './bar';

const foo = () => bar;

export default foo;
```

```js
/* test/foo.test.js */

import { expect } from 'chai';
import mockEsmodule from './mockEsmodule';
import proxyquire from 'proxyquire';
const proxyquireStrict = proxyquire.noCallThru();

describe('foo', () => {
  let foo;

  beforeEach(() => {
    foo = proxyquireStrict('../foo', {
      './bar': mockEsmodule({
        default: 'goodbye',
      }),
    }).default;
  });

  it('returns the stubbed contents of bar', () => {
    expect(foo()).to.equal('goodbye');
  });
});
```

## Code coverage: Istanbul

[Istanbul](https://github.com/gotwarlost/istanbul) is the de-facto JS code coverage tool. It provides robust HTML/LCOV reports for files that have been touched by our test suite.

Testing a Babel app is currently difficult with the current release (0.4.4) of Istanbul, but there is a command-line interface called [nyc](https://github.com/istanbuljs/nyc) that supports Babel, and even supports coverage of modules that have been required using Proxyquire. It can be easily configured to use `babel-register` for better ES2015/2016 support.