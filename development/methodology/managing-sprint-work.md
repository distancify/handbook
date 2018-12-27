[Handbook](../../README.md) / Development / Methodology

# Managing Sprint Work

*This article currently referes to how we manage work within Azure DevOps.*

The team may use Tasks within a sprint to keep track of what needs to be done. A PBI may have one or more Tasks. It's the effort attached to Tasks that is powering the Burn down chart. Although Azure DevOps insist on referring to Task effort as "Hours", it's **recommended to see the number as a complexity effort** as that will generate a much more useful burndown chart. I.e tracking hours is just letting you know if people are at work or not. It doesn't show actual progress. At Distancify, we value progress over work.

**It is paramount that the team decides on a common unit for the Task effort.**

Bugs can be seen as a type of Task. It uses a different Work Item Type than Task but is always connected to a parent PBI and is handled the same way as a Task on the Sprint board. For more details, refer to the [Product Backlog/Bugs](product-backlog.md#bugs) section. For the rest of this article, the term **Task refers to both Tasks and Bugs**.

## Workflow / States

### Product Backlog Items

Within a sprint, a PBI should always start out in the "Committed" state. The PBI will stay in this state until it's finished, given the projects Definition of Done. The team should set the state of the PBI to Done whenever they think that the PBI's requirements has been met. For more details around the PBI lifecycle, refer to the [Product Backlog](product-backlog.md) article.

### Tasks

Tasks follow a specific workflow throughout the Sprint which is modeled by a set of states. These states tells everyone in the team where a Task is on the path to production. On the sprint board, each state is represented by a column.

Here follows a brief description of each state:

#### To do

**To do** is where Tasks hang out before anyone has started working on them. It's a good idea not to assign these tasks to specific members as that may unnecessarily constrain other members way of thinking about who can do which task. It may also scare away less experienced members of the team.

#### In progress

**In progress** is where the work is being done. A Task in this state must be assigned to someone. Even if there are multiple peope contributing to solving a task, either by clever cooperation or pairing, there must be exactly one person who owns the task and can be held accountable for moving it forward. This does not mean that the assignee is on his or her own. Asking for help is greatly appreciated. But the assignee will be the go to person for anyone wondering about the state of a given Task.

#### Review

- **Review** is for your peers to review your work, such as code review or visual review. A review could also be a validation of a performed configuration change that isn't part of the source code repository. For more details around intricacies of the reviewing process, refer to the [Reviewing Work](reviewing-work.md) article.

Sometimes a task can be reviewed on it's own, such as a bugfix. Sometimes a PBI is reviewed as a whole. In the latter case, all tasks should stay in review until properly reviewed. PBIs however, do not has a "In review" state. This is because it's not really interesting to know whether a PBI is in review or not. Review only concerns the team and the immediate stakeholders the team currently works with. As a Client Sponsor or Product Owner, the review phase is not interesting.

#### Done

**Done** is when the task is reviewed and merged into the master or feature branch. Tasks of a given PBI is usually merged as a whole once the PBI is done, while Bugs that occur after a PBI has been shipped is generally considered *Done* once the bugfix is live. For more details around how we work with branches, refer to the general [Branching](../guidelines/branching.md) guidelines or check with your current project.

## Testing

Most of the testing is handled by the team members as part of the **In progress** Task state. Regardless whether the tests are implemented using automatic testing techniques or manually tested, we expect all code that goes into review to be tested to make sure that the system is working beyond reasonable doubt.

However, in some cases, it can be impossible to fully test a feature due to for example external dependencies or a lack of good test infrastructure. In this case, a new task of type **Test** should be added to the PBI that details the test.