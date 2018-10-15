# Securing Your Workspace

Working securely is important to Lab Zero and our clients. With a few simple tricks you can secure your workspace.

* Enable FileVault. Your hard drive needs to be encrypted to protect the data should the machine be stolen.
    - System Preferences > Security & Privacy > FileVault (unlock) > Turn On FileVault
    - Create a recovery key and store it offline
    - Lock the System Preferences when done editing
* Require password _immediately_ after sleep or screen saver begins
    - System Preferences > Security & Privacy > General
* Require a password to login. Fresh reboots should not automatically log you in.
* Enable Screen Saver after no more than 10 minutes.
    - System Preferences > Desktop & Screen Saver > Start after: 10 minutes (or less)
* Never leave your laptop unlocked. Don't walk away for lunch or an errand without locking your computer.
    - Tip: Use Hot Corners in the Screen Saver preferences to easily lock computer when walking away.
* Keep your laptop in a safe place. e.g. Not in your car's front seat. Cars are broken into very often. If you must leave it in your car, put it in the trunk or hide it well.
* Use a password manager, like 1Password (paid) or LastPass (free) to keep your passwords hard and secure between sites. Don't write passwords down on paper or share them with others. 
* Use Multi-Factor Authentication whenever possible. As a bare minimum, use it on Github, Google, AWS, Slack and any client provided service accounts.
* Never store production secrets/keys on your machine. They should only reside on the servers that need them, and on the configuration management system (in an encrypted format).
* Do not share SSH keys with team members. Use an SSH key specific to your machine, and have that key whitelisted on the systems you need to access. This reduces the impact of a compromised key significantly.
* Clean up when a project finishes. When you wrap-up a project, take a few minutes to clean those old assets off of your machine.
* When you leave the office, lock it up and set the alarm.

## Escalation

And finally, if your workspace is compromised physically or digitally, please notify Chris, Matt and Dean as well as your team lead immediately so that the appropriate actions can be taken.



