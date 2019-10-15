[Handbook](../../../README.md) / Methodology / Product Backlog

# Backlog Item Types

## Epic

*Epics* model individual projects at a particular client. Often, a client has different budgets for different Epics.

## Feature

Features explain strategic goals and is often modeled around how the business itself thinks about the various efforts that takes place within a project. It's the level at which the Client Sponsor and Client Management is operating, and serves as a good framework for reporting overall progress of a project. Examples of Features could be a product page template, or payment method at checkout.

## Product Backlog Item (PBI)

Product Backlog Items (or PBIs, yes we actually refers to it as "PBI" in speech) starts out as User Stories. A User Story generally explains an acitivity that a user will be able to perform. Although sometimes it can be a limitation to a users ability to perform an action. For example "Customer must not be able to place an order without paying". The User Story should adhere to the [INVEST checklist](https://www.agilealliance.org/glossary/invest).

A User Story must answer the following questions:

- Who\
Example: A customer
- What\
Example: Should be able to search for a brand using text input
- Why\
Example: The business carries 400 brands, and it's difficult to find a brand without typing it.

The user story leaves room for discussion. The team will later discuss the *What* and come up with a proposed solution to the story in the [Backlog Refinement meeting](backlog-refinement.md).

### Acceptance Criterias

Additionally to the User Story, a PBI contains acceptance criterias. The criterias serves as contract between Distancify and the Client and specifies whether the Client has received the functionality they are paying for. Acceptance criteras are also used for evaluating whether something is a bug and covered by warranty.

Acceptance criterias are noted down as scenarios using the [Cucumber/Gherkin syntax](https://docs.cucumber.io/gherkin/reference/). These scenarios serve both as acceptance criterias and can quite easily be transformed into acceptance tests.

Refer to the [Acceptance Criteria Format](../../guidelines/acceptance-criteria-format.md) section for more details about how acceptance criterias are written.

### Form

The basic structure of a PBI is:

**Title:**

```
<Who> wants/needs/must/etc <What>
```

**Why:**

```
<Why does Who needs What?>
```

**Acceptance Criteria:**

```
Scenario 1:

- Given ...
- When ...
- Then ...
```

### Constraints

Sometimes, there are specific constraints that constrain the solution in various ways. These can be technical or business. To continue on the user story example above, there may have been a contraint saying that the order of the brands list must not be change, as it's sorted based on popularity.

### Customer Summary

Once a PBI is delivered, we note down what was actually done and how the problem was solved in the customer summary. This is a high-level explanation meant for stakeholders to understand what was actually made. Links to relevant user manual sections is also included.

### States

#### Proposed

- **New**\
The user story has been noted down by the product owner. The User Story must fulfill the criteria of a user story.
- **Refining**\
The user story is currently being refined by the team. The refinement makes sure that the PBI contains the needed acceptance criterias.
- **Ready**\
The refinement is deemed complete by the team. The assignee of the PBI will now seek to approve the acceptance criterias with the client. The question is, "Assuming the system is behaving as explained by the acceptance criteria, do we think the user story will be fulfilled?". Sometimes there is no clear answer to this question, as a complex problem does not have any guaranteed solutions, but it should be our best guess.
- **Approved**\
The PBI is approved by the client and is ready to be considered for an upcoming sprint. It's also ready to be estimated by the team.

#### In Progress

- **Committed**\
The team has committed to deliver the PBI in the current sprint.
- ***Re-opened due to bugs***\
If the PBI was previously done but bugs have surfaced, the PBI is temporarily moved into this state while the bugs are being solved.

#### Resolved

- **Implemented**\
The PBI is implemented according to the Definition of Implemented. The PBI is now assigned to the Product owner who will review the final solution to make sure it's aligned with the user story.
- **Accepted by PO**\
The solution is deemed sufficient by Product owner and the PBI is now awaiting Client acceptance. The PBI is assigned back to it's primary developer to collect the acceptance from Client.
- **Accepted by Client**\
The client/primary stakeholder has accepted the solution and the PBI is ready for delivery.

#### Completed

- **Done**\
The value is delivered to the client. This could mean that the feature is live, but value can also be delivered in other forms. Not all PBIs are feature changes. Some deliverables are documents, prototypes, or waiting in a staging environment for a future release.

## Bugs

We don't estimate bugs. Bugs are mistakes generated by us and we take full responsibility for our mistakes. Therefor Bugs should slow us down. They should lower the velocity. We must work harder to keep our pace if we introduce bugs.

For this to work, we need to have a clear definition of what a bug is.

### A bug is something that is:

- Prevents the user from accomplishing the task that the system is designed to perform or
- Prevents the system to fulfill the need that the system was designed to fulfill
- Can be tied to a previous change made by the team

### A bug is not (unless it's also anything of the above):

- Something that can be improved
- A behavior that is unexpected from the user's perspective. Because expectations are subjective and there are billions of people with different expectations. This is merely a matter of quality. A high quality system meets the expectations of most of it's users.

### Anatomy of a Bug

Since by definition, a bug is always tied to previous work, we can always assume that there is always a PBI that introduced the bug. Therefor, bugs always need to reference the PBI that it originated from. A bug always re-opens a PBI until the fix is done, judging by the Definition of Done for the team.

Apart from a reference to a previous PBI, a bug must include:

- The steps needed to reproduce/demonstrate the issue, either as a numbered list or a video. Clarity is more important than format.
- An explanation why this is a bug and what the expected behaviour should be

Feel free to use the following template when creating a bug:

```
Perform the following steps:

1.

According to the PBI that stated [...]
At step #, the system should have [...]
```

Here's an example of a good bug report:

```
Perform the following steps:

1. Go to a product listings page
2. Resize the screen/viewport so that it's smaller than 768px
3. Notice that the facets in the sidebar disappears as the viewport shrink

According to the PBI that stated that visitors (regardless of device) should be able to filter the products.
At step 3, the system should have allowed the user to filter the products using the facets.
```

### Managing bugs in Azure DevOps (Visual Studio Team Services)

In Azure DevOps, Team Sprint Boards are configured to manage bugs as sub-tasks of PBIs. This means that all bugs must have a parent PBI, and can not have child Tasks. Apart from that, Bugs and managed in the same way as regular Tasks.

When a bug is found in a PBI marked as "Done", the PBI must be re-opened until the bug is fixed. Bugs are generally put into the the current sprint.