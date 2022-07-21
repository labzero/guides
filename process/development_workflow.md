# Development Workflow

One of the core tenets of the agile methodology is that each project team should feel empowered to design their own workflow, co-opting as few or as many agile tenets as practicable.

This document outlines Lab Zero’s typical adaptation of the agile toolkit to meet the needs of most of our customers. We sometimes further adapt our toolkit based on specific customer needs.

While each agile story presents its own unique challenges, developers adhere roughly to the following process.

## Self-selecting Stories

In most cases, developers self-assign stories directly from the top of the backlog. In practice, we typically work in loosely-structured siloes, so it’s worth considering the ongoing work of others before picking a task from the backlog. For this reason, checking in with the rest of the team via a Slack message or in-person conversation makes sense before self-selecting a story. We indicate to the rest of team that we’ve selected our tasks by assigning the stories to ourselves and moving them over from the backlog into the "In Progress" column.

## Reviewing Design Artifacts

For any given bug, task or feature story, the first unit of work for a developer is to review the story content itself along with any associated design and product artifacts (wiki pages, wireframes, mockups, etc.). If anything isn’t perfectly clear, a few back-and-forth conversations at this early stage with the product owner and/or the designers can save a great deal of time later.

## Understanding Reproduction Steps

For bug tickets, the text in the ticket will often contain steps to reproduce the undesirable behavior. Whether included in the ticket or not, it’s important to make sure the developer clearly understands how to reproduce the bug consistently before additional work begins. If there is a disconnect here, more conversations with designers and the product owner might be necessary.

Features and tasks will not contain reproduction steps; nonetheless, developers should always be able to answer the following two questions:

1. How does the affected part of the system currently function?

2. How should it function after delivering this story? 

## Designing a Testing Strategy

For most feature and bug stories, the development effort usually boils down to about 10% code/configuration and 90% test code and related artifacts. For this reason alone, it makes sense to consider how to test a story before writing any code. A pure Test Driven Development (TDD) approach would involve writing tests *before* writing code for a feature or fixing a bug. When this isn’t practical, at the very least it’s worth sketching out the rspec definitions before writing code as a way of helping developers fully understand the scope of the story. It also helps us identify edge cases and other "gotchas" early in the process. This [Lab Zero testing strategy guide](testing_strategy.md) further describes the motivations behind testing and some best practices.

## Developing/Testing a Feature (or Fixing a Bug)

Work on a story usually begins by using GitFlow in Tower (or on the git command line) to create a branch. On that branch, a developer writes tests and code/configuration until there’s complete code coverage, the feature matches the design (or the bug is fixed) and all the tests pass.

 

In most cases, all the code for a given story is contained in a single commit. (As an exception, when including an unrelated refactoring or other code change in a story, it usually makes sense to add an additional commit.) The same commit includes new tests that cover the added code. If the feature or bug contains a testable UI change, we also write a cucumber test to exercise it.  Unit tests ensure the base logic works as intended.  Functional tests ensure the application works as intended.

Use code quality scanners, such as [brakeman](https://brakemanscanner.org/) to ensure new code does not introduce vulnerabilities.  Use a code coverage tool, such as [simplecov](https://github.com/simplecov-ruby/simplecov) to ensure new code is appropriately tested.

Once a feature or bug fix is working with local dummy data, it’s a also a good idea to test it manually, if possible, in a development playground environment. If one exists, it usually has access to real(ish) development data but also allows developers to circumvent the build pipeline and deploy code to it quickly and easily. The process of testing in the development playground helps flesh out problems before the code moves through the pipeline and into the actual development, test and production environments. 

## Handing off a Feature/Bug Fix to the Build Pipeline

Once we’ve verified that our changes work locally and, if applicable, in the development playground, it’s time to deliver the changes via the build pipeline. We use a development workflow based off of the well-known git flow branching model, as follows:

1. Pull a feature branch off of a develop branch for any change

    1. branch name should be in the format: feature/<ticket_id>.<feature_name>

    2. feature branches should be short-lived, ideally less than a day or two

2. Open a change request to get the feature branch merged back to the develop branch

    3. Include test coverage alterations or additions

    4. Should be code reviewed by teammate before merge acceptance

At this juncture, we move our agile stories from "In Progress" to “In Review” to indicate that they’re ready for review.

## Committing Quality Changes

Commits should stand on their own as working software. This is to say that we should resist the urge to commit to just "save our work" when the changes are incomplete or non-functional.

A developer should be able to reasonably go to any commit in the history and find a working version of the application. This doesn’t mean a feature has to fit entirely in one commit, but that a commit should not leave the code in a state where it can not be run, or the tests aren’t green. Doing a git bisect on bad commits is a painful experience when commits are made with broken syntax and partial implementations.

## Amending Consecutive Commits and Rebasing Parallel Changes

Frequently we commit what we think are the final changes to a feature branch, push up to origin and open a pull request. Subsequently, we realize that we need to make additional changes. Ideally, all changes should be contained in one commit, so we [amend our previous commits](https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History) after making the additional changes. That process is pretty straightforward, especially in a git GUI client like [Tower](https://www.git-tower.com/help/mac/working-copy/commit-changes), but pushing changes back to the origin can be confusing. Git will indicate the presence of both remote *and* local changes. In this case, *force* pushing the changes back up to origin preserves the local changes. 

Before pushing to the remote, it usually makes sense to rebase in changes that have been made on the develop branch since the feature branch has diverged. While the changes could be brought in with a merge, we prefer using git rebase instead as it leaves a much cleaner commit history behind (also available via the [Tower GUI](https://www.git-tower.com/help/mac/branches-and-tags/merge-rebase)).

## Writing Good Commit Messages

(Related reading: [How to Write a Git Commit Message](http://chris.beams.io/posts/git-commit/))

We write our commit messages in the imperative present tense, aiming to describe what change will be made when the patch is applied. Ideally the commit message subject (the first line, 50 characters or so) reads clearly and concisely so that any reader will have a pretty good idea of what change was made without digging deeper into the code or into the story backlog. This makes the commit history significantly more meaningful, especially when another teammate (or even the author of the code!) looks through the history at a later date.

Bad commit log:

1. change footer

2. Story #19248673

3. Fixed the APIFooBarAdapter bug that was causing memory issues

4. Bug fixes

5. css

Good commit log:

1. Fix menu overlap in the shared page footer

2. Limit view of company dossier for locked content

3. Add BizBaz model class

4. Add validation for URL format on Company creation

## Creating Pull Requests

The main reason we open code change requests is so that other team members have a chance to review the code before it makes it to the main branch. Reviewing a request takes time and effort away from at least one other member of the team, so it is important to respect that and optimize the process as much as possible. Keeping requests as small as reasonably possible is a good way to ensure that a developer can quickly grok the change without having to spend significant time getting up to speed on what was done. A good bar to aim for is to have one commit per PR, and one feature per PR. Sometimes there will of course be a situation where a large number of files needs to be changed, or multiple stories may need to be accepted together, but these should both be rare exceptions. The important thing is that a pull request be realistically reviewable in only a few minutes. The larger a pull request is, the less likely it is to get a good code review. Remember that another person will be reviewing the work, so it’s important to be respectful of his or her time by not forcing a review of 13 commits and 63 modified files in order to approve the change.

Just because there were three or four sort-of-related things that could be done at once does not mean they should be lumped into one PR. The potential for one of the changes to block the other changes in the PR increases.  This is why we try out best to break stories into individual chunks of work.  As such, changes should be as small individual chunks of change.

Like with commit messages, the change request title should clearly and concisely define what change was made, often the change request title will simply be the commit message text. Any special context that is helpful for the reviewer to know should also be noted in the request description. This could include things like configuration changes that should be made, or initial conditions in the data that would be helpful for testing locally.

All change requests should be accompanied with matching alterations or additions to the test coverage. Although the peer review is a good checkpoint of code quality along the way, it is by no means a replacement for code coverage nor is it a removal of accountability if things break after the request is accepted.

## Going Green

Peer review is one of a handful of preconditions for getting a pull request on Github to "go green," which *per se* is a precondition for merging the change into the develop branch. In order for a PR to “go green” it must be approved by at least one other developer, all the rspecs and cucumbers must pass, all changes must be up-to-date with the develop branch, and, finally, the PR builder run must complete with no errors.

Often a PR will fail during a run of the PR builder. That can happen for legitimate reasons, e.g. a failing or flickering rspec or cucumber or code coverage issue. However, oftentimes it fails for reasons unrelated to changes in the PR. Some of those reasons include: failure connecting to Sauce Labs (for running cucumbers remotely), the disk running out of free space on the Jenkins server, necessary feature flags being flipped off (if a feature flipper is in play), password changes or locked accounts on service users, third-party services going offline, etc.

It's good practice to look at the console output to identify the root cause of the failure before before resubmitting the Jenkins job.
## Delivering a Story

After a PR goes green, any developer (other than the author/owner of the PR) squashes and merges the branch and deletes it (to avoid cluttering up the origin with orphaned branches). At this point, Jenkins will trigger a build to dev, test (or both). After Jenkins finishes deploying the changes, verify the changes in the deployed environment.

Finally, move the story to the "Delivered" column where the story will remain until accepted or rejected by the product owner or designer.

## Demoing Stories

At the end of each two-week sprint, developers demonstrate their work to stakeholders in the Demo/Retro/Spring Planning meeting. Following the demo, the Product Owner leads a brief retrospective and then presents the contents of the next sprint.

## Cutting a Release

To release code to production the lead developer typically follows these steps:

1. Select commits for the release, potentially cherry-picking out unwanted commits

2. Cut release branch

3. Stop builds to test

4. Push the release branch to test

	

At this point the QA team (if there is one) verifies the contents of the release in test. Once verified, the lead developer follows these steps to move the changes into production:

1. Create an RFC with the customer (if required)

2. Close release

3. Merge release branch into Master

4. Production deploy in jenkins using the release tag

