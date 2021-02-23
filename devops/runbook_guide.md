# Runbook Guide and Template

### Who Uses a Runbook?
> _Teams who maintain software services should maintain a `Runbook` for each service. It may be created by a `DevOps` Engineer, and likely will require input from Software Architects or Engineers and Product Owners. It can be maintained by anyone with the necessary information to complete the picture of the system. It is generally used by Systems Administrators, `DevOps` Engineers, `NOC` (Network Operations Center) Engineers, `SREs` (Site Reliability Engineers), or anyone else on the team tasked with maintaining the system or responding to incidents._

### What is a Runbook?
> _In support of DevOps practices, a `Runbook` documents how to run your system. Relevant external systems and documents should be linked from within the `Runbook`. This avoids duplication and keeps the `Runbook` clear and concise._

### What is NOT a Runbook?
> _Our implementation of a `Runbook` is not a list of play by play steps, which we consider to be a `Playbook`. Relevant `Playbooks` can and should certainly be linked from a `Runbook`. While there is not a clear standard within the DevOps community regarding the use of the words `Runbook` and `Playbook`, [Lab Zero](https://labzero.com)'s definition of these terms is shared among others in the field and has successfully facilitated efficiency within our client teams._

### Where is a Runbook?
> _Wherever your team stores their documentation is where the `Runbook` should exist. Likely this will be in a wiki, possibly with in a `DevOps` space. See our instructions in the How To section below for importing this Markdown document into a Confluence wiki. Possibly you will store the Markdown as is within your code repository, depending on the makeup of the team. The goal here is that anyone who needs to consume the document will have easy access to it._

### When to Use This Guide
> _NOW! Create the `Runbook` for your system **early** and modify the `Runbook` **often**. We have found the best results from this approach. The earlier the team is aware that the `Runbook` exists and is a shared living document which is intended to be the overall document for the system, the better the likelihood of success. This, coupled with the best practice of reviewing and modifying the `Runbook` with every change to the system, will increase efficiency, velocity, and uptime and reduce confusion, friction, and stress within your team._

### Why Use a Runbook? Why Use This Guide?
> _If you're not convinced by this guide, see our [Blog Post](https://404.noblogpostyet.labzero.com) on the subject._

### How to Use This Guide
* _Import this document into your wiki or other document management system as a template. Then remove this instruction._
* * _TODO: Instructions for importing into Atlassian Confluence._
* _Customize the template to account for proprietary business requirements or project nuances. Then remove this instruction as well as any instructions irrellevant to your team._
* _When using the template to create new `Runbooks`, remove this entire `Runbook Guide and Template` section such that the `Runbook` begins with the `Overview` section._
* _Conform to a naming convention of your determination, possibly starting the name of each `Runbook` with the word "`Runbook`."_
* _Remove and replace each section's details with concise relevant content as instructed inline. For the sake of clarity and conciseness, do not retain the inline instructions; you can always refer back to this document or your modified template._
* _Create an index of `Runbooks` for your organization if it doesn't exist. Ensure your new `Runbook` is added to the index._
* _Share your thoughts with us! We'd love to know how it works for you and how we can improve upon this guide and template going forward. Who knows, maybe together with you we can convince the entire DevOps community to adopt this standard._



* * *

## Overview
### Description
> _Replace this text with a description of the functionality that the component provides for the overall system._

### Architecture
> _Replace this with an architecture diagram or a description of the architecture._

### Maintainers
> _Replace this text with the maintainers of the code. If your team uses a directory, link to the directory as well as providing contact details. List the team or individuals. Subject matter experts should be called out individually._

| Name | Role | Team |
| --- | --- | --- |
| John Doe | Product Owner | Team1 |
| Jane Doe | Backend Engineer | Team2 |
| Jo Doe | QA Engineer | Team3 |

### Business Impact
> _Replace this text with information about how degradation or downtime affects the business. If there are any SLA (Service Level Agreement) details regarding uptime or maintenance windows to be documented or linked here, provide them._

### Stakeholders
> _Replace this text with a list of individuals or teams that have a legitimate business interest in how this component functions. These people can typically be identified by thinking about where feature requests for this component come from or who is most impacted when this component is misbehaving._

| Name | Role | Team |
| --- | --- | --- |
| Jane Doe | Corporate Sponsor | Team1 |
| John Doe | Product Owner | Team2 |
| Jo Doe | Technical Project Manager | Team3 |

* * *

## Observability
> _Replace this text and the boilerplate list below with any relevant monitoring, graphing, anaylitics, log aggregation links, etc. Add a description, if possible._

* _[monitoring link](http://monitoringlink.com) todo: replace with description_
* _[graphing link](http://graphinglink.com) todo: replace with description_
* _[analytics or insights link](http://analyticsorinsightslink.com) todo: replace with description_

* * *

## Onboarding
> _Replace this text with details about how new users are onboarded._

### Repositories
*   [repository link 1](http://gihublink.com) _Replace this text with summary of what is in this repo_
*   [repository link 2](http://gihublink.com) _Replace this text with summary of what is in this repo_

* * *

## Admin Tasks
> _Replace this text with details regarding common administration tasks._

* * *

## Deployment / CI/CD
> _Replace this text with details about how a deployment of this component is handled. List or link to deployment dependencies should be documented here along with any links to relevant CI/CD jobs_

*   [CI/CD job](http://circlejenkins.com) _Replace this text with a brief description if necessary._

* * *

## Server Details
### Endpoints and IPs
> _Replace this text with the endpoints, commands, or other techniques to query details about the containers or servers. If it is a system with static details, provide the names and IPs of the servers._

### Ports and Security
> _Replace this text with the ports on which the services are listening, as well as any security groups._

### Connecting to Service
> _Replace this text with instructions on how to connect to the pods, containers, servers, or services._

* * *

## Logging
_Replace this text with information about logging. Add details such as library used in the component for logging, where logs are stored, how they can be accessed. Add links when possible._

* * *

## Services
### Stopping and Starting
_Replace this text with a description and examples of how to stop and start the services manually outside the context of the CI/CD job. Examples:_

`sudo systemctl stop <servicename>`

`sudo systemctl start <servicename>`

`kubectl delete pod ...`

### Checking Status
_Replace this text with instructions for checking the status of the servers or services. Examples:_

`sudo systemctl status <servicename>`

`kubectl get pods ...`

### Rebooting
_Replace this text if appropriate with instructions on rebooting._

* * *

## Configuration
### Infastructure as Code Details
_Replace this text with details on where the manifests, dockerfiles, configuration management, etc are stored._

### Server Configuration Files
*   REPLACE\_ME (Category or Service):
    *   `/path/to/file/conf.conf`
    *   Created by CM from [REPLACE\_ME template](https://githublocation.com/the_file) (GitHub)
*   REPLACE\_ME (Category or Service):
    *   `/path/to/file/conf.conf`
    *   Created by CM from [REPLACE\_ME template](https://githublocation.com/the_file) (GitHub)

* * *

## Certificates
### Location on Server
> _Replace this text if appropriate with details about where certificates reside on the system._
```
/path/to/certificate.crt
/path/to/key.pem
etc.
```

### Related Guides
> _Replace this text with links to guides related to generating or maintaining certicates for your service._


* * *

## Backups
> _Replace this text with details about when backups are generated and where they are stored._

### Backups Pruning
> _Replace this text with details about how backups are pruned and where any pruning scripts are found._

### Backups Monitoring
> _Replace this text with links to monitors for the recency, quantity, and size of the backups, as well as where the configuration for this monitoring is stored._

* * *

## License Renewal
_Replace this text with details on how to renew any related licenses. Conversely, provide type of open source license being used or provided._

* * *

## Further Documentation
_Replace this text and the boilerplate list below with any relevant documentation links. Add a description for each link._

*   [https://wikilink1.com](http://wikilink1.com) - Brief description of document
*   [https://READMElink1.com](http://READMElink1.com) - Brief description of document
*   [https://boxlink1.com](http://boxlink1.com) (Box) - Brief description of document

* * *

## Known Failure Scenarios
_Replace this text with links to `Playbooks` which address known or common failure scenarios, examples on how to troubleshoot them, and how to resolve them._

* * *

## Future Considerations
_Replace this text with details about future considerations, with links to epics, stories, chores, or project plans if they exist._

* * *
