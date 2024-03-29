# Testing React applications

## Overview

We're old hands at React testing, having lived through the eras of Jasmine, Mocha, Chai, Sinon, Enzyme, et cetera. Over time testing practices have evolved significantly, primarily with the emergence of Jest and React Testing Library, which now encompass the capabilities of these older, smaller tools. We too have evolved and embrace RTL and Jest as our standard test setup.

## Unit and integration testing: Jest

We use [Jest](https://jestjs.io/) as our testing framework. We make use of Jest's assertions, matchers, mocks, built-in code coverage, and more.

We use Jest to write unit tests for code outside of React components, such as API routes and helpers. We also use Jest to write integration tests with the help of React Testing Library.

### Code coverage

We often strive toward 100% code coverage when reasonable. In some cases, there might be JSDOM limitations, third-party code which is hard to partially mock, or Jest's inability to pass tests with uncaught errors. If so, we tell Istanbul, Jest's code coverage tool, to `istanbul ignore` particular lines, followed by a descriptive comment explaining why.

## Rendering: React Testing Library

We make use of [React Testing Library](https://testing-library.com/react) to test our React components, writing integration tests that describe user behavior, and skipping directly testing any internal methods or hooks. When aiming for high (or total) code coverage, we find that the use of RTL helps us write better components, as we want our tests to _indirectly_ cover the aforementioned internal code.
