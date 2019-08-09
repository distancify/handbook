[Handbook](../../README.md) / Development / Guidelines

# Acceptance Criteria Format

Acceptance criterias are noted down as scenarios. The syntax for scenarios is originates from the [Cucumber/Gherkin syntax](https://docs.cucumber.io/gherkin/reference/). In order to make scenarios easier to overview and read, we have changed and extended the syntax slightly and we apply a consistent styling of how they are written.

As scenarios are read by humans, readability is the number one priority. When deciding how to formulate your scenarios, always think of the person that is going to read them.

## Overall form

Below is the simplest example of a scenario. Notice the bolded scenario name and list. This is style elements supported by Azure DevOps and limits the visual load of a scenario.

<table>
<tr>
    <th>Example</th>
</tr>
<tr>
    <td>
        Scenario <b>Cancel allowed</b>:
        <ul>
            <li>When I open the order</li>
            <li>Then I should be able to Cancel the order</li>
        </ul>
    </td>
</tr>
</table>

## Pre-requisites

When the action and outcome is dependent on a given circumstance:

<table>
<tr>
    <th>Example</th>
</tr>
<tr>
    <td>
        Scenario <b>Cancel allowed</b>:
        <ul>
            <li>Given the order is in status Confirmed</li>
            <li>When I open the order in Zendesk</li>
            <li>Then I should be able to Cancel the order</li>
        </ul>
    </td>
</tr>
</table>

When a given action and outcome is shared between multiple circumstances, in which case multiple givens can be combined as follows:

<table>
<tr>
    <th>Example</th>
</tr>
<tr>
    <td>
        Scenario <b>Cancel allowed</b>:<br>
        <ul>
            <li>Given <b>ANY</b>:
                <ul>
                    <li>The order is in status Init</li>
                    <li>The order is in status Confirmed</li>
                    <li>The order is in state Attention and all connected Deliveries are in state "Init"</li>
                </ul>
            </li>
            <li>When I open the order in Zendesk</li>
            <li>Then I should be able to Cancel the order</li>
        </ul>
    </td>
</tr>
</table>

When a given action and outcome is dependent on multiple circumstances. Instead of making the Given statement too long and difficult to interpret, each pre-requisite can be added as separate rows as follows:

<table>
<tr>
    <th>Example</th>
</tr>
<tr>
    <td>
        Scenario <b>Cancel allowed</b>:<br>
        <ul>
            <li>
                Given <b>ALL</b>:
                <ul>
                    <li>The order is in status Confirmed</li>
                    <li>The order has not been previously cancelled
                    <li>When I open the order in Zendesk</li>
                </ul>
            </li>
            <li>When I open the order in Zendesk</li>
            <li>Then I should be able to Cancel the order</li>
        </ul>
    </td>
</tr>
</table>

The two previous examples can also be combined:

<table>
<tr>
    <th>Example</th>
</tr>
<tr>
    <td>
        Scenario <b>Cancel allowed</b>:<br>
        <ul>
            <li>
                Given <b>ALL</b>:
                <ul>
                    <li>Given <b>ANY</b>:
                        <ul>
                            <li>The order is in status Init</li>
                            <li>The order is in status Confirmed</li>
                            <li>The order is in state Attention and all connected Deliveries are in state "Init"</li>
                        </ul>
                    </li>
                    <li>The order has not been previously cancelled</li>
                </ul>
            </li>
            <li>When I open the order in Zendesk</li>
            <li>Then I should be able to Cancel the order</li>
        </ul>
    </td>
</tr>
</table>

Although these formats can sometimes help making multiple scenarios easier to overview, it can also have the reverse effect. Sometimes it's easier to break the Scenario into multiple smaller ones. Use your judgement when deciding how to write your scenarios.

## Scenario naming

The name of the scenario should be short and to the point. Any auxiliary verbs should be stripped if not necessary. Also try to make the names of the scenarios easily distinguishable. For example, do not have scenarios named "Cancel allowed Init", "Cancel allowed Confirmed", "Cancel allowed Attention". Instead, just name them "Init", "Confirmed", "Attention". Names don't have to make much sense but they must be easily recognizable.

## Comments

Sometimes it can be hard to understand the underlying reason for a scenario. In those cases you may add an explanation or background for the scenario.

A comment often explains the behavior in the context of the system. Perhaps the given scenario has some external dependency or pre-requisite that isn't directly covered by the PBI itself.

<table>
<tr>
    <th>Example of good comment</th>
</tr>
<tr>
    <td>
        Scenario <b>Processing</b>:<br>
        <i>Comment: As orders will always be moved back to "Confirmed" after any change has been made, and then immediately transfer to processing, we can use the processing state-change in order to achieve this.</i>
        <ul>
            <li>When an order is moved to processing</li>
            <li>Then the order should be sent to ERP</li>
        </ul>
    </td>
</tr>
</table>

### Hidden User Stories

Beware that needing a comment can often mean you need an additional user story instead.

Take the example below:

<table>
<tr>
    <th>Example of bad comment</th>
</tr>
<tr>
    <td>
        Scenario <b>Only discounted price</b>:<br>
        <i>Comment: If we only send discounted/final price to ERP, we get full freedom on how we want discounts applied in the e-commerce without having to worry about how ERP models the discount. For example order discounts can sometimes be tricky to handle in ERP.</i>
        <ul>
            <li>Given that the order has a discount</li>
            <li>When the order is exported to ERP</li>
            <li>Then only the discounted sums should be sent to ERP (not the original price)</li>
        </ul>
    </td>
</tr>
</table>

This scenario actually explains a hidden need, and can be made more explicit with a user story:

> ERP wants to have order discounts split upon all the affected rows as the ERP can't properly handle order discounts in the return flow

## Multiple steps

When an action is divided into multiple substeps, it can help for readability to split the actions up in a list. Note that the list should be numbered and the actions are assumed to play out in order:

<table>
<tr>
    <th>Example</th>
</tr>
<tr>
    <td>
        Scenario <b>Cancel allowed</b>:<br>
        Reason: Orders may only be cancelled in specific states due to business rules.
        <ul>
            <li>Given the order is in status Confirmed</li>
            <li>
                When:
                <ol style="list-style-type: decimal;">
                    <li>I open Zendesk</li>
                    <li>I click on the order overview</li>
                    <li>I click on an order in the order overview</li>
                </ol>
            </li>
            <li>Then I should be able to Cancel the order</li>
        </ul>
    </td>
</tr>
</table>

## Examples

It may be tempting to add an example to a scenario. Imagine a scenario as follows:

<table>
<tr>
    <th>Example</th>
</tr>
<tr>
    <td>
        Scenario <b>Addition</b>:
        <ul>
            <li>When
                <ol style="list-style-type: decimal;">
                    <li>Enter a number</li>
                    <li>Clicks the "plus" button</li>
                    <li>Enter another number</li>
                    <li>Clicks the "equal" button</li>
                </ol>
            </li>
            <li>Then I should see the sum of the two numbers</li>
        </ul>
    </td>
</tr>
</table>

One could be tempted to give a concrete example, such as "enter number 2, then number 3 and the answer should be 5".

However, **this misses the fact that scenarios should be concrete in the first place!**

Being concrete in your scenario description is a good thing. The person reading the scenario should be capable of generalising the underlying behaviour. If not, multiple scenarios given different inputs can be made. So instead, the above scenario could be written like:

<table>
<tr>
    <th>Example</th>
</tr>
<tr>
    <td>
        Scenario <b>Addition</b>:
        <ul>
            <li>When
                <ol style="list-style-type: decimal;">
                    <li>Enter number 2</li>
                    <li>Clicks the "plus" button</li>
                    <li>Enter number 3</li>
                    <li>Clicks the "equal" button</li>
                </ol>
            </li>
            <li>Then I should see the number 5</li>
        </ul>
    </td>
</tr>
</table>

Writing the scenario like this have the following benefits:

- The person writing the scenario don't have to think of the underlying implementation and does not has to reduce the problem down to a general solution. This is what the implementation phase is for.
- The person reading the scenario doesn't have to "compile" the scenario in his/her head in order to understand whether it does the right thing
- The scenario can be 1:1 copied into an actual test.

If you think of your scenarios as test as you would write a unit test before implementing the code, you realize that you don't need to know the implementation when writing the test. It's actually better to come up with the implementation after you have the test.

## Reverse scenarios

Scenarios should only describe new behavior tied to the user story. It might be tempting to add reverse scenarios, such as:

<table>
<tr>
    <th colspan="2">Examples</th>
</tr>
<tr>
    <td>
        Scenario <b>Cancel allowed</b>:
        <ul>
            <li>Given the order is in status Confirmed</li>
            <li>When I open the order in Zendesk</li>
            <li>Then I should be able to Cancel the order</li>
        </ul>
    </td>
    <td>
        Scenario <b>Cancel not allowed</b>:
        <ul>
            <li>Given the order is <b>not</b> in status Confirmed</li>
            <li>When I open the order in Zendesk</li>
            <li>Then I should <b>not</b> be able to Cancel the order</li>
        </ul>
    </td>
</tr>
</table>

This is generally not needed and only serves to confuse whoever is trying to understand the criterias.

It might however be a reasonable test scenario. But the test scenarios needed to validate a feature generally always extend upon the acceptance criterias.

## Legacy scenarios

When changing the behavior of an existing system, one may want to specify a scenario that describes how the system already works. But old scenarios are generally unaffected by new development unless they specifically conflict with new scenarios.

For example, a scenario in a previous PBI may have been:

<table>
<tr>
    <th>Example</th>
</tr>
<tr>
    <td>
        Scenario <b>Login disallowed</b>:
        <ul>
            <li>When I login with non-existing credentials</li>
            <li>Then I should see a message saying the credentials are incorrect</li>
        </ul>
    </td>
</tr>
</table>

Let's imagine we then have a new PBI which says that when I log in with incorrect credentials, I want to have the option to reset my password in case I have forgotten it.

In this new PBI, it could be tempting to add a scenario that also says that there should be a message saying the credentials was incorrect. **Do not do this**. The old scenario still applies as long as none of the new scenarios directly contradicts it. Adding scenarios explaining existing functionality only serves to confuse the person reading the scenarios. Should the implementation impact old scenarios in an unexpected way, there should be tests covering the old scenarios saying so, or at least it will be regarded as a bug and will be fixed.

Instead, likely the only scenario needed for the new PBI would be:

<table>
<tr>
    <th>Example</th>
</tr>
<tr>
    <td>
        Scenario <b>Suggest password reset</b>:
        <ul>
            <li>When I login with non-existing credentials</li>
            <li>Then I should see a link to the reset password form</li>
        </ul>
    </td>
</tr>
</table>

And this new scenario **does not mean that the old message should be removed**.