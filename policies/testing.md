[Handbook](../README.md) / Policies

# Testing

All units that contain logic should be testable in isolation and have automatic tests that runs without external dependencies, aka Unit Tests.

All specified behavior should be specified as executable tests (such as gherkin or similar) and preferably be implemented in code so that the tests can be re-run automatically.

All projects must have the necessary infrastructure to run deterministic end-to-end tests, manually or automatic with minimal effort on behalf of the tester/test runner. This means that running tests should not require any manual set up of systems or data.

The [Code Owner](code-owners.md) is responsible for making sure the project fulfills this policy.
