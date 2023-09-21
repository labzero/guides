## Why write user stories?

Lab Zero writes user stories to place a product’s users at the center of our thinking and decision-making. User stories also support our ability to validate product hypotheses, deliver value early, often and predictably, make better trade-offs, and prioritize effectively.

**Stories generate interest, empathy and vision.** At the highest level, stories embody the things that make your product worth building — who it’s for and what they can do to achieve their goals. If your team isn’t aligned on these core goals, they won’t know how to prioritize their work to achieve the greatest outcomes for the least effort. 

**Stories focus conversation.** A story allows the team to make multiple confirmations of the task throughout the development process. This begins with agreement on the task to be done, and later, how it will pass acceptance testing.

## What is needed before we write user stories?

**Map the customer’s experience.** Armed with your customer research (you’ve defined personas based on qualitative and quantitative research, right?) put yourself in the customer’s shoes and map their journey as you understand it today.

**Define a clear goal.** Review your map with the project’s stakeholders to confirm your current understanding and agree upon a single experience or interaction which matches a single business outcome. Clarify the riskiest assumption, define your hypothesis, and explain how you will test and measure success.

**Draft a design.** Designs help clarify to the entire team what will be done. They naturally tease out edge cases. Discuss with your team what fidelity of design is right for your situation. 

## Story Structure

**[User] --> [does or sees something]  + [optional qualifiers] --> in order to [accomplish a clear goal].**

#### User… 

Choose a personal or functional role within your system. 

#### …does or sees [something]” + [optional qualifiers] 

Be concrete but not overly verbose - let the design fill in the details.

#### ...in order to [accomplish a goal].

Describe the outcome the user achieves.


## Acceptance Criteria

The description in your story should provide additional context and clarify what will be tested when the story is delivered.

Consider trying the “Given-When-Then” formula, a template intended to guide the writing of acceptance tests ([Gherkin](https://cucumber.io/docs/gherkin/)). It is likely that the developer will write automated tests based on your story, some tests may match the criteria you use to accept the work. 

* Given [some context, this is the pre-condition to the activity]
* When [some action is carried out]
* Then [a particular change or set of changes you expect due to the specified action]

Here's an example of a login story.
>_Feature: As a user I want to sign in and see my orders_  
>
>__Scenario: User supplies correct username and password__  
>_Given that I am on the log in page_  
>_When I enter my username and password correctly_  
>_And click 'Sign in'_  
>_Then I am taken to my dashboard showing my orders_  
>
>__Scenario: User does NOT supply correct username and password__  
>_Given that I am on the log in page_  
>_When I enter my username and password incorrectly_  
>_And click 'Sign in'_  
>_Then I see an error message ‘Sorry, incorrect user name or password.”_  

To clarify the standard for completion for all stories in the backlog, define your team’s technical “Definition of Done” in a visible place at the beginning a project. For example, at Lab Zero, completing a story requires not only implementing it and fulfilling the acceptance criteria, but also writing tests, running test suites and using pull requests to merge code. 

## Who writes the stories?

Lab Zero likes to have the product owner write epics, and the designer write user stories. 

Why? 

It helps plant the product owner firmly in the problem space: defining the value the product should deliver based on our current understanding of the customer’s goals, the desired business outcomes and priorities. 

This empowers the designer to work creatively on the customer experience moment-to-moment — the interaction patterns, design principles, edge cases.

We’ve seen a number of problems arise if user stories are written prior to or without the designer’s involvement:

* Design doesn’t have enough time to fully consider the customer experience. Instead, they’re forced to design based on a list of tactical stories possibly written from the business owner’s perspective, instead of the user’s. 
* The pre-written stories don’t match the final design, and dev has to reconcile the inconsistencies before starting work.
* The stories are incomplete. It’s hard to anticipate all the edge cases of a feature before it’s gone through the design process. 

## Story Time

Team partnership and peer review is essential to achieve strong alignment and buy-in.

**Early peer review:** After the designer has written stories, the product owner should review and provide feedback on the first draft. A second pair of eyes helps ensure focus and clarity of content. It also gives the product owner time to review the backlog as a whole to confirm that it represents the scope and priority of work.

**Full team review:** The designer presents each story in the backlog to the full team for feedback and estimation. Common results of an effective team review:

* Stories are sized
* Missed edge cases are exposed
* Hidden technical work is revealed (and added to the backlog)
* Stories are re-prioritized
* Proposed solutions are reconsidered and stories are decomposed/rewritten

**Prioritization:** Through team discussion, the team should have a good understanding of how they intend to deliver value in an incremental fashion. Now the product owner can take one more shot at the backlog to meet prioritized business & customer goals, produce a vertical slice, and/or reduce inter-story dependencies in the same sprint.

## Working on a user story

An effective user story stands on its own but is strengthened by the context you already know about the project. Whether you’re a designer working on an epic, or a developer working on an interaction story, do not work on a story that is unclear. Find time to clarify the task with the right person before moving forward.

Delivering: a story should be marked as delivered after it’s been merged to the proper environment and the test suite passes.

## Accepting user stories

You must be able to verify on a pre-defined environment that the work delivered meets the Acceptance Criteria before accepting the story.

**Right person, right story, right time.** It is important to understand who on the team has the proper skills to accept the story at hand. Design or interaction-heavy stories should be accepted by a designer, preferably the individual who created the design. If you can’t verify an engineering task, don’t accept the story — find a developer who can. Do not allow delivered stories to sit for more than a day without acceptance testing. This can unnecessarily lengthen the feedback loop, reducing positive momentum and allowing the team to forget the specifics of the work.

**Reject early, reject often.** The Reject action is the flag to begin a conversation. You are not saying that the effort put forth has no value, just that the Acceptance Criteria have not yet been met. Comments must be added along with steps to reproduce any unmet criteria. Work out with your team the right amount of information to add when rejecting. Consider using software like [Licecap](https://github.com/justinfrankel/licecap) if an animated gif may help clarify the actions you have performed.