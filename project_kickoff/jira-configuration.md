<h1>Customizing Jira for agile teams</h1>

Software projects take effort to manage; that’s indisputable. In order to ensure that we’re spending our time in the most productive way, we make sure that the tools we use to help manage our projects are lightweight and focused on tracking useful information. Our development team usually prefers Pivotal Tracker and our design team likes Trello. No tool is perfect, but these two seem to have the right balance of flexibility and ease-of use while providing visibility into a team’s progress toward a goal. 

Some of our clients ask us to use their internal tools. Often, that means we use Jira. “When in Rome...” we do as the Romans do—almost.

Out of the box, Jira’s Agile module meets most of our needs, but still needs a few tweaks to make it work really well. This guide summarizes the ways we configure Jira's workflows to support a lightweight process that fits with Lab Zero’s agile software development practice.  

<h2>Limit the Types of Tickets</h2>
Out-of-the-box Jira supports many kinds of tickets— too many kinds of tickets to be honest. We typically find that we only need a few. Here are the ones we use:

- Story
- Bug
- Task
- Epic (not a ticket type)
- Custom Workflows

<h3>Workflow</h3>

We keep the workflow straightforward. 

For stories with points, we want the work to be reviewed by another developer, delivered on a test server, and clearly be ready for acceptance or rejection by the Product Manager or Designer. 

**ADD IMAGE

<h3>Accept Workflow</h3>
For stories with points, we want the work to be reviewed by another developer, delivered on a test server, and clearly be ready for acceptance or rejection by the Product Manager or Designer:

**ADD IMAGE

<h2>Filters</h2>
**Add text**

<h2>Columns</h2>
The project’s “Board View” should clearly show the current state of the sprint. On the Board view in Jira we show tickets that are:

- To Do
- In Progress
- Blocked
- In Review (ready for another engineer to review and merge)
- Delivered (this is the signal to the PM/Designer/QA to start testing)
- Accepted

This view gives us an understanding of some interesting project traits:

- What stories are ready to be accepted by the Product Manager?
- Is there too much work in-progress?
- Who has too many stories in-progress? (Implicit call-to-action: Go ask them why!)
- What should be accepted & working on the test server right now?

![Jira configuration](/assets/images/Jira_column_configuration_backend.png)

<h2>Reports</h2>
Not a whole lot to report here (no pun intended). We generally don’t need a chart to tell us if our flow is healthy, but one of our teams uses the burn-down chart during the sprint to keep their eyes on the prize. We wouldn’t grade ourselves on our burn-down charts, but if we see a consistent pattern that affects our ability to deliver working software—e.g. never burning down or adding too many story points late in the sprint—we’d take corrective action.

That team often sees burn-downs like this:

![Jira Report](/assets/images/jira-report.png)

Team X has been using the burndown chart to motivate the team to put more effort into the sprint beginning (vs. goal-posting delivery and acceptance of last-minute changes).
One client asked us to include a listing of stories delivered during a given invoice period. e.g.:
project = TX AND status in (Resolved, Done, Delivered, Confirmed, Finished, Rejected) AND updated >= 2015-06-01 AND updated <= 2015-06-30 AND assignee in (membersOf("Team X"))

<h2>Conclusion</h2>
Yes, Jira can work for lean/agile/kanban design and development teams. We’ve been using Jira configured this way for many years and it is working well for us. Here’s a recap of our tricks:

- Limit the number of ticket types to the few that the team uses
- Customize the workflows by ticket type
- Customize default columns on boards
- Share handy filters with the team
