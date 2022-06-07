# Exploratory Testing

When a new version has been deployed to staging, you should get notified by the Release Manager. Exploratory testing is done to catch undefined behavior and regressions in and around affected features.

Start by reviewing the included features in the Release board item

For each feature:

1. Go through the included scenarios, but look for ways to break the system by inputting unexpected values. There should be no need to test the acceptance tests per se, as they are already tested
2. Look for *implicit requirements*. Some things to look for:
   - Inconsistent behavior or styling in different browsers/different screen sizes
   - Missing or incorrect error messages
   - Forms that are not properly marked up
   - Missing meta data such as microdata or other types of technical SEO tagging
   - Crashes due to missing input, or overly long/complex input

If you find a bug, add a bug report to the *Release board item* itself. Follow the [Submitting a bug report](submitting-a-bug-report.md) guidelines, but do not add it to the backlog - add it as a child of the release.