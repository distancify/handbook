# The Sprint Cycle

## Sprint

A sprint is a timeboxed set of time. Each sprint should be comparable in the number of mandays. Planned vacation and national holidays should be taken into account when mapping out upcoming sprints to make sure each sprint is as comparable as possible. However, there will always be unforseen events that occur and limits our resources, such as sick days and other emergencies. These are expected to be averaged out over time and should not be taken into account when planning sprints.

In summary, these events may increase the number of (calendar) days in a sprint:

- Planned vacation or similar reasons we might lack people, such as planned parental leave
- National holidays
- Team building events

These events may not increase the number of (calendar) days in a sprint:

- Sick days
- Bad luck
- Mistakes or obvious misunderstandings or miscommunications made by us

Note that a sprint can never be extended **ONCE IT HAS STARTED**. The number of calendar days in a sprint is set before it starts and never changes.

## Sprint Commitment

Every sprint should be of equal size. We do not strive to increase the sprint size for a given project over time. We favor predictability over sheer output. However, we hope, and always strive, to increase the overall velocity of the team by removing things that slows us down. We don't increase velocity by working longer hours. We save our resources for those times where we fight an uphill battle. An uphill battle brought upon us by ourselves by mistakes or over-promising.

It is the team that ultimately makes the commitment and delivers it to the customer and product owner. From the start of the sprint to the end of it, the team has full ownership of delivering on the needs specified in the items in the sprint.

## Sprint Summary

At the end of each sprint, the team compiles a sprint summary. This summary should be in written form and distributed to the custoemr and product owner, often as part of the Sprint Demo meeting.

The sprint summary should contain the following:

- A short story (1-2 paragraphs) that summarises the overall theme of the sprint. What was the focus and how the work progressed
- A list of the PBIs that was committed to
- A list of which PBIs has been delivered
- A list if things that was done, PBIs or otherwise, that was not specified in the commitment but was done anyway

## Ritual: The Sprint Demo

A sprint demo is where the team sits down together with stakeholders and product owner and shows the result of what has actually been done. Some features will be more visual in it's nature and will always be easier to show. But remember that if a PBI solves a problem for someone, there should always be a way of proving or showing that the system now solves it.

The meeting can be either physical or remote. The important thing is that all the necessary stakeholders and representatives from the team is available.

The meeting should be held within the last two days of the sprint ends to avoid interfering with the next sprint. Since committing to the next sprint is part of what is done in the Sprint Demo no work on the next sprint can begin before the meeting is held.

Since the team may be working on multiple projects in parallel in the sprint, and each project require a Sprint Demo, the meetings must be concise and efficient so that they can be held in 1-2 days.

The team is expected to have prepared the Sprint Summary before the meeting.

The timebox for the meeting is 1 hour.

The agenda for a sprint demo is as follows:

- The team presents the sprint summary
- The team demos the features
- The customer is asked to accept the result of the sprint, meaning that the team has done everything within it's power to deliver on the needs specified in the committed PBIs
- The team presents what they are ready to commit to for the next sprint, based on the priority set out in the backlog by the product owner

## Ritual: The Stand Up

Every day, the team needs to have a status update. This is to get everyone up to date on how the current sprint is progressing. The team captain is the moderator of the meeting.

The meeting is tactical in it's nature. The timebox for the meeting is **15 minutes**. This can not be extended and it's the moderators job to make sure it's not.

The agenda for a stand up is as follows:

- Everyone reports on what they did yesterday, what they plan to do today and whether they think they will need any support from someone else with any specific PBI. There should be **no** discussion around what or how the work will get done. The stand up is not a design meeting. If a person states that they need help, that is noted down by the moderator.
- The moderator looks at the burn down chart to gauge whether there might be a concern for the sprint. If anyone stated that they need help or the burndown chart is starting to diverge, the team must quickly determine what the problem is and make a decision about which members of the team will scramble to solve the problem. Note that the stand up is **not** a place to be discussing what needs to be done, but rather assign who will handle the problem.

### Stand Up Meeting Minutes

Should be written by the moderator. Should be short and simple and only contain exceptional information. Should not contain what people have done or what they plan to do. This information should be available within the project management tool by task assignment etc. But any issue that has been raised must be noted down and the assigned members that is tasked with solving the problem. This information is critical when it comes to compiling the Sprint Summary at the end of the sprint.

## Bugs

We will never estimate bugs. Bugs are mistakes generated by us and we take full responsibility for our mistakes. Therefor Bugs should slow us down. They should lower the velocity. We must work harder to keep our pace if we introduce bugs.

For this to work, we need to have a clear definition of what a bug is.

### A bug is something that is:

- Obviously broken or
- Prevents the user from accomplishing the task that the system is designed to perform or
- Prevents the system to fulfill the need that the system was designed to fulfill

### A bug is not (unless it's also anything of the above):

A behavior that is unexpected from the user's perspective. Because expectations are subjective and there are billions of people with different expectations. This is merely a matter of quality. A high quality system meets the expectations of most of it's users.