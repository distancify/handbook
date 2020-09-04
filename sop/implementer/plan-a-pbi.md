[Handbook](../../README.md) / Standard Operating Proceedures / Coder

# Plan a PBI

Once you have been assigned a PBI, it's time to make a plan for implmenting it. We have a acceptance-test-driven approach, and track most progress around whether an acceptance test is passing or not.

## 1. Add scenarios to board

The [Product Developer]() should have added all the new acceptance tests to the *spec repo* already. In order to find the related scenarios, open up **SpecFlow+ LivingDoc** and go to the related repository.

> You can find out which spec repos are affected by looking at the related Pull Requests on the PBI.

Once in LivingDoc, simply search for `@item:1234` (where `1234` is the PBI number). This will filter all the scenarios and only show the ones affected by the PBI.

Now, for each scenario, simply add a work item of type **Test** as a child of the PBI, this can be done easily from the **Sprint board**.

The **Test** work item should contain a link to the scenario that it covers. The link can be copied from **SpecFlow+ LivingDoc** by clicking the ![paper clip](clip.png) icon.

## 2. Estimate scenarios

Before you're done, add an hourly estimate to each scenario, roughly estimating the time it will take to finish each scenario.