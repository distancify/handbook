[Handbook](../../README.md) / Development / Process

# Product Backlog

The purpose of the backlog is to help prioritising what is most important to do next, and to allow for long term planning to get an idea of where we are heading.

## Backlog Building Blocks

### Epic

...

### Product Backlog Item (PBI)

...

### Sprints

...

## Backlog Estimation

### Story Points and Complexity

In order for the backlog to be able to fulfill it's purpose of long term planning, we need estimate the work inside of it. We do this using the *Story Point* metric.

We see the story point of the estimated complexity of a problem. The benefit of estimating complexity over time is that in order to estimate time, you need to know pretty much exactly what you are going to do. And you can't know exactly what you are going to do 3-4 months in advance when estimating a PBI. But you can gauge the complexity.

Think of complexity as a metric of moving parts, or surface area of a problem.

Do not think:
> ~~What are the exact steps I need to take to get from A to B?~~

Think instead:
> How many moving parts are related to the parts of the system that has to change in order to achieve the objective?

By simply tallying these up in your mind, you will be able to estimate the complexity pretty good.

Story Points, as opposed to time, is not an absolute metric. A PBI can only be estimated in relation to another PBI. So having only Story Points, we can say that **a PBI of 10 points is twice as complex as a PBI of 5 points**. In order for the long term planning to work, you need to combine Story Points with the team's **Velocity**. The Velocity is the amount of Story Points on average completed within a sprint by the team.

### Backlog Refinement and Planning Poker

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