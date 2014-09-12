# LZ iOS - Best Practices Guide


## Overview
This document is our narrative over a handful of good online resources and to cover topics that those resources do not address.
To get started, make sure that you’re familiar with the style guides.

## Style Guide

The following guides explain how we style our code at LZ. These are not merely suggestions, you need to follow them, excepting the addendum below. In particular, deviating from Apple’s guide will cause KVC and KVO issue, as their guide covers naming conversions that the Objective-C runtime and Cocoa runtime rely on.
 
Apple: https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/CodingGuidelines/CodingGuidelines.html

New York Times: https://github.com/NYTimes/objective-c-style-guide

## Addendum

### Closing Curly Braces
Ignore the curly brace styles in the NYT guide (found in the Spacing section). At LZ we use the curly brace style that Apple uses (and which Xcode gives you on all autocompletes). The last closing curly brace always goes on a new line, but intermediate closing curly braces go on the same line as the next opening curly brace.

For example:
```
if (foo) {
	// do stuff
} else if (bar) {
	// other stuff
} else {
	// more stuff
}

Not:
if (foo) {
	// do stuff
}
else if (bar) {
	// other stuff
}
else {
	// more stuff
}
```
### Images

We follow everything the NYT style guide says for naming images for apps targeting iOS 5 or lower. For apps that target 6.0 and higher, always use the Asset Catalog for all images. The naming conventions should follow the same style.

### Interface Construction

We favor XIB over programmatic interface construction whenever reasonable. We favor Auto Layout over Autoresizing Mask whenever the targeted OS supports it. Views in the XIB should have good english names, title cased and space separated. Do not name your view after the outlet it’s associated with.

### Styling

Styling is a complex beast. We favor styling in a XIB if the view has minimal styling and does not require an outlet. For complex reused styles, we prefer to use a styling method on a styling helper. For complex one off styles, doing it programmatically in the view controller or view is the way to go.

### Pragma Marks

Pragma marks are used to separate grouping of methods in the source code.  This helps searching and browsing the method signatures in XCode a lot easier.  Typically we group methods by their implementation.  In UIViewController subclasses, the overridden implementations of the lifecycle methods should be first.  UIViewControlller specific local methods are next.  Then methods for each protocol implementation should be grouped and delimited in their associated Pragma Marks.

## Continuous Delivery

All of our iOS applications should have automated builds that are triggered by commit that run the unit tests, acceptance tests and publishes passing builds to TestFlight. There are a handful of things that you’ll need to do to set it up in Jenkins, here’s how.

### Getting a new project going for CI

We’re using the XCode plugin with the Jenkins Slave plugin…

Do these things:

setup testflight (list these things)

## Test Driven Development

### Unit Testing

XCode provides XCTest as a way to unit test code.  This should be the preferred method for unit testing your code.  OCMock https://ocmock.org is an open source library that we've used in the past to mock out components to help with unit testing.  OCMock now works for Swift!

### Acceptance Testing

Calabash
We use Calabash for automated functional testing of iOS apps.  https://calab.sh.  Calabash requires generating a separate test target to your iOS project.  The installation steps are here https://github.com/calabash/calabash-ios.  Calabash asks as a server listens for commands sent from the test scripts, CFNetwork framework should be included in your project as well as calabash.framework.  The tests are run using Cucumber and written in Gherkin.  

Appium
We are also investigating using Appium for testing iOS apps.  Unlike Calabash, Appium does not require a separate test target for testing your applciation.  Appium server issues commands to your iOS application via UIAutomation.  Running appium is fairly simple locally with a stand-alone app that can be download via https://appium.io.  For integrating with CI, appium commandline should be installed.  The stand-alone Appium app has a recorder that acts as a great first steps for creating tests.  Appium is language agnostic and can generate tests in various languages.  Our preference is to record the test steps in ruby and run with rspec.

Parallelizing tests
Currently, since iOS tests are run via the iOS Simulator, we aren't able to run test suites in parallel.  We currently run our tests on a Jenkin slave node that can launch the simulator.  There are various companies that can run tests in parallel which can be used if that is desired.

## Useful Design Patterns

which ones?
