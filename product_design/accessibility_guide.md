# Accessibility

## Accessibility concerns that impact our users
“Accessibility is the practice of making your websites usable by as many people as possible — we traditionally think of this as being about people with disabilities, but really it also covers other groups such as those using mobile devices, or those with slow network connections.”

[What is accessibility](https://developer.mozilla.org/en-US/docs/Learn/Accessibility/What_is_accessibility)

**Common impairments:**
- Visual
- Hearing
- Mobility
- Cognitive
- Technological

## Why we develop with accessibility in mind
15% of the world's population, have some form of disability (WHO reporting)

- It’s the kind and right thing to do
- There are often legal implications for ignoring accessibility
- For some clients, this is an internal requirement
- We gain SEO and general performance improvements
- If it’s accessibility friendly, all users benefit

## Available tools to enable developing for accessibility

- Our own skills and experience: We develop expertise in the practices and patterns that break accessibility.
- The web is already accessible by default: Semantic html is 100% accessible in its natural state.
- The WAI-ARIA spec enables non-semantic HTML to retain its semantic intent. While not ideal, this solution mitigates the level of refactoring required on exisiting projects. ARIA is also key to hiding elements from screenreaders as needed.

## Accessibility testing
We start with a baseline of readily available tools for testing and add the appropriate addtional tools as needed.

### Planning for accessibility

- [DIY Accessibility Checklists](https://dap.berkeley.edu/testing/checklist-manual-reviews)
- [Screen reader support for hidden content](https://stevefaulkner.github.io/HTML5accessibility/tests/hidden-2016.html)
- [Accessibility for Teams](https://accessibility.digital.gov/)

### General accessibility testing

- Built in Chrome Accessibility tools are available in the Dev tools under Audits.
- [WAVE evaluation tool](https://wave.webaim.org/) works similarly and is created by WebAIM
- [Pa11y.org](https://pa11y.org/) is a suite of open source testing tools including command line utilities and a cross-platform GUI application.
- [axe](https://www.deque.com/axe/) is an open source rules library for accessibility testing.
- Navigate through the project using Voice Over (on Apple products), keyboard navigation, turn on high contrast mode, etc. We use the browser's and OS’s built-in tools to see what it looks like to someone using them.

### Color blindness testing
Other options are helpful for the planning and design stages of a project such as color blindness simulators and contrast ratio checkers.

- [Contrast Grid](https://contrast-grid.eightshapes.com/)
- [Contrast Ratio](https://contrast-ratio.com/)

## Incorporating accessibility testing into our workflows
- When practicable, we involve people from the groups the project is serving to help develop the tools we're building.
- We explore the impact of new frameworks, fonts, and other changes to a project before implementing them to understand the impact they will have on accessibility.
- We test early and often for potential accessibility issues.
