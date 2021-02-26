[Handbook](../../README.md) / Standard Operating Proceedures / Developer

# Implement a PBI

## 1. Plan work

Once the specification has been approved, it's time to start planning the implementation work. We have an acceptance-test-driven approach, and track progress through whether an acceptance test is passing or not.

### Add scenarios to board

Start by adding a **Test** work item for each related **Scenario** of PBI.

Finding all related scenarios should be easy as long as they where properly tagged in [refinement][(write-feature-spec.md).

Once in LivingDoc, simply search for `@item:1234` (where `1234` is the PBI number). This will filter all the scenarios and only show the ones affected by the PBI.

The **Test** work item should contain a link to the scenario that it covers. The link can be copied from **SpecFlow+ LivingDoc** by clicking the ![paper clip](clip.png) icon.

### Estimate scenarios

Secondly, add an hourly estimate to each scenario, roughly estimating the time it will take to finish each scenario.

## 2. Create feature branch

Before the work of implementing a feature can begin, you must create a source branch where that work can be written in isolation.

Branches and the way we organize them is the back bone of the quality control and how software is shipped. Therefor it's **very** important to pay close attention to where, when and how you name a branch for that control not to be lost.

### Different types of software

The way we ship or deploy software differs somewhat between whay type of project you're working in. We make the main distinction between *SaaS* and *Shipped software*.

#### SaaS

**SaaS** projects are services that usually runs on hardware controlled and maintained by us. There's only a single "instance" of a SaaS service, even if they all have various test environments. The most common SaaS project you will encounter at Distancify is a customer e-commerce website, but there are others as well.

A **SaaS** service generally only have a single version in production at any given time.

![SaaS Branching](https://app.lucidchart.com/publicSegments/view/74994a86-3922-4197-b714-c4a0a8738d0b/image.png)

#### Shipped Software

**Shipped Software** is software that is shipped as a package to be used in other projects. Libraries fall within this category, but also applications that runs on the user's machine fall into this category.

A **Shipped Software** has multiple versions that must be maintained in parallell, as different consumers might be updating to newer versions in a non coherent fashion.

![Shipped Software Branching](https://app.lucidchart.com/publicSegments/view/d99bf5d7-bc4a-45c2-8566-ff2cfe02b251/image.png)

## 3. Writing code

### Discovering new scenarios

Implementing a feature means focusing intensly on a specific part of the system. This can sometimes lead to new discoveries being made that was not immediately obvious during the [refinement](/write-feature-spec.md). In this case, the scenarios should be added and forwarded to the Product Owner and Stakeholders for another review.

### Implementing logic

Logic, or code that involves conditions and performing mutations to a system's state, should be implemented according to the TDD cycle, which is very well summarized on [Wikipedia](https://en.wikipedia.org/wiki/Test-driven_development). There are dozen of other great sources on the TDD process. Ask your colleagues if you need direction or help.

#### Logs

Logging what happens in a system is of key importance. The rule of thumb is, if data changes, you log it. If a user performs an action, you log it.

The point of logging is to be able to go back and see what happened in a system to understand why the system is in it's current state. It is also useful for monitoring for load in SaaS services (number of requests, orders etc.). It can be difficult to anticipate what data you will need in the future when for example troubleshoting, so here's a checklist:

- Errors and exceptions
- State changes
- User or external system triggers an action, along with identifying information such as session ids or IP addresses, avoid GDPR-sensitive (personal) data
- User or external system input
- Background jobs/processes starting/stopping
- Progress of long running background jobs

Different levels of logging is used for different types of logs. Refer to [Logging levels](../../policies/logging-levels.md) for an in-depth explanation.

### Implementing views

Views, or "front-end code" requires a significant different approach than logical code. The "acceptance criteria" for a view is often a combination of acceptance tests but also a mockup. Mockups should generally be regarded as pixel-perfect visualizations of the final product. However many times a mockup can't cover all aspects such as interaction with all different screen sizes and input devices.

Sometimes the implemented view is a compromise between the mockup and what's technically feasible, although we should always strive to keep this to a minimum.

Due to this inexact nature of human interfaces, close communication must be had with the UX designer.

#### Pixel perfect matching

A lot of the web mockup/prototype tools these days provide crude CSS and technical details such as font sizes. These data should always be taken with a grain of salt. Very often, the exact numbers are not reliable. Also the CSS is often sub-optimal and might not take older browsers into account.

A better approach is to take the a screenshot of the mockup, putting it as a semi-transparent overlay on top of your implementation, and make sure the pixels line up. For web design, a simple tool that can help you with this is [PerfectPixel](https://www.welldonecode.com/perfectpixel/)

### Code styles and readability

We apply different code styles for different languages in order to increase readability and maintainability. If all code is written in the same style, it will be faster to read and understand.

Perferably, all projects would use the same guidelines, but they sometimes vary. This can be due to historical reasons or [Code owner](../../policies/code-owners.md) preference. Each project should detail their code style guidelines in their README file, and preferably also provide configs for linting tools. The project's [Code owner](../../policies/code-owners.md) is reponsible for setting and imposing the code style.

## 4. Committing code

Commit changes to your development branch created in step 2. Refer to our [policy on commit messages](../../policies/commit-messages.md) for more information.
