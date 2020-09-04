[Handbook](../../README.md) / Standard Operating Proceedures / Coder

# Submitting Test Results for Review

When a feature has been implemented, acceptance tests are to be run by the developer. The results of the tests should be submitted for review to the Product Developer. The purpose of this review is to make sure that the tester (developer) has interpreted the intention of the acceptance criteria correctly.

## Submission Requirements

A test can either be performed automatically (scripted) or manually. Below is a guide to give you an idea of what needs to be provided for a review to be possible.

### Manual Tests

A manual test is conducted by going through each scenario, documenting each step with screenshots or other hard evidence that the system was set up correctly and behavior was as expected.

This is most easily done by breaking down a Gherkin scenario line-by-line and provide evidence for each one.

Here's an example:

```
Given there's a channel with countries "Belgium" and "France"

[Screenshot of channel settings view with two countries, Belgium and France]

And I'm geographically located in France

[Screenshot of something indicating that the browser will be treated as located in France, for example by using a proxy]

When I go to the 

[Screenshot of browser browsing the channel]

Then the country should be set to "France"

[Screenshot of the country selecting displaying country "France"]
```

### Automatic Tests

Automatic testing are done using various automation tool. At the time of this writing, cypress is out primary tool for web-based automating testing. Cypress has the ability to record a video performing the test. This video can substitute the above documentation mentioned in "Manual Tests" above.

If the tool does not have video capabiltiies, the documentation mentioned in "Manual Tests" is expected to be followed.