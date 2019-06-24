We follow the agile testing approach and divide test activities in four quadrants. The main purpose of Q1 and Q2 is not to find bugs, but to support the development team so they avoid making them with the help of TDD/BDD, and should therefore always involve the developers. The main purpose of Q3 and Q4 is, on the other hand, to try to break the system and can therefore benefit from an external team (developers don’t like to break their own code). 

**Q2 Functional acceptance tests**

I’ve chosen to start in Q2, i.e. with writing functional acceptance test. 

Here we should adopt a BDD (Behavior-driven development) approach and extend our user stories with test cases written in Gherkin syntax. Gherkin is the language used in Cucumber/Specflow to write automated acceptance tests. The test automation is not the most important thing here, but what is important is that the test cases are specific enough to be automated. User stories are often vague, usually because the person who wrote them didn’t have a clear understanding of how the features were going to be used. Gherkin on the other hand forces the person to write concrete examples on how each feature will behave in different scenarios, which forces the person to actually understand how the features are going to be used. Since Gherkin is business-readable, the test can be developed in collaboration with the stakeholders and therefore provide a precise acceptance criteria, and at the same time provide a good documentation of how the features are supposed to work.

The structure of a functional acceptance test, written in Gherkin, is shown below:

    Feature: Feature 1
        Description / User Story

        Scenario: Scenario 1
            Given preconditions
            When actions
            Then results

        Scenario: Scenario 2

A Feature is a standalone functionality of the project. 
The feature description is often written as a User Story on the format: As a (role) I want (something) so that (benefit), but can be written in any format as it is intended for a human reader, and is not executed by Cucumber/Specflow. 

The actual test cases are then written in the Scenarios. Each scenario gives an example on how the Feature should behave, using a sequence of steps on the format Given (preconditions), When (actions), Then (results). The test scenarios should provide examples with specific test data.

The tests cases can be automated using Specflow. These tests are completely black box and should be placed in a separate solution and not together with the code under test. They are typically executed as part of the continuous delivery pipeline, e.g. when new code has been merged to main and after all unit tests have passed.

**Q1 Unit tests**

Using BDD for our acceptance tests helps the developers creating the right functionality. Using TDD (test driven development), i.e. writing the unit tests before implementing the actual methods, forces the developer to write testable code. Focusing on testability helps the developer to create a good design that makes the code more robust and easier to maintain. 

Testability is determined by factors such as (https://en.wikipedia.org/wiki/Software_testability):

* Controllability: The degree to which it is possible to control the state of the component under test (CUT) as required for testing.
* Observability: The degree to which it is possible to observe (intermediate and final) test results.
* Isolateability: The degree to which the component under test (CUT) can be tested in isolation.
* Separation of concerns: The degree to which the component under test has a single, well defined responsibility.
* Understandability: The degree to which the component under test is documented or self-explaining.
* Automatability: The degree to which it is possible to automate testing of the component under test.
* Heterogeneity: The degree to which the use of diverse technologies requires to use diverse test methods and tools in parallel.

Using a design pattern like MVC together with Dependency Injection we can achieve high testability by separating the logic (i.e. the Controller for logic tied to a specific View or Service for shared business logic) from the data (Model) and user interface (View), and by making it possible to inject test data. The latter is important since we want to test each unit in isolation as opposed to the functional acceptance tests where we do end-to-end testing at system level.

A common question when it comes to unit testing is how to define our units. In C# a unit is typically defined as a single method. However, writing unit tests for all methods would be time consuming and futile. The unit tests should focus on testing business logic rather than testing the user interface or the database. 
The unit tests are put in the same solution as the code under test. For each project in the solution there should usually be a separate test projects that gathers the unit tests for that particular project. 

The unit tests should be short and execute fast so that all unit tests can be executed each time there is a new commit in the repository.

**Q3 – UAT and Exploratory testing**

There will always be requirements that are not explicitly specified, so just verifying that the functionality fulfills the acceptance criteria may not be enough. In a user acceptance test (UAT) the end user validates that it actually works as they expected.

In exploratory testing a dedicated tester tries to break the application and see how it behaves when used outside the specification. It is hard to write any general guidelines on how this should be done and when it should be considered as finished. Usually this is a time-boxed activity where the tester spends an extra 15-30 min testing the application based on previous experience with things that could go wrong. 

When introducing changes to the user experience of critical processes like user registration or the checkout it can be also be good to make a formal usability study. In a usability study a number of users that have not been involved in the development are asked to perform a specific task in both the old and the new version and their actions are monitored using video recording and/or eye tracking together with a questionnaire where they answer questions on how easy they thought it was to perform the task.

An alternative way to check that a change has the desired effect can be to use an A/B-test where both the old and new version are active simultaneously and users are randomly assigned to either version in order to measure which version provides the best result.

**Q4 – Performance and load testing**

Performance is very important in e-commerce applications. While we rarely specify performance requirements explicitly in the PBIs it is important to make sure that the overall performance does not decay over time. 

One way to make sure that the performance does not decay is to monitor page loads etc.

A more proactive way to measure performance is to use a load test. There are several tools for load testing such as JMeter and Locust, and also dedicated load testing services such as Load Impact. These tools make it possible to record or script test scenarios and then let hundreds or thousands of virtual users execute those scenarios.  The load tests record load time as a function of the number of simultaneous users and usually also provides a server agent that measures CPU, memory, and bandwidth usage.
 
Load tests can be executed as part of the continuous delivery, or be scheduled to run at the end of each sprint.
