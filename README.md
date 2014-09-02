<h1>LZ iOS - Best Practices Guide</h1>

LZ iOS - Best Practices Guide

<h2>Overview</h2>
This document is our narrative over a handful of good online resources and to cover topics that those resources do not address.
To get started, make sure that you’re familiar with the style guides.

<h2>Style Guide</h2>

The following guides explain how we style our code at LZ. These are not merely suggestions, you need to follow them, excepting the addendum below. In particular, deviating from Apple’s guide will cause KVC and KVO issue, as their guide covers naming conversions that the Objective-C runtime and Cocoa runtime rely on.
 
Apple: https://developer.apple.com/library/mac/documentation/Cocoa/Conceptual/CodingGuidelines/CodingGuidelines.html

New York Times: https://github.com/NYTimes/objective-c-style-guide

<h2>Addendum</h2>

<h3>Closing Curly Braces</h3>
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
<h3>Images</h3>

We follow everything the NYT style guide says for naming images for apps targeting iOS 5 or lower. For apps that target 6.0 and higher, always use the Asset Catalog for all images. The naming conventions should follow the same style.

<h3>Interface Construction</h3>

We favor XIB over programmatic interface construction whenever reasonable. We favor Auto Layout over Autoresizing Mask whenever the targeted OS supports it. Views in the XIB should have good english names, title cased and space separated. Do not name your view after the outlet it’s associated with.

<h3>Styling</h3>

Styling is a complex beast. We favor styling in a XIB if the view has minimal styling and does not require an outlet. For complex reused styles, we prefer to use a styling method on a styling helper. For complex one off styles, doing it programmatically in the view controller or view is the way to go.

<h3>Pragma Marks</h3>

<needs to be flushed out>

We Zeropeans use a variety of tools in certain ways to deliver high quality products for our clients this is our recipe.

<h2>Continuous Delivery</h2>

All of our iOS applications should have automated builds that are triggered by commit that run the unit tests, acceptance tests and publishes passing builds to TestFlight. There are a handful of things that you’ll need to do to set it up in Jenkins, here’s how.

<h3>Getting a new project going for CI</h3>

We’re using the XCode plugin with the Jenkins Slave plugin…

Do these things:
-setup testflight (list these things)
-
<h2>Test Driven Development</h2>

<h3>Unit Testing</h3>
OCUnit? Cedar? 

<h3>Acceptance Testing</h3>
Calabash?  

Can we parallelize these tests?


<h2>Useful Design Patterns</h2>
<which ones?>
