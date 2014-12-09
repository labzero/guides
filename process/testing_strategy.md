# Testing Strategy

## Overview
Every product has a unique risk profile that we need to measure to create a testing strategy that addresses those risks.
Test coverage comes from a variety of methods; no purely automated approach is able to provide sufficient coverage by itself.
Likewise, no purely manual testing approach can appropriately validate a product; usually, time and lack of human resources
prevents exhaustive manual testing strategies from being effective.

A balanced approach is required that manages risk at each layer and provides crucial feedback to a team via Continuous
Integration as well as by manual validation. Broadly speaking, our testing coverage comes from some combination of unit
tests, acceptance tests, and exploratory testing.

## How to spend your testing dollars
Ideally, we're able to get the bulk of our feedback on the quality of the product via automated channels, like Continuous
Integration. This allows for manual/exploratory testing efforts to be better spent on activities that can't be found via
automation, e.g., CSS styling, unexpected conditions, unusual flows through a product, and bugs with ideas/designs themselves.

Broadly speaking, we're looking for 80% or greater overall code coverage provided to us by our unit test suite.
This applies to the JS in the browser as well as to our controllers and models on the backend. Using a percentage for
coverage is generally an insufficient metric since path coverage through the code has little to do with inputs and
expected outputs for various use cases. Ideally, we have better than 80% coverage on our highest risk areas of the
codebase, e.g., business logic, information accuracy, security, etc.

No automated tool can properly assess these use cases or our coverage of them, so we'll use the term "code coverage"
lightly. This is where we need to use our human intelligence to assess "coverage" during the review of a pull request,
or ideally even earlier when the tests are being written.

Unit tests are well and good, but we'll need something better to verify a number of scenarios on any given product. This
is where "acceptance" tests become important to make sure we're tracking well toward a goal of 100% of use cases.

Acceptance tests should be written from the perspective of the user, product owner and/or tester. These tests use the
system as it is intended to run in production and usually entail end-to-end testing via the browser, mobile device, or API's.

Exploratory testing is what happens when a real human tries to use the product and even when they try to break it. This
type of testing requires true human intelligence and relies on the fact that once a product is in a user's hands, they
will do things that might not have been anticipated in advance.

## Keeping the light green, and meaningful
Modern dev teams live and die by the feedback that their robot counterparts can provide. We want the tests written by
the team to run locally, in Continuous Delivery, and manually against various target environments.

If tests are written after the features, then we really don't know if a new change works, or if it breaks other things
that were untested. We need to keep an eye out for appropriate levels of automated tests during the peer review stage.
For most teams, this means during the review of a Pull Request, or earlier at the time of writing a story. Ideally, all
acceptance scenarios are identified at the time of writing the story; in reality, this is a hard goal to acheive. At a
bare minimum, during a code review we should be looking for coverage over common "known" cases. Even developers with the
best intentions can miss things; they could use an extra set of eyes.

## Partnering with QA
This is where magic happens. Teams fortunate enough to have QA team members have a great oppotunity to create
a great partnership between Dev and QA to help manage gaps in coverage.

By using modern ATDD tools, it's easier to see which use cases are covered and which are not. These BDD tools also lend
themselves nicely to a proper collaboration at the test code level to acheive the "coverage" that we're after.

QA should review pull requests and suggest that more coverage is added if they see significant gaps. Additionally, QA can
audit the suite as a whole and add coverage that is missing to the ATDD suite. In time, our regression suite should cover
most of the product's functionality, leaving certain cases to be done manually.

QA will also need to do exploratory testing of the product, even though we have partnered to create a wonderful ATDD/BDD
acceptance suite. The spirit here is that QA is able to use their knowledge of the test coverage provided by automation,
in order to focus their attention towards use cases that were not automated. Many scenarios may be too hard to automate,
and a deal will need to be made with QA and the product team to address these scenarios manually. Consider using a tag
of `@manual` on your suite to denote the scenarios that should be covered manually.