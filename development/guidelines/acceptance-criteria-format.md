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

**Note** that there should always only be a single *When* and *Then* statement for each scenario.

## Scenario naming

The name of the scenario should be short and to the point. Any auxiliary verbs should be stripped if not necessary. Also try to make the names of the scenarios easily distinguishable. For example, do not have scenarios named "Cancel allowed Init", "Cancel allowed Confirmed", "Cancel allowed Attention". Instead, just name them "Init", "Confirmed", "Attention". Names don't have to make much sense but they must be easily recognizable.