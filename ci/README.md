Continuous Integration
======================

Servers
-------

 1. CI Server: Jenkins (or Hudson, Bamboo, TeamCity, CruiseControl, Travis, etc.)
 1. Build Automation Tools: Rake (or Gradle, Make, Ant, Maven, etc.)
 1. Artifact Repositories: TestFlight (or Nexus, Artifactory, Archiva, etc.)
 1. Test Frameworks: Selenium / SauceLabs / Sauce Connect (and/or Capybara, JUnit, TestNG, Cucumber, etc.)
 1. Code Analysis: Sonar, Cobertura, etc.
 1. Code Repository: GitHub (or Stash, etc.)

Jenkins Initial Setup
---------------------

###Download and Install Jenkins###

`wget -q -O - https://jenkins-ci.org/debian/jenkins-ci.org.key | sudo apt-key add -`

`sudo sh -c 'echo deb http://pkg.jenkins-ci.org/debian binary/ > /etc/apt/sources.list.d/jenkins.list'`

`Update apt-get`

`sudo apt-get update`

`sudo apt-get install jenkins`

###Install Oracle###

This requires logging in to Oracle and accepting the license agreement.

`http://download.oracle.com/otn/linux/oracle11g/xe/oracle-xe-11.2.0-1.0.x86_64.rpm.zip`

Copy the downloaded zip file to the Jenkins server

`unzip oracle-xe-11.2.0.1.0.x86_64.rpm.zip`

In Ubuntu .rpm files cannot be run or installed so you have to download and run “alien” to convert from .rpm to .deb

`sudo apt-get install alien`

`cd Disk1/`

`sudo alien --to-deb --scripts oracle-xe-11.2.0-1.0.x86_64.rpm`

Make some configuration changes required for Oracle to run properly upon installation.

`sudo ln -s /usr/bin/awk /bin/awk`

`sudo mkdir /var/lock/subsys`

Become root and create chkconfig file.

`sudo -i`

Copy and paste this entire block into the terminal on the server as root to create the file.

`cat > /sbin/chkconfig <<-EOF`

`#!/bin/bash`

`# Oracle 11gR2 XE installer chkconfig, Only run once.`

`echo "Simulating /sbin/chkconfig..."`

`if [[ ! \`tail -n1 /etc/init.d/oracle-xe | grep INIT\` ]]; then`

`cat >> /etc/init.d/oracle-xe <<-EOM`

`#`

`### BEGIN INIT INFO`

`# Provides: OracleXE`

`# Required-Start: \\\$remote_fs \\\$syslog`

`# Required-Stop: \\\$remote_fs \\\$syslog`

`# Default-Start: 2 3 4 5`

`# Default-Stop: 0 1 6`

`# Short-Description: Oracle 11g Express Edition`

`### END INIT INFO`

`EOM`

`fi`

`update-rc.d oracle-xe defaults 80 01`

`EOF`

Log out as root and make the chkconfig file executable.

`exit`

`sudo chmod 755 /sbin/chkconfig`

Install Oracle

`sudo dpkg -i oracle-xe_11.2.0-2_amd64.deb`

You will have to change the HTTP port as 8080 is already used by Jenkins by default. 8081 was chosen during the initial install.

`HTTP port for Oracle Application Express: 8081`

Note the database listener port - no need to change the default.

`Database listener port: 1521`

You will also be asked for a password for the SYS and SYSTEM users.  Create one, save it securely, and share on an as-needed basis with appropriate team members.
After the installation is complete, set the oracle user's password, then save it securely and share on an as-needed basis with appropriate team members.

`sudo passwd oracle`

###Install and Configure Apache###

`sudo aptitude install apache2`

Enable proxy and proxy_http mods

`sudo a2enmod proxy`

`sudo a2enmod proxy_http`

Disable default VirtualHost

`sudo a2dissite 000-default`

Create Jenkins VirtualHost

`sudo vi /etc/apache2/sites-available/jenkins.conf`

`<VirtualHost *:80>`

`  ServerAdmin master@yourdomain.com`

`  ErrorLog /var/log/apache2/error.log`

`  LogLevel warn`

`  CustomLog /var/log/apache2/access.log combined`

`  ProxyRequests Off`

`  <Proxy *>`

`    Order deny,allow`

`    Allow from all`

`  </Proxy>`

`  ProxyPreserveHost on`

`  ProxyPass / http://localhost:8080/ nocanon`

`  ProxyPassReverse / http://localhost:8080/`

`</VirtualHost>`

Enable Jenkins VirtualHost

`sudo a2ensite jenkins`

Restart Apache

`sudo service apache2 restart`

###Update DNS and Set Jenkins URL###

Request DNS entry for `jenkins.yourdomain.com`

After DNS is set up, go to `/configure on` the server and update the "Jenkins URL" setting appropriately.

Jenkins URL: `http://jenkins.yourdomain.com/`

###Install Jenkins Plugins###
 * All Plugins which needed to be updated
 * active-directory
  * audit-trail 
 * build-blocker-plugin 
 * build-pipeline-plugin 
 * bitbucket-pullrequest-builder
  * cobertura 
 * copy-to-slave 
 * greenballs
  * git
  * ldap
  * maven-plugin 
 * nexus-task-runner 
 * openJDK-native-plugin 
 * rake 
 * rvm
  * sonar 
 * sonargraph-plugin 
 * sonatype-ci 
 * sauce-ondemand 
 * StashBranchParameter 
 * stashNotifier

###Connect Jenkins to Active Directory###

After making the connection to active directory, put groups / users / permissions in place and remove anonymous access to Jenkins.

###Configure SMTP###

###Use SSL###

Acquire and install the SSL Certificate for `jenkins.yourdomain.com`.

Update Apache VirtualHost to use SSL

Update Jenkins URL to use https

After SSL certificate and Apache VirtualHost are set up to use ssl, go to `/configure` on the server and update the "Jenkins URL" setting appropriately.

Jenkins URL: `https://jenkins.yourdomain.com/`


Stash Initial Setup
-------------------

Nexus Initial Setup
-------------------