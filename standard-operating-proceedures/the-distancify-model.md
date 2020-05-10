[Handbook](../../README.md) / Standard Operating Proceedures / 

# The Distancify Model

## Introduction

The Distancify Model is an evolving process integration the business and sales process together with the development process. It's a combination of industry best practices put together in a way to fit our way of doing business and the way we develop software.

It has undergone several iterations over the years and is often changed in both small and large ways in order to improve. This document aims to describe the current version.

## Goals

Some of the key goals of the model are:

- Delivery accurate estimations as early as possible
- Minimize and balance risk for all parties involved
- Minimize waste - optimize efficiency

## The Development Cycle

### Defining Phase

_1-6 months before delivery_

Everything starts by defining the problem. A problem should be described as a user story. User stories generally start off large and vague. The goal of the user story is to capture the user's need while providing enough information to the development team in order to make an estimation.

The work of defining stories is owned by the Product Owner Team (POT), which should consist of a Product Developer from Distancify, and at least one representative from the customer. The work is practically led by the Product Developer from Distancify, who is an expert in the process of defining stories and the Distancify Model. As Distancify works in the e-commerce niche, a Distancify Product Developer is expected to be well educated in the e-commerce domain. This further accellerates the defining of stories.

In determining what is needed for a user story, a good rule of thumb is to think of it as an actual story. The user stories should tell an actual story. And the story should explain the problem and the intent of the user. Sometimes that can be done in a few sentences. Sometimes it needs epics, story maps, wire frames or even mood boards. More often than not, they need an actual person to also tell that story. So recording a short video telling the story could be a useful tool as well.

The members of the POT may not have all of the knowledge to actually produce this content, which is why they need access to specialized competence depending on the subject. Distancify aims to have the resources to cover all of these areas, but sometimes the customer have in-house or 3rd party vendors or consultants that can help out as well, which is always welcome.

Once the POT determines a user story or epic to be sufficiently defined, the story is told to the development team that makes an estimation of the effort needed to complete the task. It is this estimation that serves as the basis for the cost of the user story, as the customer pays a fixed price for each delivered story.

If a story gets too high estimation, that is to be regarded as a risk of the story being vague (inaccurate estimation) or just too big, and the POT should make an attempt at further splitting the story into smaller parts.

Once a story is fully defined, it's either:

- Planned into a future iteration
- Stored in the backlog

If the customer can't make a commitment to buy the story right now, it can be stored in the backlog, outside of the delivery plan for a while. Stories that has lingered in the backlog for long enough are usually simply deleted, as they tend to grow more inaccurate over time as the system keeps evolving.

### Refinement Phase

_1-4 weeks before Implementation Phase_

Stories are delivered in iterations. But before the iteration and implementation can begin, the stories must be further refined. In the refinement process acceptance tests are developed. Acceptance tests are feature based. Often user stories in an iteration targets the same feature, which is why some acceptance criterias overlap several user stories.

Acceptance criterias serves as a form of contract between Distancify and the customer, and they must be agreed upon by both parties before the implementation can start.

Acceptance criterias are written in Gherkin syntax and stored in a separate code repository, which means the approval of acceptance criteras can be formalized as pull requests. Each pull request is referred to as a "refinement". This code repository is known as the "spec repo" and follows the naming convention [Project name].spec. Each refinement generally maps all user stories for a given feature in a specific iteration. Each refinement's branch should follow the naming convention [planned iteration]/[feature or story]. The pull request should reference all user stories that the refinement is based on.

Important: Once a refinement is accepted by all parties, it is not "completed", meaning the changes does not get merged into the central branch. This completion is done as part of the finalizing of the sprint, when the system is actually behaving according to this new set of specifications.

If a refinement is not done before an iteration starts, it's generally pushed into the next iteration, which is why it's important that the delivery plan is made well in advance to let the refinement be done in time.

The refinement process is managed by the POT team with input from stakeholders.

Sometimes, although it should be rare, new discoveries are made during the refinement process which alters the user stories. In this case, the feature or stories may go back to the previous phase for further defining.

### Implementation Phase

_3 weeks_

The implementation phase happens during the much talked about "iteration". This is a 3 week period where the development team works focused on implementing the acceptance criterias. The development may consist of designing and implementing a front-end feature as well as specifying and implementing a back-end process or integration.

As an iteration starts, the team is introduced to the acceptance criterias by the Project Developer. Continuous communication between the team and Product Developers are encouraged, but should not be required.

The team assigns each user story in the iteration to a single team member. This person is responsible for delivering the user story. The user story is then broken down into smaller tasks by the responsible team member. Each task is estimated in actual time it should take to accomplish.

Tasks are useful in order for the team to find capacity bottlenecks. They are also useful when having multiple team members cooperate on the same story. Sometimes a story might need graphical design and implementation done by two separate members.

Acceptance tests work items are also created and added to the board. These serves to track the completion of the actual requirements aggreed to with the customer.

Once a story is complete, the responsible team member records a short demo explaining how the system works and how it now delivers the value described by the user story.

By the end of the sprint, all acceptance criterias should be passing. This should be proved by either an automatic test or a documented manual test. Once the sprint ends, the new specifications are merged into the project's spec repo's master branch.

### Deployment

Demos should be handed to the POT and the customer's stakeholders. If the customer has one, the new features should be deployed to a staging environment. The delivered user stories are invoiced as part of closing the sprint. Should there be any bugs after the sprint is closed, Distancify will fix them free of charge.

The customer then decides when the features should be deployed to production.

### Troubleshooting Guide

1. The team must constantly ask the POT for clarifications or verification

   If a repeating pattern of required communication appears, it's likely that the Defining phase is not defining the user stories well enough. A rule of thumb is that user facing features should come with a wireframe describing the overall layout of information. A back-end integration should come with a specification of data points that are to be transferred in the integration. If the integration is to be connected to an existing interface, then a reference to the existing interface should be part of the story definition, and the behavior of the interface should be encoded into the refinement.