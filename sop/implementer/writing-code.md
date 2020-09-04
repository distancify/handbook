[Handbook](../../README.md) / Standard Operating Proceedures / Implementer

# Writing code

There are two main types of implementations that require different approaches and considerations. In both cases though, you let your acceptance test (see [Plan a PBI](plan-a-pbi.md)) drive your direction. The benefit of using acceptance tests for planning your work is that you avoid unconcious scope-creep and focus on what's important.

## Discovering new Acceptance Tests

Implementing a feature means focusing intensly on a specific part of the system. This can sometimes lead to new discoveries being made that was not immediately obvious during the [Refinement Phase](../the-distancify-model.md#refinement-phase). In this case, you should talk to the Product Developer to discuss the new discovery. Most of the time, a new acceptance test will be added to cover the scenario during the sprint.

This is normal and expected.

## Implementing logic

Logic, or code that involves conditions and performing mutations to a system's state, should be implemented according to the TDD cycle, which is very well summarized on [Wikipedia](https://en.wikipedia.org/wiki/Test-driven_development). There are dozen of other great sources on the TDD process. Ask your colleagues if you need direction or help.

### Logs

Logging what happens in a system is of key importance. The rule of thumb is, if data changes, you log it. If a user performs an action, you log it.

The point of logging is to be able to go back and see what happened in a system to understand why the system is in it's current state. It is also useful for monitoring for load in SaaS services (number of requests, orders etc.). It can be difficult to anticipate what data you will need in the future when for example troubleshoting, so here's a checklist:

- Errors and exceptions
- State changes
- User or external system triggers an action, along with identifying information such as session ids or IP addresses, avoid GDPR-sensitive (personal) data
- User or external system input
- Background jobs/processes starting/stopping
- Progress of long running background jobs

Different levels of logging is used for different types of logs. Refer to [Logging levels](../../policies/logging-levels.md) for an in-depth explanation.

## Implementing views

Views, or "front-end code" requires a significant different approach than logical code. The "acceptance criteria" for a view is often a combination of acceptance tests but also a mockup. Mockups should generally be regarded as pixel-perfect visualizations of the final product. However many times a mockup can't cover all aspects such as interaction with all different screen sizes and input devices.

Sometimes the implemented view is a compromise between the mockup and what's technically feasible, although we should always strive to keep this to a minimum.

Due to this inexact nature of human interfaces, close communication must be had with Product Developers and Stakeholders.

### Avoiding scope creep

When talking to stakeholders (and sometimes even Product Developers) you must keep a vigilant eye on the scope. Many times discussion regress into a brain storming of what could be done in the future. Direct these questions to the Product Owner instead, and try to focus on the problem at hand.

The mockup is ultimately the acceptance criteria, and only technical deviations or clarifications around this is on the agenda.

### Pixel perfect matching

A lot of the web mockup/prototype tools these days provide crude CSS and technical details such as font sizes. These data should always be taken with a grain of salt. Very often, the exact numbers are not reliable. Also the CSS is often sub-optimal and might not take older browsers into account.

A better approach is to take the a screenshot of the mockup, putting it as a semi-transparent overlay on top of your implementation, and make sure the pixels line up. For web design, a simple tool that can help you with this is [PerfectPixel](https://www.welldonecode.com/perfectpixel/)

## Code styles and readability

We apply different code styles for different languages in order to increase readability and maintainability. If all code is written in the same style, it will be faster to read and understand.

Perferably, all projects would use the same guidelines, but they sometimes vary. This can be due to historical reasons or [Code owner](../../policies/code-owners.md) preference. Each project should detail their code style guidelines in their README file, and preferably also provide configs for linting tools. The project's [Code owner](../../policies/code-owners.md) is reponsible for setting and imposing the code style.