[Handbook](../../README.md) / Development / Guidelines

# Acceptance Criteria Format

Acceptance criterias are noted down as scenarios using the [Cucumber/Gherkin syntax](https://docs.cucumber.io/gherkin/reference/). In order to make scenarios easy to overview and read, we have extended the syntax slightly and we apply a consistent styling of how they are written.

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
        Scenario **Cancel allowed**:
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

## Explanations

Sometimes it can be hard to understand the underlying reason for a scenario. In those cases you may add an explanation or background for the scenario.

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
            <li>When I open the order in Zendesk</li>
            <li>Then I should be able to Cancel the order</li>
        </ul>
    </td>
</tr>
</table>

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