# Writing a README
All code repos should include a README that gives a summary of what the code does and provides necessary instructions for setup and use.

## Formatting
A README file should generally be written in [github-flavored Markdown](https://help.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github), unless it will be presented somewhere other than GitHub. Markdown files can be previewed in editors such as [VS code](https://code.visualstudio.com/docs/languages/markdown) and [Macdown](https://macdown.uranusjr.com/), or by searching for an online Markdown editor.

Information should be split into sections that make the instructions easy to follow. Use formatting options correctly to ensure accessibility. Header levels should appropriately divide sections and subsections, and there should be a single `h1` top-level header. In general, keep in mind guidelines and best practices for writing [accesible content](https://developers.google.com/style/accessibility).

Avoid adding so much information that the README loses focus or becomes difficult to follow. Additional docs can be useful when a detailed explanation of the code or concepts is necessary. When referencing third-party software, it's generally good practice to include a link to the relevant overview or download page for that software.

## Relevant sections
A README should provide enough information for a new user to run the code. This includes requirements and prerequisites as well as code commands.

The following sections are commonly used and can serve as a starting point for a README. Documentation can grow with the codebase, and it's better to not add sections that aren't needed.

### Overview
The README should start with a brief overview that summarizes the use or purpose of the repository. If your introduction is not self-explanatory to a new user, consider adding reference links to any related third-party libraries or other concepts that might be unfamiliar.

Although not necessary, it may be helpful to include shields/badges for code coverage, passing builds, etc. to demonstrate that the code is well-maintained.

### Requirements
If there are any environment prerequisites or other steps that are required for installation of the repo, list them out before the installation section. This includes listing any requirements regarding programming language version or operating system, and any dependencies that need to be manually installed. Avoid making assumptions about the user's setup.

### Installation
Include the commands needed to install the project and any dependencies. Be sure to include any environment configuration steps. List any requirements for database setup.

### Usage
Include the commands needed to run the code (in the development environment). If the user can pass in options, list out options and flags.

If there are multiple ways to run the code (for instance, running the code offline using a local server versus connected to a dev database), discuss what is required to run the code with different settings. Include example commands and output where relevant.

Be sure to include any commands to run tests and linting. 

If the code might commonly return an error, consider adding an error/troubleshooting section.

### Build and Deployment
If relevant, include build and deployment instructions. This might include build commands and configurations that the user will have to set up.

### Other
Other commonly included sections are *contributing*, *acknowledgments*, and *license*. They may or may not be relevant depending on your project and audience.
