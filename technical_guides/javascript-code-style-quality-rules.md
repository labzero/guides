## JavaScript coding conventions / quality guidelines 

### Language

We use [TypeScript](https://www.typescriptlang.org/) whenever possible. When using [Webpack](https://webpack.js.org/) to bundle our code, we'll pass TS files through [`ts-loader`](https://github.com/TypeStrong/ts-loader).

### Code style

We use a combination of [ESLint](https://eslint.org/) and [Prettier](https://prettier.io/) to enforce a consistent code style. We make use of IDE extensions to automatically lint and format our code.

If the project is not TypeScript-based, we usually use the [Airbnb config](https://www.npmjs.com/package/eslint-config-airbnb). If it is TypeScript, we use the [recommended settings that come with `typescript-eslint`](https://typescript-eslint.io/getting-started/).
