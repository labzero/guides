# Runbook Guide and Template

### Runbooks: A Jumping-Off Point
A `Runbook` documents how to run your system. It is a jumping-off point which provides an overview and then outlines pathways to dive into the supporting subsystems and documentation. This document is the source of truth for your application. Though it has the word "book" in it, a `Runbook` is more akin to a table of contents, in that relevant external systems and documents are linked from within the `Runbook`. This avoids duplication and keeps the `Runbook` clear and concise.

### Playbooks and Runbooks are Different
Our implementation of a `Runbook` is not a list of play-by-play steps, which we consider to be a `Playbook`. Relevant `Playbooks` are linked from a `Runbook`. While there is not a clear standard within the software community regarding the use of the words `Runbook` and `Playbook`, [Lab Zero](https://labzero.com)'s definition of these terms is shared among others in the field and has successfully facilitated efficiency within our client teams.

### Everyone Uses the Runbook
Everyone? Well, anyone on the team who maintains the system, responds to incidents, or requires knowledge of the system uses a `Runbook` for each service. It is a reference guide for anyone on the team, and essentially this means "everyone." The `Runbook` is created by whoever starts the project. Team members across functional units make subsequent edits in order to complete the picture of the system.

### Do You Need a Runbook?
Yes. The existence of a `Runbook` is an important part of DoD (Definition of Done) for a "production ready" system or service. A `Runbook` ensures that every element of a system is addressed and documented in a central location, allowing for expedient maturity. Trying to run a system without a `Runbook` results in divergent and compartmentalized knowledge within a team, which causes communication breakdowns during crucial moments. Don't let that happen to your team; use this guide as a template for generating a `Runbook`.

### Runbook Early, Runbook Often
Create the `Runbook` for your system **early** and modify the `Runbook` **often**. The earlier this document exists, the more traction it has within the team. Review and modify the `Runbook` with every change to the system. This will increase efficiency, velocity, and uptime and reduce confusion, friction, and stress within your team. It is a shared living document which is intended to be the record of the system. Create it at the inception of a project, and keep it up to date.

### Front and Center
`Runbooks` are to be stored wherever your team regularly looks for information. This could be in a wiki, a code repository, or any other centralized document store that supports revision history, depending on your organization and team. The goal here is that anyone who needs to consume the document will have easy access to it, and changes are tracked.

### Create Your Runbook Template
* Import this document into your system as a template. _Details provided below for Atlassian Confluence._
* Customize the template to account for proprietary business requirements or project nuances. Remove anything that is irrelevant to your team.
* Remove this entire `Runbook Guide and Template` section such that your `Runbook` template begins with the `Overview` section.

### Use Your Runbook Template
* Conform to a naming convention when you create a new `Runbook` from this template. Start the name of each `Runbook` with the word "`Runbook`," ie: `Runbook - Application Server`
* Remove and replace each section's details with concise relevant content as instructed inline. For the sake of clarity and conciseness, do not retain the inline instructions; you can always refer back to this document or your modified template.
* Create a single index of `Runbooks` for your organization. Ensure your new `Runbook` is added to the index.

### How to Import Into Atlassian Confluence
If you're using Atlassian Confluence, follow these steps to import this Markdown and use it to generate a template:
* Click the `...` to the right of `Create` in the top nav.
* Click `Add or customize templates for the selected space` in the resulting modal.
* Next to `User Created Templates`, click the `Create New Template` button.
* Add `Runbook Template` as the Template title.
* On the blank Template page, click the `+v` button to expose more options and click the `Markup` menu item.
* Select `Markdown` in the dropdown list next to `Insert`
* Copy and paste this entire Markdown document into the text area on the left.
* After reviewing the preview pane, click the `Insert` button.
* Click `Save` button in the lower left corner.

_Optional:_ Create a Table of Contents on the right side of your Confluence template, which will allow for quicker navigation to the desired section (especially helpful in an urgent situation):
* Click `Page Layout` icon, then click `Two column section with right side-bar` icon.
* Type `Table of Contents` at the top of the left column as a heading.
* Below that, type `{Table of Contents` and hit enter. The `Table of Contents` macro element will appear.
* Click `Update` in the lower left corner.

Subsequently, when creating a new `Runbook`, select this new `Runbook Template`.

### Best Practices
* **Add** missing sections that will benefit your team or project.
* **Delete** irrelevant sections. Every team and project is different.
* **Refresh** this document as often as you make changes to the system.
* **Make it yours** with whatever changes make the template and individual `Runbooks` work for **your team**.
* **Evangelize it** within your project team and organization if it works for you.
* **Share your thoughts** with us! We'd love to know how it works for you and how we can improve upon this guide and template going forward. Who knows, maybe together with you we can convince the entire software community to adopt this standard.

* * *

## Overview
### Description
Replace this text with a description of the functionality that the component provides for the overall system.

### Architecture
Replace this with an architecture diagram or a description of the architecture.

### Maintainers
Replace this text with the maintainers of the code. If your team uses a directory, link to the directory as well as providing contact details. List the team or individuals. Subject matter experts should be called out individually.

| Name | Role | Team |
| --- | --- | --- |
| John Doe | Product Owner | Replace With John's Team Name |
| Jane Doe | Backend Engineer | Replace With Jane's Team Name |
| Jo Doe | QA Engineer | Replace With Jo's Team Name |

### Business Impact
Replace this text with information about how degradation or downtime affects the business. If there are any SLA (Service Level Agreement) details regarding uptime or maintenance windows to be documented or linked here, provide them.

### Stakeholders
Replace this text with a list of individuals or teams that have a legitimate business interest in how this component functions. These people can typically be identified by thinking about where feature requests for this component come from or who is most impacted when this component is misbehaving.

| Name | Role | Team |
| --- | --- | --- |
| Jane Doe | Corporate Sponsor | Replace With Jane's Team Name |
| John Doe | Product Owner | Replace With John's Team Name |
| Jo Doe | Technical Project Manager | Replace With Jo's Team Name |

* * *

## Observability
Replace this text and the boilerplate list below with any relevant monitoring, graphing, anaylitics, log aggregation links, etc. Add a description, if possible.

* [monitoring link](http://monitoringlink.com) todo: replace with description
* [graphing link](http://graphinglink.com) todo: replace with description
* [analytics or insights link](http://analyticsorinsightslink.com) todo: replace with description

* * *

## Onboarding
Replace this text with details about how new users are onboarded.

### Repositories
*   [repository link 1](http://gihublink.com) Replace this text with summary of what is in this repo
*   [repository link 2](http://gihublink.com) Replace this text with summary of what is in this repo

* * *

## Admin Tasks
Replace this text with details regarding common administration tasks.

* * *

## Deployment / CI/CD
Replace this text with details about how a deployment of this component is handled. List or link to deployment dependencies should be documented here along with any links to relevant CI/CD jobs

*   [CI/CD job](http://circlejenkins.com) Replace this text with a brief description if necessary.

* * *

## Server Details
### Endpoints and IPs
Replace this text with the endpoints, commands, or other techniques to query details about the containers or servers. If it is a system with static details, provide the names and IPs of the servers.

### Ports and Security
Replace this text with the ports on which the services are listening, as well as any security groups.

### Connecting to Service
Replace this text with instructions on how to connect to the pods, containers, servers, or services.

* * *

## Logging
Replace this text with information about logging. Add details such as library used in the component for logging, where logs are stored, how they can be accessed. Add links when possible.

* * *

## Services
### Stopping and Starting
Replace this text with a description and examples of how to stop and start the services manually outside the context of the CI/CD job. Examples:
```
sudo systemctl stop <servicename>
sudo systemctl start <servicename>
kubectl delete pod ...
```

### Checking Status
Replace this text with instructions for checking the status of the servers or services. Examples:
```
sudo systemctl status <servicename>
kubectl get pods ...
```

### Rebooting
Replace this text if appropriate with instructions on rebooting.

* * *

## Configuration
### Infastructure as Code Details
Replace this text with details on where the manifests, dockerfiles, configuration management, etc are stored.

### Server Configuration Files
* REPLACE\ME (Category or Service):
  * `/path/to/file/conf.conf`
  * Created by CM from [REPLACE\ME template](https://githublocation.com/thefile) (GitHub)
* REPLACE\ME (Category or Service):
  * `/path/to/file/conf.conf`
  * Created by CM from [REPLACE\ME template](https://githublocation.com/thefile) (GitHub)

* * *

## Certificates
### Location on Server
Replace this text if appropriate with details about where certificates reside on the system.
```
/path/to/certificate.crt
/path/to/key.pem
etc.
```

### Related Guides
Replace this text with links to guides related to generating or maintaining certicates for your service.


* * *

## Backups
Replace this text with details about when backups are generated and where they are stored.

### Backups Pruning
Replace this text with details about how backups are pruned and where any pruning scripts are found.

### Backups Monitoring
Replace this text with links to monitors for the recency, quantity, and size of the backups, as well as where the configuration for this monitoring is stored.

* * *

## License Renewal
Replace this text with details on how to renew any related licenses. Conversely, provide type of open source license being used or provided.

* * *

## Further Documentation
Replace this text and the boilerplate list below with any relevant documentation links. Add a description for each link.

* [https://wikilink1.com](http://wikilink1.com) - Brief description of document
* [https://READMElink1.com](http://READMElink1.com) - Brief description of document
* [https://boxlink1.com](http://boxlink1.com) (Box) - Brief description of document

* * *

## Known Failure Scenarios
Replace this text with links to `Playbooks` which address known or common failure scenarios, examples on how to troubleshoot them, and how to resolve them.

* * *

## Future Considerations
Replace this text with details about future considerations, with links to epics, stories, chores, or project plans if they exist.

* * *
