# Structuring Epics, Stories, Bugs and Tasks
* Contents
{:toc}

This page summarizes what an Epic, User Story, Bug, and Task is and documents our best practices for how they should be structured. Not every project will follow these practices. We’ll rely on our team norming sessions to adapt ticket writing practices so they best support the team in the context of their project.

Guidance on our approach to [writing Epics and User Stories](../product_design/how_we_write_user_stories.md) can be found here.

![Initiatives inform Epics which then inform our stories, tasks, and bugs](/assets/images/structuring_tickets/structure-overview.png)

<br>

---
## Initiatives
Initiatives are a collection of epics that drive towards a common goal (for example: “expand in to Australia” or “launch a new product that decreases costs by 7% this year”). An initiative is broader than a single epic, and may span multiple teams and multiple quarters.

## Epics
Epics convey the overall big picture priorities. They contain a group of stories (on a particular theme) that are too big to be described by a single user story. Epics are written concisely and in a way that is simple to understand.
- Epics are specific, achievable, and completable. They don’t exist forever.
- The speclet becomes the Epic once there is alignment on it. ***The Jira Epic links to the speclet.***
- Speclets are generally written and owned by the Product Manager.
- Epics do not have estimates and are likely to span multiple sprints.
- An epic may include a hypothesis. A hypothesis justifies the change and specifies what difference you expect to see as a result. The hypothesis should be based on data and include links to the data source.

### Structure of a speclet:
**Title:** Concise summary of the epic.

**Problem Summary:** A description of the problem this epic addresses.

**Vision:** A brief summary of the future state that could be achieved by completing this epic.

**Stakeholders:** A list of the primary stakeholders impacted by this epic, with a very brief (one-line) description of their role.

**Desired outcomes:** Including metrics where possible.

**High-level user stories:** High-level stories that will later be broken down into user stories for the engineering team. These are added to the speclet during the Discovery process.

**Notes:** Links to relevant documents.

#### Example speclet: 
| <a href="https://guides.labzero.com/assets/images/structuring_tickets/structure-speclet1.png"><img src="https://guides.labzero.com/assets/images/structuring_tickets/structure-speclet1.png" alt="Page one of our speclet example" width="400" ></a> | <a href="https://guides.labzero.com/assets/images/structuring_tickets/structure-speclet2.png"><img src="https://guides.labzero.com/assets/images/structuring_tickets/structure-speclet2.png" alt="Page two of our speclet example" width="400" ></a> |
|-|-|


### Example Epic in Jira:
**Title:** Concise summary of the epic.

**Description:** Link to the speclet.


--- 

## User stories
- User stories describe a small, discrete, testable piece of functionality from the perspective of the person who desires the new capability (usually a user or customer of the system).
- The fibonacci sequence is used for estimating (1, 2, 3, 5, 8). Any story with more than 3 points should be broken down into smaller stories.
  - Read about why we use these numbers in these articles by [Mike Cohn](https://www.mountaingoatsoftware.com/blog/why-the-fibonacci-sequence-works-well-for-estimating).
- Every story should have an Acceptor assigned. The Acceptor is usually decided in Storytime.
- Subtitles within the story should be bold, and bullet points or numbers used where possible.
- All user stories should be part of an epic. There are multiple user stories in an epic.
- Stories represent a full slice of functionality (ie including front end and back end).

All user stories must be:

| Letter | Meaning | Description |
|:--------|:-------|:--------|
| I | [Independent](https://en.wikipedia.org/wiki/INVEST_(mnemonic)#Independent) | The user story should be self-contained. |
| N | [Negotiable](https://en.wikipedia.org/wiki/INVEST_(mnemonic)#Negotiable) | User stories are not explicit contracts and should leave space for discussion. |
| V | [Valuable](https://en.wikipedia.org/wiki/INVEST_(mnemonic)#Valuable) | A user story must deliver value to customers. |
| E | [Estimable](https://en.wikipedia.org/wiki/INVEST_(mnemonic)#Estimable) | You must always be able to estimate the size of a user story.  A user story should not be larger than a team can complete in one sprint. If it exceeds this time-box, it should be split in a way that still delivers value to a customer.  Ideally user stories should be sized so that they are estimated to be done in half a sprint or less so that the team has visibility on their progress. |
| S | [Small](https://en.wikipedia.org/wiki/INVEST_(mnemonic)#Small) | User stories should not be so big as to become impossible to plan and prioritize. |
| T | [Testable](https://en.wikipedia.org/wiki/INVEST_(mnemonic)#Testable) | The user story or its related description must provide the necessary information to make test development possible. |

<br>

### Structure of a user story:
**Summary:** The title of the ticket (which shows up in the Backlog list). Short, descriptive, and easy to scan. If possible putting the user first.

**Description:** Expands on the title, explaining who wants the functionality, why and to what end. Format: 

**Why** In order to *...reason why the user would need to do this activity*,
**Who** I, the *...persona name, with link to their persona page*,
**What** *...need/ want/ etc.*

**Acceptance criteria:** A numbered list of functionality that the Designer or Product Manager will use to test that the story has been completed. Stories can’t be rejected for a requirement that isn’t stated here (new tickets should instead be created to cover the missed criteria).

**Out of scope:** Calls out any non-obvious functionality that is out of scope.

**Relevant tickets:** Closely related tickets that the developer should be aware of when working on this one. Use the “Link issue” feature or link to the tickets from the acceptance criteria.

**Resources:** Links to relevant designs, user flows, etc. Link to the original design (eg a screen in a Figma file) where possible, rather than attaching images to the story. 

#### Example user story:
| <a href="https://guides.labzero.com/assets/images/structuring_tickets/structure-story.png"><img src="https://guides.labzero.com/assets/images/structuring_tickets/structure-story.png" alt="Example user story" width="600" ></a> |
|-|
| <a href="https://guides.labzero.com/assets/images/structuring_tickets/structure-figma-attachment.png"><img src="https://guides.labzero.com/assets/images/structuring_tickets/structure-figma-attachment.png" alt="Example of a figma attachment" width="600" ></a> |

 
--- 
## Bugs
- Bugs address exceptions in a story or task that was delivered.
- If a story has bugs that prevent it from meeting the acceptance criteria then the story should be rejected, with the bugs noted in the comments.
  - If the bug isn’t a blocker it can make more sense to accept the story and create a new bug in the backlog.
- Bugs shouldn’t be added to an active sprint unless they are a blocker.
- Bugs can be written by the Product Manager, Designer, Engineering or Developers. They are prioritized by Product.
- Bugs are not estimated.

### Structure of a bug:
**Title:** Short and descriptive, describing the problem. Example: Product Drive doesn’t display in IE11.

**Test environment:** Short description of the environment used when the issue was experienced. This should include which browser (including version number) and which device.

**Prerequisites:** Any prerequisites required to experience the issue.

**Steps to recreate:** Steps taken to reproduce the issue.

**Results and Expected results:** State what the result of the steps is, and what the result should be. Include images where possible.

**Attachments:** Screenshots and/ or video are attached clearly showing the issue.

#### Examples:
| <a href="https://guides.labzero.com/assets/images/structuring_tickets/structure-bug1.png"><img src="https://guides.labzero.com/assets/images/structuring_tickets/structure-bug1.png" alt="Example of a bug" width="600" ></a> |
|-|
| <a href="https://guides.labzero.com/assets/images/structuring_tickets/structure-bug2.png"><img src="https://guides.labzero.com/assets/images/structuring_tickets/structure-bug2.png" alt="Example of a bug" width="600" ></a> |


 
--- 
## Tasks
- Tasks capture actionable events that need to occur during development but which don’t provide direct, obvious value to the user.
  - The output of tasks usually isn’t visible to users: ie nothing is functionally or visually different about the product when the task is done.
- In general, these tasks should align with one or more stories in the current sprint. Rogue tasks should at least raise questions about the relative priority.
- Tasks do not require estimation (although it can better inform a story estimate).
- Tasks are prioritized by the Product Manager.

### Structure of a task:
*Title:* Short description of the task

*Description:* Full summary of the task, using bullet points.

*Resources:* Links to any relevant resources.

#### Example

| <a href="https://guides.labzero.com/assets/images/structuring_tickets/structure-tasks.png"><img src="https://guides.labzero.com/assets/images/structuring_tickets/structure-tasks.png" alt="Example of a task" width="600" ></a> |
|-|

### Structure of a design ticket:
(Coming soon!)
