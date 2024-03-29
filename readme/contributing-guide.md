---
description: The best way to contribute to ContentBox
layout:
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Contributing Guide

Hola amigo! I'm excited that you are interested in contributing to ContentBox CMS. Before submitting your contribution, please make sure to take a moment and read through the following guidelines:

### Code Of Conduct

This project is open source, and as such, the maintainers give their free time to build and maintain the source code held within. They make the code freely available, hoping it will be useful to other developers and/or businesses. Please be considerate towards maintainers when raising issues or presenting pull requests. **We all follow the Golden Rule: Do to others as you want them to do to you.**

* As contributors and maintainers of this project, we pledge to respect all people who contribute through reporting issues, posting feature requests, updating documentation, submitting pull requests or patches, and other activities.
* Participants will be tolerant of opposing views.
* Examples of unacceptable behavior by participants include the use of sexual language or imagery, derogatory comments or personal attacks, trolling, public or private harassment, insults, or other unprofessional conduct.
* Project maintainers are responsible for removing, editing, or rejecting comments, commits, code, wiki edits, issues, and other contributions not aligned with this Code of Conduct. Project maintainers who do not follow the Code of Conduct may be removed from the project team.
* When interpreting the words and actions of others, participants should always assume good intentions. Emotions cannot be derived from textual representations.
* Instances of abusive, harassing, or otherwise unacceptable behavior may be reported by opening an issue or contacting one or more project maintainers.

### Bug Reporting

Please make sure also that if you submit a pull request, you link it to the appropriate issue.

* ContentBox : [https://ortussolutions.atlassian.net/browse/CONTENTBOX](https://ortussolutions.atlassian.net/browse/CONTENTBOX)
* ColdBox Core : [https://ortussolutions.atlassian.net/browse/COLDBOX](https://ortussolutions.atlassian.net/browse/COLDBOX)

If you file a bug report, your issue should contain a title, a clear description of the issue, a way to replicate the issue, and any support files that we might need to replicate your issue. The goal of a bug report is to make it easy for yourself - and others - to replicate the bug and develop a fix for it. All issues that do not contain a way to replicate will not be addressed.

### Support Questions

If you have any questions on usage, professional support or just ideas to bounche of the maintainers, please do not create an issue. Leverage our support channels first.

* Ortus Community Discourse: [https://community.ortussolutions.com/c/communities/contentbox/15](https://community.ortussolutions.com/c/communities/contentbox/15)
* Box Slack Team: [https://boxteam.ortussolutions.com/](https://boxteam.ortussolutions.com/)
* Professional Support: [https://www.ortussolutions.com/services/support](https://www.ortussolutions.com/services/support)

### Pull Request Guidelines

* The `master` branch is just a snapshot of the latest stable release. All development should be done in dedicated branches. Do not submit PRs against the master branch. They will be closed.
* All pull requests should be sent against the `development` branch or the release branch for LTS
* Having multiple small commits as you work on the PR is OK - GitHub will automatically squash it before merging.
* Make sure all local tests pass before submitting the merge.
* Please make sure all your pull requests have companion tests.
* Please link the Jira issue in your PR title when sending the final PR

### Security Vulnerabilities

If you discover a security vulnerability, please email the development team at [security@ortussolutions.com](mailto:security@ortussolutions.com?subject=security) and report it to the `#security` channel in our Box Team Slack Channel. All security vulnerabilities will be promptly addressed.

### Development Setup

We have added all the necessary information for you to develop on ContentBox in our readme collaboration area and our UI Developer Docs so you can setup for UI development.

### Language Compatibility

Please make sure your code runs on the following CFML Engines:

* Lucee 5+
* Adobe ColdFusion 2018+

### Coding Styles & Formatting

We are big on coding styles and have included a `.cfformat.json` in the root of the project so that you can run the formatting tools and CommandBox scripts:

```bash
# Format everything
box run-script format

# Start a watcher, type away, save and auto-format for you
box run-script format:watch
```

We recommend that anytime you hack on the core, you start the formatter watcher (`box run-script format:watch`). This will monitor your changes and auto-format your code for you.

You can also see the Ortus Coding Standards you must follow here: [https://github.com/Ortus-Solutions/coding-standards.](https://github.com/Ortus-Solutions/coding-standards.)

### CFC Docs With DocBox

All CFCs are self-documenting, and we leverage [DocBox](https://docbox.ortusbooks.com/) to document the entire software. All functions must be properly documented using the DocBox syntax: [https://docbox.ortusbooks.com/getting-started/annotating-your-code](https://docbox.ortusbooks.com/getting-started/annotating-your-code)

### Financial Contributions

You can support ColdBox and all of our Open Source initiatives at Ortus Solutions by becoming a Patreon. You can also get lots of goodies and services depending on the level of contributions.

* [Become a backer or sponsor on Patreon](https://www.patreon.com/ortussolutions)
* [One-time donations via PayPal](https://www.paypal.com/paypalme/ortussolutions)

### Contributors

Thank you to all the people who have already contributed to ContentBox!\
We :heart: :heart: :heart: love you!

[![](https://contrib.rocks/image?repo=Ortus-Solutions/contentbox)](https://github.com/Ortus-Solutions/contentbox/graphs/contributors)

Made with [contributors-img](https://contrib.rocks)
