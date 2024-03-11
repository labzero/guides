## Epics and User Stories

* Contents
{:toc}

## The role of Epics and User Stories in our work 

Epics and User Stories are tools that focus our conversation around what to build and why. At the highest level, they embody the things that make our product worth building — who it’s for and what that person can do with the product to achieve their goals.

- Epics describe the vision and the outcomes we are striving to achieve and how we intend to measure success. 
- User stories generate empathy and alignment around a discrete effort and how that work will benefit the user. Writing user stories helps us come to an agreement on what needs to be done and what criteria we will use to tell when the work is complete.  

This document describes the best practices we aspire to. Not every project will follow this approach exactly. We’ll rely on our team norming sessions to decide how to adapt this approach so that it best supports the team in the context of their project.

## Writing Epics and User Stories is a collaborative process
We believe writing Epics and User Stories is a collaborative process between the Product Manager, the Designer, and a Lead Engineer. In addition to the responsibilities described below, we highly encourage our teams to pair throughout the process. 

### The Product Manager is responsible for clear epics. 
The Product Manager is responsible for defining the value the product should deliver based on our current understanding of the customer’s goals, the desired business outcomes, and priorities. 

### The Designer is responsible for the clear, actionable user stories… *unless it’s a technically-focused ticket.* 
When we translate a design into tickets ready for engineering, the Designer is the person with the greatest knowledge of the user experience and what requirements need to be reflected in the ticket. That does not mean design must do this work alone. Product and Engineering feedback is valuable here and the Designer may consider scheduling time to pair to ensure tickets are clear. 

*The exception is when the user story does not have a design component.* In these cases, someone else is the expert. These types of tickets may be written by the Product Manager or the Lead Engineer with input from Design. 

### The Lead Engineer will always be consulted on epics and design-focused stories… *and is also responsible for clear, actionable technically-focused stories when needed.* 
Without an engineering perspective, all our epics and stories are just wishes. Engineering provides a critical perspective into feasibility. They need to be kept in the loop so their team is aligned on the why behind our work. They should be consulted early and often. The Lead Engineer should have weighed in on context and design well before a ticket makes it to Backlog Prioritization. 

## Why do we approach Epics and User Stories this way? 
Our approach enables 
- the **Product Manager** to focus on the **“why,”** 
- the **Designer** to focus on the **“what,”**
- the **Engineering team** to focus on the **“how,”**

While encouraging **conversation and collaboration** along the way. 

## Our Approach: From Epic to User Story to Sprint
The full kickoff-to-backlog process is outlined in the [Discovery Journey Map](https://www.figma.com/file/I8gn3uTpbA7dakZu7xdUjj/LZ-discovery-journey-map-%5BWIP%5D?node-id=0%3A1).

The list below describes the best practices we aspire to. Not every project will follow this approach exactly. We’ll rely on our team norming sessions to decide how to adapt this approach so that it best supports the team in the context of their project. 

1. **Draft speclet** <br>
The Product Manager begins by writing a speclet that will serve as a stand-in for the epic. High-level user stories focusing on user needs are added to this document as the Discovery progresses. <br>
2. **Begin design**<br>
When the Designer has enough context on the problem (from the speclet and discovery) they begin work on designs.<br>
3. **Create Epic in Jira** <br>
Product Manager creates the Epic(s) and possibly shell user story tickets in Jira. 
Follow [this guidance](tbd) on epics.<br>
4. **Add User Stories to the Epic**<br>
When designs are agreed on, the Designer prepares the designs for handoff and [writes detailed user stories based on the designs](tbd). *If the epic doesn’t have a user interface, it may be more appropriate for the Lead Engineer to write the user stories.*<br>
5. **Preview stories**<br> 
The Product Manager, Designer, and Lead Engineer review all stories before Storytime and estimation.<br>
6. **Initial prioritization**<br> 
Product Manager prioritizes stories before Storytime so that we estimate the highest priority tickets first.<br>
7. **Storytime (estimation)**<br>
PM and Designer schedule a Storytime meeting with the sprint team. 
- If the Designer wrote the story, they take the lead in talking through it.
- Stories are discussed and estimated by those involved in delivering the story.
- Stories may be broken down into smaller tickets if needed
- User stories must have an estimation before they are considered ready to be included in a sprint.<br>
8. **Final prioritization**<br>
PM reprioritizes the backlog before Sprint Planning and Kickoff. This helps ensure the highest priority tickets are ready for the next sprint and the backlog is prioritized with this new work. <br>
9. **Sprint Planning**<br>
Meeting where we align our commitments for the next sprint with our actual capacity.<br>

Further information on [Sprint Ceremonies can be found here](../project_kickoff/ceremonies.md).

## Our responsibilities during the sprint
### Answering Questions
If questions come up during the sprint, the Designer is the first line to answer the question. They may pull the Product Manager and/or the Lead Engineer into the conversation if needed.

### Accepting User Stories
On a pre-defined environment (for example, a Staging site), we verify that the work delivered meets the Acceptance Criteria before accepting the story.

**Right person, right story, right time.** It is important to understand who on the team has the proper skills to accept the story at hand. 
- Design or interaction-heavy stories should be accepted by a designer, preferably the individual who created the design. 
- If you can’t verify an engineering task, don’t accept the story — find a developer who can. 
- Do not allow delivered stories to sit for more than a day without acceptance testing. This can unnecessarily lengthen the feedback loop, reducing positive momentum and allowing the team to forget the specifics of the work.

**Reject early, reject often.** The Reject action is the flag to begin a conversation. You are not saying that the effort put forth has no value, just that the Acceptance Criteria have not yet been met. 
- Comments must be added along with steps to reproduce any unmet criteria. Work out with your team the right amount of information to add when rejecting. 
- Consider using software like [Licecap](https://www.cockos.com/licecap/) if an animated gif may help clarify the actions you have performed.

<br>
<br>

## Related pages
- [Development Workflow](../continuous_delivery/development_workflow.md) guide
- [Definition of Ready and Done](https://labzero.com/blog/essential-working-agreements-ready-and-done) blog post
