## Delivering A Change
We use a development workflow based off of the well-known git flow branching model. Although this may vary slightly from project to project, at a high level this means we follow the basic model of:

1. Pull a feature branch off of a develop branch for any change
    1. branch name should be in the format `feature/<feature_name>.<ticket_id>`
    1. feature branches should be short-lived, ideally less than a day or two
1. Open a change request to get the feature branch merged back to the develop branch
    1. Include test coverage alterations or additions
    1. Should be code reviewed by teammate before merge acceptance

## Committing Quality Changes
Commits should stand on their own as working software. This is to say that you should resist the urge to commit to just “save your work” when the changes are incomplete or non-functional.

A developer should be able to reasonably go to any commit in the history and find a working version of the app. This doesn’t mean a feature has to be entirely in one commit, but that a commit should not leave the code in a state where it can not be run, or the tests aren’t green. Doing a `git bisect` on bad commits is a painful experience when commits are made with broken syntax and partial implementations.

## Amending consecutive commits and rebasing parallel changes
A common scenario that happens while working in a feature branch is that you commit what you think are the final changes, you push up to origin, open a change request, and then realize that you need to make additional changes. Since you want ideally keep all changes under one commit, you will need to [amend your previous commit](https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History) after making the additional changes. That process is pretty straightforward, especially if you are using a GUI client like [Tower](https://www.git-tower.com/help/mac/working-copy/commit-changes), but the confusion starts when you go to push your changes back up to origin. You will now see that you have both **remote** *and* **local** changes. In this case you will need to *force* push your changes back up to origin.
In a similar situation, you may find yourself needing to rebase in some changes that have been made on develop in the time that your branch has been alive. While the changes could be brought in with a merge, we prefer using `git rebase` instead as it leaves a much cleaner commit history behind (also available via the [Tower GUI](https://www.git-tower.com/help/mac/branches-and-tags/merge-rebase))

## Commit message format
Related reading: [How to Write a Git Commit Message](http://chris.beams.io/posts/git-commit/)

Commit messages should be in the imperative present tense and should describe what change will be made when the patch is applied. The commit message subject (the first line, 50 characters or so) should be clear and concise so that any reader will have a pretty good idea of what change was made without digging deeper into the code or into the story backlog. This makes the commit history significantly more meaningful, especially when another teammate, or future-you, is looking through the history at a later date.

Bad commit log:

1. change footer
1. Story #19248673
1. Fixed the APIFooBarAdapter bug that was causing memory issues
1. Bug fixes
1. css

Good commit log:

1. ISSUE-###: Adjust vertical item spacing on user list
1. Fix menu overlap in the shared page footer
1. Limit view of company dossier for locked content
1. Add BizBaz model class
1. Add validation for URL format on Company creation

## Pull request / merge request guideline
The main reason for opening a code change request is so that other team members have a chance to review your code before it makes it to the main branch. Reviewing a request takes time and effort away from at least one other member of the team, so it is important to respect that and optimize the process as much as possible. Keeping requests as small as reasonably possible is a good way to ensure that a developer can quickly grok the change without having to spend significant time getting up to speed on what was done. A good bar to aim for is to have one commit per PR, and one feature per PR. Sometimes there will of course be a situation where a large number of files needs to be changed, or multiple stories may need to be accepted together, but these should both be rare exceptions. The important thing is that a pull request be realistically reviewable in only a few minutes. The larger a pull request is, the less likely it is to get a good code review. Remember that another person will be reviewing your work, so be respectful of their time, and don’t make somebody have to comb through 13 commits and 63 modified files in order to review your change.

Just because there were three or four sort of related things that could be done at once does not mean they should be lumped into one PR. The problem that arises in this situation is that one of the multiple changes is blocked for some reason, and since the changes are all now linked together, all changes are effectively blocked.

Like with commit messages, the change request title should clearly and concisely define what change was made, often the change request title will simply be the commit message text. Any special context that is helpful for the reviewer to know should also be noted in the request description. This could include things like configuration changes that should be made, or initial conditions in the data that would be helpful for testing locally.

All change requests should be accompanied with matching alterations or additions to the test coverage. Although the peer review is a good checkpoint of code quality along the way, it is by no means a replacement for code coverage nor is it a removal of accountability if things break after the request is accepted.

## General editorial guidelines
We create code bases to eventually hand over to our clients. For this reason, we want to make sure that commit history, pull requests, comments, etc are all professional and easy to understand. Refrain from being sarcastic or using any language that your mother wouldn’t approve in any commit messages, change requests descriptions or code review comments. Our commit history is a representation of us as a team, and should be treated as such.

## Release Request Process
On some projects we trigger production deploys via pull requests back to master.

1. Pull release branch off of `develop` for pre-release staging
1. Open a change requests against `master` branch to start a release.
1. Acceptance of merge request to `master` triggers a release
1. `master` branch is tagged with a release identifier

