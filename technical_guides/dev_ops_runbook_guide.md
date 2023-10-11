- [Runbook Guide](#devops-runbook-guide)
    - [Runbooks: A Jumping-Off Point](#runbooks-a-jumping-off-point)
    - [Playbooks and Runbooks are Different](#playbooks-and-runbooks-are-different)
    - [Everyone Uses the Runbook](#everyone-uses-the-runbook)
    - [Do You Need a Runbook?](#do-you-need-a-runbook)
    - [Runbook Early, Runbook Often](#runbook-early-runbook-often)
    - [Keep 'em Front and Center](#keep-em-front-and-center)
    - [Create Your Runbook Template](#create-your-runbook-template)
    - [Use Your Runbook Template](#use-your-runbook-template)
    - [Import Confluence Template](#import-confluence-template)
    - [Best Practices](#best-practices)
    - [Conventions](#conventions)
- [Runbook Template](#runbook-template)

# DevOps Runbook Guide

### Runbooks: A Jumping-Off Point
A `Runbook` documents how to run your application, service, or subsystem. It is a jumping-off point which provides an overview and then outlines pathways to dive into the supporting resources and documentation. This document is the source of truth for your application. Though it has the word "book" in it, a `Runbook` is more akin to a table of contents, in that relevant external systems and documents are linked from within the `Runbook`. This avoids duplication and keeps the `Runbook` clear and concise.

### Playbooks and Runbooks are Different
Our implementation of a `Runbook` is not a list of play-by-play steps, which we consider to be a `Playbook`. Relevant `Playbooks` are linked from a `Runbook`. While there is not a clear standard within the software community regarding the use of the words `Runbook` and `Playbook`, [Lab Zero](https://labzero.com)'s definition of these terms is shared among others in the field and has successfully facilitated efficiency within our client teams.

### Everyone Uses the Runbook
Everyone? Well, anyone on the team who maintains the system, responds to incidents, or requires knowledge of the system uses a `Runbook` for each service. It is a reference guide for anyone on the team, and essentially this means "everyone." The `Runbook` is created by whoever starts the project. Team members across functional units make subsequent edits in order to complete the picture of the system.

### Do You Need a Runbook?
Yes. The existence of a `Runbook` is an important part of DoD (Definition of Done) for a "production ready" system or service. A `Runbook` ensures that every element of a system is addressed and documented in a central location, allowing for expedient maturity. Trying to run a system without a `Runbook` results in divergent and compartmentalized knowledge within a team, which causes communication breakdowns during crucial moments. Don't let that happen to your team; use this guide as a template for generating a `Runbook`.

### Runbook Early, Runbook Often
Create the `Runbook` for your system **early** and modify the `Runbook` **often**. The earlier this document exists, the more traction it has within the team. Review and modify the `Runbook` with every change to the system. This increases efficiency, velocity, and uptime and reduces confusion, friction, and stress within your team. It is a shared living document which is the record of the system. Create it at the inception of a project, and keep it up to date.

### Keep 'em Front and Center
`Runbooks` are to be stored wherever your team regularly looks for information. This could be in a wiki, a code repository, or any other centralized document store that supports revision history, depending on your organization and team. The goal here is that anyone who needs to consume the document has easy access to it, and changes are tracked.

### Create Your Runbook Template
* Import this document into your system as a template. _Details provided below for Atlassian Confluence._
* Customize the template to account for proprietary business requirements or project nuances. Remove anything that is irrelevant to your team.
* Remove this entire `Runbook Guide` section such that your `Runbook` template begins with the `Overview` after the `Runbook Template` header below.

### Use Your Runbook Template
* Conform to a naming convention when you create a new `Runbook` from this template. Start the name of each `Runbook` with the word `Runbook`, ie: "`Runbook - Application Server`"
* Remove and replace each section's details with concise relevant content as instructed inline. For the sake of clarity and conciseness, do not retain the inline instructions; you can always refer back to this document or your modified template.
* Create a single index of `Runbooks` for your organization. Ensure your new `Runbook` is added to the index.

### Import Confluence Template
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
* **Share your thoughts** with us! We'd love to know how it works for you and how we can improve upon this guide and template going forward. Who knows? Maybe together with you we can convince the entire software community to adopt this standard!

### Conventions
Conventions used in the below template. 

Examples. Each section contains an example. Each example is a block quote starting with the word Example in italics. The remainder of the block quote is a fictional example of the type of content to be replaced for a given section. Any code snippets are formatted as code blocks. If something is shown, it does not necessarily mean it is applicable to your runbook. What follows is an example of an example. When making use of these examples, add, remove, or change content and formatting to suit your needs.
> _Example:_
> 
> Example text
> 
> * example text
> ```
> example code snippet
> ```
> * more example text
> 
> Example table:
> 
> | Column 1 | Column 2 | Column 3 |
> | --- | --- | --- |
> | Example data | Example data | Example data |
> | Example data | Example data | Example data |

* * *

# Runbook Template
Here it is! Everything below this point is the template to generate a new `Runbook`.

* * *

## Overview
### Description
Replace this text with a description of the functionality that the component provides for the overall system.

> _Example:_
> 
> GenericWebApp does generic things on the web.

### Architecture
Replace this with an architecture diagram or a description of the architecture.

> _Example:_
> 
> GenericWebApp consists of a Node frontend, a Ruby On Rails backend, and a PostgreSQL database.

### Maintainers
Replace this text with the maintainers of the code. If your team uses a directory, link to the directory as well as providing contact details. List the team or individuals. Subject matter experts should be called out individually.

> _Example:_
> 
> | Name | Role | Team |
> | --- | --- | --- |
> | John Doe | Product Owner | Product |
> | Jane Doe | Backend Engineer | Engineering |
> | Jo Doe | QA Engineer | Quality Assurance |

### Business Impact
Replace this text with information about how degradation or downtime affects the business. If there are any SLA (Service Level Agreement) details regarding uptime or maintenance windows to be documented or linked here, provide them.

> _Example:_
> 
> If this application encounters an outage, generic things cannot happen on the web. GenericWebApp needs to be running 24/7 and any outages are considered P1 incidents.

### Stakeholders
Replace this text with a list of individuals or teams that have a legitimate business interest in how this component functions. These people can typically be identified by thinking about where feature requests for this component come from or who is most impacted when this component is misbehaving.

> _Example:_
> 
> | Name | Role | Team |
> | --- | --- | --- |
> | Janie Doe | Corporate Sponsor | Product |
> | John Doe | Product Owner | Product |
> | Jonie Doe | Technical Project Manager | Product |

* * *

## Observability
Replace this text and the boilerplate list below with any relevant monitoring, graphing, anaylitics, log aggregation links, etc. Add a description, if possible.

> _Example:_
> 
> * [NewRelic](https://example.com) : Application metrics
> * [Grafana](https://example.com) : Graphs of system level Prometheus metrics
> * [Matomo](https://example.com) : Site traffic analysis
> * [Icinga](https://example.com) : Self hosted VM system monitors

### Logging
Replace this text with information about logging. Add details such as library used in the component for logging, where logs are stored, how they can be accessed. Add links when possible.

> _Example:_
> 
> In this case, we are presuming both internal and external log aggregation. 
> 
> * [Splunk](https://example.com) : log aggregation and dashboards
> * [ELK / Logstash](https://example.com) : log aggregation and dashboards for sensitive systems
> * Tail front-end logs
> ```
> kubectl logs -f -l app=frontend
> ```
> * Tail back-end logs
> ```
> kubectl logs -f -l app=backend
> ```

* * *

## Onboarding
Replace this text with details about how new users are onboarded.

> _Example:_ 
> 
> Follow the [GenericWebApp Setup Guide](https://example.com) to configure your dev environment.

### Repositories

> _Example:_
> 
> * [GenericWebApp FrontEnd on GitHub](https://example.com) : Node.js application code
> ```
> git clone git@github.com:genericwebcompany/GWA_Frontend.git
> ```
> * [GenericWebApp BackEnd on GitHub](https://example.com) : Ruby On Rails application code
> ```
> git clone git@github.com:genericwebcompany/GWA_Backend.git
> ```
> * [GenericWebApp Terraform on GitHub](https://example.com) : Terraform infrastructure as code
> ```
> git clone git@github.com:genericwebcompany/GWA_Terraform.git
> ```

* * *

## Admin Tasks
Replace this text with details regarding common administration tasks.

> _Example:_
> 
> Check the status of the pods.
> ```
> kubectl get pods
> ```

* * *

## Deployment / CI/CD
Replace this text with details about how a deployment of this component is handled. List or link to deployment dependencies should be documented here along with any links to relevant CI/CD jobs

> _Example:_
> 
> [Jenkins MultiBranch Pipeline Job](https://example.com) - TODO: Add overview of how pipeline works.

* * *

## Server Details
### Endpoints and IPs
Replace this text with the endpoints, commands, or other techniques to query details about the containers or servers. If it is a system with static details, provide the names and IPs of the servers.

> _Example:_
> 
> * Get all resources
> ```
> kubectl get all
> ```
> * Describe a resource (services for example)
> ```
> kubectl describe services
> ```

### Ports and Security
Replace this text with the ports on which the services are listening, as well as any security groups.

> _Example:_
> 
> * The service listens on port `443` and load balances between the front-end pods.
> * The Node.js pods are labeled `frontend` and listen on port `3000`
> * The Ruby On Rails pods are labled `backend` and listen on port `3000`
> * The PostgreSQL pod is backed by a persistent volume claim and listens on port `5432`

### Connecting to Service
Replace this text with instructions on how to connect to the pods, containers, servers, or services.

> _Example:_
> 
> Connect to pods
> ```
> kubectl exec -it <pod_name> sh
> ```

* * *

## Services
### Stopping and Starting
Replace this text with a description and examples of how to stop and start the services manually outside the context of the CI/CD job.

> _Example:_
> 
> Stop and start Apache
> 
> ```
> ssh user@example.com
> sudo service apache2 stop
> sudo service apache2 start
> ```
> 
> Cycle front-end pods
> ```
> kubectl delete pods -l app=frontend
> ```
> Cycle back-end pods
> ```
> kubectl delete pods -l app=backend
> ```


### Checking Status
Replace this text with instructions for checking the status of the servers or services. 

> _Example:_
> 
> Check Apache status
> ```
> sudo service apache2 status
> ```
> Get front-end pods
> ```
> kubectl get pods -l app=frontend
> ```
> Get back-end pods
> ```
> kubectl get pods -l app=backend
> ```

### Rebooting
Replace this text if appropriate with instructions on rebooting.

> Example:
> 
> SSH into the server and reboot.
> ```
> ssh user@example.com
> sudo su -
> reboot -h 0
> (enter name of host as requested by mollyguard)
> ```

* * *

## Configuration
### Infastructure as Code Details
Replace this text with details on where the Terraform plans, Kubernetes manifests, Dockerfiles, Chef cookbooks, etc are stored.

> Example:
> 
> * [Terraform on GitHub](https://example.com)
> ```
> git clone git@github.com:example.com/terraform.git
> ```
> * [Chef on GitHub](https://example.com)
> ```
> git clone git@github.com:example.com/chef.git
> ```

### Server Configuration Files

> Example:
> 
> * Backend Ruby On Rails Application Configuration
> ```
> config/application.rb
> ```
> * Frontend Node.js Configuration
> ```
> config/default.json
> ```

* * *

## Certificates
### Location on Server
Replace this text if appropriate with details about where certificates reside on the system.

> _Example:_
> 
> ```
> /path/to/certificate.crt
> /path/to/key.pem
> ```

### Related Guides
Replace this text with links to guides related to generating or maintaining certicates for your service.

> _Example:_
> 
> * [Playbook: Scale Pods](https://example.com) - How to scale pods up when alerted about resource thresholds
> * [Playbook: Busybox Troubleshooting](https://example.com) - How to spin up a busybox pod for troubleshooting issues

* * *

## Backups
Replace this text with details about when backups are generated and where they are stored.

> _Example:_
> 
> Hourly backups are stored here: 
> ```
> example.com:/Backups/GenericWebApp
> ```

### Backups Pruning
Replace this text with details about how backups are pruned and where any pruning scripts are found.

> _Example:_
> 
> * Nightly pruning keeps only the last complete backup of the day.
> * Weekly pruning retains only the last complete backup of each Friday.
> * Monthly pruning retains only the last complete backup of the month.


### Backups Monitoring
Replace this text with links to monitors for the recency, quantity, and size of the backups, as well as where the configuration for this monitoring is stored.

> _Example:_
> 
> [Backups Monitoring Group - Icinga](https://example.com) - This monitoring group contains separate monitors to ensure the backups are recent, there are the expected number of backups, and they within an expected size range

* * *

## License Renewal
Replace this text with details on how to renew any related licenses.

> _Example:_
> 
> TODO: Add better details about how to renew a licence, for example a Jira license.

* * *

## Further Documentation
Replace this text and the boilerplate list below with any relevant documentation links. Add a description for each link.

> _Example:_
> 
> * [Playbook: Competitive Analysis](https://example.com) - Analysis of competitive landscape
> * [Playbook: Project Charter](https://example.com) - Charter that was developed at the inception of this project

* * *

## Known Failure Scenarios
Replace this text with links to `Playbooks` which address known or common failure scenarios, examples on how to troubleshoot them, and how to resolve them.

> _Example:_
> 
> * [Playbook: Pod Scheduling Delay](https://example.com) - What to do when scheduled pods are not created in a timely manner

* * *

## Future Considerations
Replace this text with details about future considerations, with links to epics, stories, chores, or project plans if they exist.

> _Example:_
> 
> * [JIRA: Helm Chart Templates](https://example.com) - Ticket in the backlog for templatizing our Kubernetes manifests
> * [JIRA: Horizontal Pod Autoscaling](https://example.com) - Ticket in the backlog for implementing autoscaling


* * *
