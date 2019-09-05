# Testing

This section describes the different testing activities carried out during a sprint.

## Test planning

At the start of a sprint we should have a number of PBI's with a list of acceptance criteria for each PBI. While we write our acceptance criteria in Gherkin format, they are not necessarily complete test cases. During test planning we create test tasks for each criteria by adding test data, e.g. which specific user, category, and/or product should be used. This way we identify the potential need for seeding new data into the test system. We should also add negative tests that are often left out of our acceptance criteria, but equally important. 

During test planning we should also consider which acceptance criterias that are best covered by unit tests and which should be verified though functional acceptance tests. If we need to export data on a specific format, e.g. using max 30 characters, we could verify the export method with a unit test and catch errors early instead of later in the development cycle, as the cost for fixing bugs are higher the later they are detected. On the other hand, things as verifying the user interface and log messages are typically functional tests.

In some cases we may have PBI's that are dependent on other PBI's and cannot be fully tested by themselves, or that can only be tested in the production environment. In those cases there should be a feature toggle that makes it possible to turn the functionality on and off, and also a separate test PBI for running the tests once the environment is in place.

The test planning is typically done together by the person that will test the PBI and the developer that will implement it.

The test tasks created during test planning should be put in status blocked, until the functionality is implemented and deployed to the test environment.

## Development and unit testing

The developer implementing the PBI is also responsible for writing unit tests. The unit tests should be written as part of designing the solution, and before implementing the actual functionality. If it is difficult to write the unit tests, that may be an indication that the design can be improved. Also, by writing the unit tests before implementing the code, it is less likely that a fault will be introduced during implementation.

When enough functionality has been implemented to run a functional test, that test task should be unblocked, rather than waiting until the whole solution is ready and unblock all tests.

## Functional testing

When a test is unblocked, the developer should have a short handover to the tester where the functionality is demonstrated, i.e. showing how the feature work and not how it is implemented.

The tester is responsible for executing the functional tests and documenting each step using screen dumps and/or detailed descriptions. 

The tests can be done either manually or be automated using Specflow and Selenium. We should automate the tests whenever possible, as the automated tests provide a living documentation of the functionality. While creating automated tests is initially more time consuming, the time for writing automated tests is gradually reduced as many steps, or part of steps, can be reused between different scenarios. We should particularly use test automation in the following cases:

- The test is deemed to be valuable as a regression test
- We need to execute the scenarios several times with different test data
- We need to run the test on multiple browser

Even when using test automation there are often steps that are better suited for manual testing, such as verifying the look and feel of the user interface. 

## Exploratory testing

The tester is also expected to do some exploratory testing to see how the feature behaves outside its normal use. This is normally not documented unless some unexpected behavior occurs. When something unexpected happens it should be documented and more time should be put into exploratory testing of that specific feature since bugs often cluster.

## User acceptance test

When testing is done there should be a handover to the customer where the feature is demoed and the test results are shown. The demo should clearly show that the acceptance criteria have been fulfilled and can be agreed on by the customer. 

The customer can also run their own UAT where they test the feature in the QA-system. Having the customer testing a feature is important for validating that the functionality works as they expected, since the customer often has implicit requirements that may not have been captured during specification. It should be noted that the UAT is not part of the sprint work, and any issue that is not related to the original acceptance criteria should be communicated to the product owner before any action is taken.  

## Testing external integrations

We don't test integrations with third party services as part of the sprint. If a PBI has an external dependency we mock this during the functional tests. External integration tests are instead performed as separate tasks. 


