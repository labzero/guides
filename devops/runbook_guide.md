Description
===========

_Replace this text with a description of the functionality that the component provides for the overall system._

* * *

Maintainers
===========

_Replace this text with who are the maintainers of the code. List the team, or individuals. Subject matter experts should be called-out individually._

* * *

Business Impact
===============

_Replace this text with information about how degradation or downtime affects the business._

* * *

Stakeholders
============

_Replace this text with a list of individuals, group or teams that has a legitimate business interest in how this component functions. These people can typically be identified by thinking about where feature requests for this component come from or who is most impacted when this component is misbehaving._

| Name | Role | Team |
| --- | --- | --- |
| Person1 | Backend Engineer | Team1 |
| Person2 | QA Engineer | Team1 |

* * *

Monitoring
==========

_Replace this text and the boilerplate list below with any relevant monitoring links. Add a description, if possible._

*   [link 1](http://monitoringlink1.com)
*   [link 2](http://monitoringlink2.com)

* * *

Onboarding
==========
_Replace this text with details about how new users are onboarded._

Repositories
------------
*   [repository link 1](http://gihublink.com) _Replace this text with summary of what is in this repo_
*   [repository link 1](http://gihublink.com) _Replace this text with summary of what is in this repo_
* * *

Admin Tasks
===========
 _Replace this text with details regarding common administration tasks._

* * *

Deployment / CI/CD
==================

_Replace this text with details about how a deployment of this component is handled. List or link to deployment dependencies should be documented here along with any links to relevant CI/CD jobs_

*   [CI/CD job](http://circlejenkins.com) _Replace this text with a brief description if necessary._

* * *

Server Details
==============

Names and IPs
-------------
_Replace this text with the names and IPs of the servers._

Ports and Security Groups
-------------------------
_Replace this text with the ports on which the services are listening, as well as any security groups._

Connecting to Server
--------------------
_Replace this text with instructions on how to connect to the server(s) or services._

* * *

Logging
=======
_Replace this text with information about logging. Add details such as library used in the component for logging, where logs are stored, how they can be accessed. Add links when possible._

* * *

Services
========

Stopping and Starting
---------------------
_Replace this text with a desctription and examples of how to stop and start the service manually outside the context of the CI/CD job_

`sudo systemctl stop <servicename>`

`sudo systemctl start <servicename>`

`kubectl delete pod ...`

Checking Status
---------------
_Replace this text with instructions of how to check the status of the server(s) or services._

Rebooting
---------
_Replace this text if appropriate with instructions on rebooting._

* * *

Configuration
=============

Infastructure as Code Details
------------------
_Replace this text with details on where the manifests, dockerfiles, configuration management, etc is stored._

Server Configuration Files
--------------------------
*   REPLACE\_ME (Category or Service):
    *   `/path/to/file/conf.conf`
    *   Created by CM from [REPLACE\_ME template](https://githublocation.com/the_file) (GitHub)
*   REPLACE\_ME (Category or Service):
    *   `/path/to/file/conf.conf`
    *   Created by CM from [REPLACE\_ME template](https://githublocation.com/the_file) (GitHub)

* * *

Certificates
============

Location on Server
------------------

```
/path/to/certificate.crt
/path/to/key.pem
etc.
```

Related Guides
--------------
*  _Replace this text with links to related guides._


* * *

Backups
=======
Backups are generated daily/hourly/REPLACE\_ME by "REPLACE\_ME" which is in a [backups script](http://REPLACE_ME) on REPLACE\_ME. These backup files are stored in location.com:/REPLACE\_ME via NFS mount. Additionally we are [logging](http://REPLACE_ME) each backup file creation and storing those logs on REPLACE\_ME server at` REPLACE_ME/logs.`

Pruning
-------
We have an automated [prune\_REPLACE\_ME\_backup\_logs script](http://REPLACE_ME) for pruning backup log files in REPLACE\_ME server if the log files are older than X days. A [crontab](http://REPLACE_ME) will run daily at X:XAM for pruning. Similarly, We have an [REPLACE\_ME\_backup\_prune script](http://REPLACE_ME) for pruning backup files in backup server if the files are older than X days. A [crontab](http://REPLACE_ME) will run daily at X:XAM for pruning.  

Monitoring Backups
------------------
We have REPLACE\_ME` Backups` service group to monitor X backup checks 
*   on Monitoring Server 
    *   [REPLACE\_ME Backups](http://REPLACE_ME)
*   on Dev Monitoring Server  
    *   [REPLACE\_ME Backups](http://REPLACE_ME)

* * *

License Renewal
===============
_Replace this text with details on how to renew any related licenses._

* * *

Further Documentation
=====================
_Replace this text and the boilerplate list below with any relevant documentation links. Add a description for each link._

*   [http://wikilink1.com](http://wikilink1.com) - Brief description of document
*   [http://wikilink2.com](http://wikilink2.com) - Brief description of document
*   [http://boxlink1.com](http://boxlink1.com) (Box) - Brief description of document

* * *

Known Failure Scenarios
=======================
_Replace this text with details about known or common failure scenarios, examples on how to troubleshoot, and resolve them._

* * *

Future Considerations
=====================
_Replace this text with details about future considerations, with links to tickets or project plans if they exist._

* * *
