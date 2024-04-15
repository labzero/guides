# Continuous Integration and Continuous Delivery

Continuous Integration and Continuous Delivery (CI/CD) is a software development practice that aims to automate the building, testing, and deploying of code changes in a frequent and reliable manner. It helps to ensure that new features can be delivered faster, bugs are caught early, and the codebase remains stable.

## Continuous Integration

Pull requests to merge code changes triggers the automation pipeline.  The pipeline runs validation checks and ensures the changes are ready for peer review.  The following stages go into detail how the code changes are validated.  This pipeline needs to reside in a dedicated, preferrably ephemeral, environment.

### Building
1. Style/lint checks.  Ensure consistency in coding styles and convention makes code easier to read and understand.
2. Static analysis tools.  Scans code for quality and potential security risks.
3. Dependency auditing. Checks third party package for vulnerabilities and updates.
4. Compilation (for compiled code). Catches syntax/compliation errors.

### Testing
1. Run unit tests. Code changes include new unit tests and modifying existing tests to ensure functionality is working as expected. 
2. Enforce test Coverage.  Ensures code base meets testing coverage threshold.
3. Deploy code to testing environment. Ideally an ephemeral environment that will be used for functional testing.  Otherwise blocking environment that serializes pull request pipelines for blocking functional tests. 
4. Run database migrations.  Scaffolding database and running migrations to build a consistent database that mirrors those in production. 
5. Seed any new application database data.  Also seed any test data required for functional tests.
6. Run functional/integration tests. These tests are written from the perspective of end user/application feature perspective. A typical example uses browser drivers that mimic user interactions with the application, in a repeatable deterministic script. 

### Code Review
1. Peer code review and approval.  Peer developer review once all automated checks passes.  Any changes from the review will trigger the automation pipeline again.
2. Merge code change.  Once the pull request is approved, the author merges the changes.

## Continuous Delivery

Merging code changes to the development branch triggers automation to deploy the code to a staging environment.

1. Deploy code to qa/staging environment.  This environment is a long-lived environment for feature acceptance.  
2. Run database migrations.  Run any wew migrations. 
3. Populate database seed data.  Populate any new seed data.
4. Feature Acceptance on staging environment.

## Production Deployment

Production deployment strategy should include handling rollback and recovery in case of any issues that might happen during deployment.  Using release tagging with a version control like Git can help reverting the application to a previously known working state.  Combined with regular backups of application data and configuration, will enable fast rollback in case of failure.  The follow are steps recommended when deploying to production.

1. Create a release tag in source control.  This will create a snapshot of the codebase for the code that will be deployed to production.
2. Manual approval for merging of the release tag to the source control.  This acts as the final trigger for deployment to production.
3. Automation triggers on the merging of the release tag to the source control.  The automation should run through the build stage with the same checks a those for the continous integration build steps.  
4. The testing stage would run the full unit test suites, and User Acceptance Testing suites in the functional end to end testing if the application has special UAT created accounts on the production application.  The goal is to have a set of UAT tests that validates the deployment but not impact production data.
