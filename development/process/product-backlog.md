[Handbook](../../README.md) / Development / Process

# Product Backlog

The purpose of the backlog is to help prioritising what is most important to do next, and to allow for long term planning to get an idea of where we are heading.

## Backlog Building Blocks

### Epic

Epics explain strategic goals and is often modeled around how the business itself thinks about the various efforts that takes place within a project. It's the level at which the Client Sponsor and Client Management is operating, and serves as a good framework for reporting overall progress of a project. Examples of Epics could be delivering the checkout and order management flow, or launching in a new market.

### Product Backlog Item (PBI)

We use the term Product Backlog Item (or PBI, yes we actually refers to it as "PBI" in speech) to refer to an item in a backlog. "PBI" can be seen as a carrier of *User Stories* or *Requirements* .

Note that PBIs can contain multiple user stories that all align around a given feature. So in one sense, a PBI can be referred to as a Feature. Which is why we avoid using the "Feature" terminology used in Azure DevOps *Scrum* processes.

#### User Stories

Although PBIs can be formal requirement documents, we prefer the use of User Stories, as it invites more collaboration from th team.

A User Story must answer the following questions:

- Who\
Example: A customer who is looking for a particular brand
- What\
Example: Should be able to search for a brand using text input
- Why\
Example: The business carries 400 brands, and it's difficult to find a brand without typing it.

Often, we put all of this into a sentence to form a sort of requirement:

> As a customer who is looking for a particular brand, I should be able to search for a brand using text input as the list of 400 brands is very difficult to browse through.

This user story allows room for discussion:

> "Let's see here, the search could be incorporated into the site-wide search," said Levi.
> 
> "Or we could add a search box to the brand index page," said Rikard.
> 
> "**Wait!**" shouted Christopher as if he just woke up. "Why is the brand index page difficult to browse in the first place?"
> 
> Rikard and Levi sat quiet, thinking to themselves "Where did he come from?"
> 
> "Let's check," continued Christopher. "Oh, it's unordered. What if we simply make it in alphabetical order? That would surely make it easier to browse. And it will be cheaper to implement too."
> 
> Still stunned by the sudden appearance of Christopher out of nowhere, Rikard and Levi nodded in agreement. "Good point!" said Levi.

This fictional discussion, is held during the Backlog Refinement meeting to discuss new PBIs in the backlog. In this case, assuming the Product Owner agreed, the PBI will be updated to change the "What", but still retain the why. Once the team agree on the "What", the PBI is moved into the "Approved" state, as it is now approved both by the product owner and the team.

The above discussion could never have been had if there wasn't a *Who* and *Why*. Therefor, **the most essential part of a Product Owner's job is to uncover the *Who* and *Why***. The initial *What*, is primarly needed to make sense of the *Who* and *Why* and serve as a starting point for discussion.

#### Acceptance Criteria

On top of the Who, What and Why, there could be specific constraints. These are also added to the PBI. They could be technical or otherwise specific needs that must be fulfilled. In Azure DevOps, we note these down in the **Acceptance Criteria** field.

### Sprints

...

## Backlog Refinement

A backlog refinement meeting consists of two parts:

1. Approval of User Stories (see example under [User Stories](#user-stories))
2. Estimating approved PBIs

### Backlog Estimation

#### Story Points and Complexity

In order for the backlog to be able to fulfill it's purpose of long term planning, we need estimate the work inside of it. We do this using the *Story Point* metric.

We see the story point of the estimated complexity of a problem. The benefit of estimating complexity over time is that in order to estimate time, you need to know pretty much exactly what you are going to do. And you can't know exactly what you are going to do 3-4 months in advance when estimating a PBI. But you can gauge the complexity.

Think of complexity as a metric of moving parts, or surface area of a problem.

Do not think:
> ~~What are the exact steps I need to take to get from A to B?~~

Think instead:
> How many moving parts are related to the parts of the system that has to change in order to achieve the objective?

By simply tallying these up in your mind, you will be able to estimate the complexity pretty good.

Story Points, as opposed to time, is not an absolute metric. A PBI can only be estimated in relation to another PBI. So having only Story Points, we can say that **a PBI of 10 points is twice as complex as a PBI of 5 points**. In order for the long term planning to work, you need to combine Story Points with the team's **Velocity**. The Velocity is the amount of Story Points on average completed within a sprint by the team.

#### Backlog Refinement and Planning Poker

Estimation takes place in a *Backlog Refinement* meeting, using *Planning Poker*. Planning Poker is a well defined type of game where team sits down together with the [Product Owner](project-roles.md#product-owner) and [Team Coach](project-roles.md#team-coach). The whole point of the game is to gather all the perspectives of the team but at the same time avoiding team members from influencing each others estimates. For example, if you have a team of both junior and senior members, it's likely that senior members will influence junior members estimates. Purely by their seniority.

The meeting is facilitated by the Team Coach.

For each PBI the Product Owner briefly describes the PBI's intent and any specific acceptance criteria. Before estimations, members are allowed to ask for clarifications on aspects that they might not understand. The clarifications are also noted down on the PBI. It's important here that members **do not** ask leading questions which might influence the other members estimates.

Do not ask:
> Can we solve this using Excel?

Instead ask:
> Are there any particular software constraints that we need to adhere to?

After a brief round of questioning and clarifications, the team votes. Each member makes their vote in secret and all members reveal their vote at the same time. We often use Azure DevOps Estimation tool for this. When voting, members of the team gets to chose a number from the Fibonacci sequence. The Fibonacci sequence is useful because it grows ever more inaccurate the further up the sequence you go. This maps pretty well with humans ability to estimate large and complex objectives.

After the vote is revealed, in the case where most team members voted pretty similar, the average score is calculated and added to the PBI.

Sometimes team members votes very differently. If members votes are more than two numbers apart (i.e 3-13 or 2-8), the Team Coach starts by turning to the person who voted the **lowest score**. The question asked is:

> Can you please enumerate the various parts that you feel makes up the complexity of you estimate?

After which the person does just that. Then the Team Coach turns to the person who voted the **highest score** and asks the same thing.

After both has given their answers, we are left with two lists of things that makes up the complexity. The Team Coach then compares the lists, and if there are items in one of the lists that is not in the other, calls for a re-vote. In this case, all team members make a new vote based on the information that was just incovered. This is repeated until the vote is within the same three-number sequence, in which case the team is deemed to have taken everything that is known into account.

**Note** that the order in which the lowest voting person and highest voting person is asked is important. Because it's likely that the person with the highest score has more things on his or her list and we don't want that to influence the person with the lower score. Therefor, **always ask the person with the lowest vote first**.