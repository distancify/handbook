[Handbook](../../README.md) / Standard Operating Proceedures / Support

# Responding to a Support Request

A support request can come in many forms, and have many purposes. The most important task when dealing with a new support request, is to determine what kind support request it is. This identification follows a very simple pattern that can be summarize as follows:

1. Assume it's a question
2. If it's not a question, it might be a bug
3. If it's not a bug, it's a feature request

Depending on the nature of the support request, we have different proceedures, detailed below.

## A Note About Statistics

In order to keep track of the kind of support requests we get, the 1st-line support team is expected to group different type of questions into groups (using Tags in Freshdesk). This allows us to extract statistics that will guide long-term investments implementing solutions to minimize the need for support.

> **Principle: Support is a necessary evil**
> 
> We believe that support will always be needed, but it is not a goal in itself. Support begins where the system fails. An intuitive, high quality, self-healing system should require minimal support. On the other hand, in order to achieve high-quality, it's paramount that the Developers and Product Owners get feedback from the Support channel on how to improve the system over time.

## Questions

A question can come in many forms. Sometimes it might not even be phrased as a question, but it's a question none the less.

Below are some common patterns and how to handle them.

### How do I do *X*

A very straight forward question. First, ensure that what the customer is asking for is possible to do. If so, try to find a [Solution](./writing-a-solution.md). If there are none, write it. Then reply to the customer with a link to it.

If you find yourself unable to figure out how to help the customer. You may assign the ticket to 2nd line Developers group, and ask for advice.

### Where do I find *X*

This kind of question is handled exactly like **How do I do *X***.

### Can you do *X* for me?

This question is a request to have something made for the customer. We will always try to help the customer, even if they are capable to do it themselves. Sometimes they might simply not have time or feel comfortable enough to do it themselves.

There are also cases where the user strictly can not perform the action themselves, but it still falls within our Support team's capabilities. This could be things like database operations, configuration changes or front-end styling tweaks.

Sometimes, you will find youself not knowing how to perform the task asked for. Then you may assign the ticket to 2nd line Developers group, and ask for advice.

In a few cases, what's asked for by the customer simply can't be done. In this case, the ticket is to be regarded as a feature request.

> **Principle: Empower the user**
> 
> Even if we help the customer to perform the action, we shoud always strive to inform the customer how to do it themselves the next time (if possible). Ensure there's a solution that outlines the proceedure, and inform the customer that if they want to, they may chose to follow it the next time.

> **Principle: Look for a work around**
> 
> Even if what the customer asks for exactly might end up as a feature request, we should always lookd for, and suggest, a work around which might still help the customer for the time being.

### Is it possible to do *X*?

This question is similar to **How do I do *X*** but more often ends up being a feature request, depending on the customer's own familiarization with the system. This kind of question is a bit ambiguous.

If you find that what the customer asks for is possible, we should inform the customer how they can do it themselves (if they can), and ask whether they'd like us to do it for them.

If the thing the customer asks for is not possible, we should look for a potential workaround, and identify the ticket as a feature request, passing it on to Product Owners.

## Bugs

If a support request points to a behavior of the system that clearly contradicts current acceptance criterias, it's to be regarded as a bug. There are also bugs of "implcit criterias". These can be things like a system breaking laws (which where applicable at the time of implementation), unexpected behavior or throwing error messages. However, these kind of implicit bugs can be more tricky to determine, and should first and foremost be forwarded to the Product Owners.

For obvious bugs, refer to [Submitting a bug report](./submitting-a-bug-report.md) article.

## Feature Requests

Feature requests are not covered by any SLA, and are to be passed on to the Product Owner group for further discussion. The Product Owners will try to identify the underlying cause of the support request, what we refer to as the User Story. Sometimes, after identifying the root problem of a request, it might be determined that a goal can be achieved with existing functionality. In this case, the support request will be identified as a Question and be passed back to Support group with a description of how to solve the problem.

> **Principle: A feature change is a last resort to a problem**
> 
> We should always try to solve customer's problems with existing functionality, only building features where it's absolutely necessary. Every feature adds complexity and has a maintenance cost. It also adds constraints to future development. By keeping solutions lean we ensure we can keep a high productivity long term.
