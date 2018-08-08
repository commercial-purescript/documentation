# Documentation

Documentation targeting the needs of commercial PureScript users.

## About Commercial-PureScript

Commercial-PureScript is an experiment to see what documentation & libraries for PureScript would look like if it targets commercial users of PureScript and is maintainership privileges are liberally given, provided maintainers uphold the principles of the project, listed below.

The principles are not set in stone -- if you'd like clarification, qualification, addition, removal, or changes to these principles, open an issue to discuss.

Currently, the scope of this project should be limited to documentation. As much as possible, we should use libraries maintained elsewhere in the community. If a library that Commercial-PureScript users depend on has been abandoned and can't find another home, a fork can be maintained in this organization temporarily or perhaps long-term.

## Commercial-PureScript principles

- Designing and building a great application using PureScript should be a pleasurable path, rather than one full of pitfalls and regrets.
- A pleasurable experience designing and building a great application consists of analysis, appropriate architecture, and re-useable code.
- There are many types of applications that can be built with PureScript, each archetype of which should have documentation.
- Tools are a valuable part of building great applications and should have design explanations and documentation.
- This project, and projects it depends on, are likely maintained by volunteers. We should appreciate contributions made by volunteers who find the time to contribute. If you're disappointed by a project's progress, you should try to find time to realize the change yourself. If you need help contributing, ask for help in an issue or pull request on the project or in a PureScript user group.

### Documentation principles

- Documentation is easist to maintain if it follows a well-defined format, such as templates.
- *Some* documentation is better than no documentation.
- Documentation is a mapping from the problem domain to the solution domain and an explanation of the solution domain.
- Documentation readers should be expected to provide constructive feedback and improvements.
- Documentation should avoid implicit bias towards a specific project as a solution.

#### Documentation templates

The templates we use are inspired by the Divio team's analysis of good documentation, as laid out in https://www.divio.com/en/blog/documentation/

Following is a short description of this project's documentation strategies. Each of these have a different template, located as a TEMPLATE file in the corresponding directory in this project, to simplify the addition of new documentation of that type.

- Tutorials: A learning-oriented lesson.
- How-to guides: A goal-oriented sequence of steps which solves a problem.
- Explanations: An understanding-oriented explanation of background and context.
- Reference: An information-oriented complete description of a concept/idea or piece of machinery.


### Library principles

- Using and maintaining existing libraries should be preferred, presuming they generally follow the Commercial-PureScript library principles.
- Library code should be as reusable as possible.
- Generally, fast/efficient functions should not be the main priority. They can be provided separately in a peer module for situations which require it.
- Libraries should have enough maintainers to triage issues and pull requests.
- Breaking changes are acceptable if they reasonably move the library further towards these principles.
- While there is not a single "correct" abstraction, abstractions which describe the problem domain should be preferred. (Maybe?)
- A library should describe its design and principles to help ensure maintainers don't change them in a way which breaks its principles.

## Contributing

Contributions are welcome, provided they align with the goals and principles of the project.
Simply open an issue or pull request. Contributions don't have to be perfect.

### Becoming a maintainer

The responsibility of a maintainer is to stop by from time to time to triage issues and make progress on them.
If you'd like to be a maintainer, communicate with one of the existing maintainers, perhaps by opening or commenting on an issue.
Some aspects we consider when deciding whether to accept you as a maintainer:
- You understand the principles of the project.
- You have a stake in the project's success.
- You have contributed a large amount to the project.

Generally, we should easily accept a new maintainer. If problems arise in the future, we can revert changes and revoke permissions.

### Current focus

- Building documentation templates, categories, and examples. Motivated by the analysis of good documentation as laid out in https://www.divio.com/en/blog/documentation/
