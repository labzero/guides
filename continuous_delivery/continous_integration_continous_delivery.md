# Continuous Integration and Continuous Delivery

The aim of Continuous Integration and Continuous Delivery (CI/CD) is a software development practice that aims to automate the building, testing, and deploying of code changes in a frequent and reliable manner. It helps to ensure that new features can be delivered faster, bugs are caught earlier, and the codebase remains more stable. To achieve faster delivery, automation is used to test and validate all changes and provide feedback to the developer on the state of the system with the inclusion of the changes.

## Continuous Integration

Pull requests to merge code changes trigger the automation pipeline. The pipeline runs validation checks and ensures the changes are ready for peer review.  The following stages go into detail about how the code changes are validated. This pipeline needs to reside in a dedicated, and preferrably ephemeral environment.

# Style and Static Analysis
1. **Style/lint checks:** Ensure consistency in coding styles and conventions, making code easier to read and understand.
2. **Static analysis scans:** Scan code for quality and potential security risks.
3. **Dependency audits:** Check third-party packages for vulnerabilities and updates.

### Building
1. **Compilation (for compiled code):** Catch syntax/compilation errors.

### Testing
1. **Unit tests execution:** New code changes should include new unit tests and modification of existing tests to ensure functionality is working as expected. 
2. **Test coverage report:** Ensures code base meets testing coverage threshold. Dips in coverage is an early indicator of risk. 
3. **PR environment deployment:** Ideally an ephemeral PR environment that will be used for functional testing.  Otherwise use a blocking environment that serializes pull request jobs during the functional tests.
4. **Database migrations:** Use a database that has similar data and identical structure as that in production. Run new migrations and verify the results are as expected.
5. **Database seeding:** Seed any test data required for functional tests.
6. **Functional/integration tests execution:** Run end-user tests. Typical example uses browser drivers that mimic user interactions with the application, in a repeatable deterministic script. 

### Code Review
1. **Peer code review and approval:** Peer review starts after all automated checks [go green](development_workflow.md#going-green).  This ensures that the changes meet the minimum validation threshold before the review begins. Any new code changes during the review will trigger the automation pipeline again.
2. **PR code merge:** Once the pull request is approved, the changes are merged. One approach is the reviewer merging the changes. This approach has faster delivery of the changes, but potentially slower response from the author if there isn't a notification built informing of merge issues.  The other approach is the author merging the changes.  This approach has the advantage that the author of the change can quickly address any potential issues with the merge. It's a norming practice that should be agreed upon by the team.  Once the PR is merged, the story is marked [delivered](development_workflow.md#delivering-a-story).

## Continuous Delivery

Merging code changes to the development branch triggers automation to deploy the code to a staging environment.

1. **QA/staging/UAT environment deployment:** Deploy to the long-lived QA/staging/UAT environment for feature acceptance.  
2. **Database migrations:**  Run any new migrations. This step should be identical to those in the PR testing stage.
3. **Database seeding:**  Populate any new seed data. Any new application specific seeds in the PR. 
4. **Feature acceptance:** Perform feature acceptance on staging environment.  Design or Product will do final acceptance in this long-lived environment.  Once validated, the ticket associated with the PR can be moved to accepted.  

## Production Deployment

A robust production deployment strategy must encompass rollback and recovery procedures for potential deployment issues. Leveraging release tagging within a version control system such as Git facilitates reverting the application to a proven, stable state. Combined with routine backups of application data and configuration, this ensures swift rollback capabilities in the event of failure. The following steps are recommended for production deployment:.

1. Create a release tag in source control. This will create a snapshot of the codebase for the code that will be deployed to production.
2. Manual approval for merging of the release tag to source control. This acts as the final trigger for deployment to production.
3. Automation triggers on the merging of the release tag to the source control. The automation should run through the build stage with the same checks as those for the continuous integration build steps.  
4. In the testing stage, full unit test suites, User Acceptance Testing (UAT) suites, and end-to-end functional testing are conducted. If the application utilizes special UAT accounts on the production environment, these are also included. The objective is to perform UAT tests that validate the deployment without affecting production data.
