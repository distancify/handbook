[Handbook](../../README.md) / Standard Operating Proceedures / Support

# Submitting a Bug Report

Bugs are to be submitted to the project's or clients main backlog in Azure DevOps.

## Bug Description

Since by [definition](../../definitions/bug.md), a bug is always tied to previous work, we can always assume that there is always a previus feature that introduced the bug. Therefor, bugs always need to reference the spec (or in the absence of spec, PBI or other work related item/instruction from client) that it originated from.

Apart from a reference to a previous spec, a bug must include:

- The steps needed to reproduce/demonstrate the issue, either as a numbered list or a video. Screenshots are also welcome. Clarity is more important than format
- An explanation why this is a bug and what the expected behaviour should be
- *Severity* should be set according to how many users are affected and in which way they are affected

Feel free to use the following template when creating a bug:

```
Perform the following steps:

1.

According to the scenario XYZ (https://link/to/spec) that stated [...]
At step #, the system should have [...]
```

Here's an example of a good bug report:

```
Perform the following steps:

1. Go to a product listings page
2. Resize the screen/viewport so that it's smaller than 768px

According to the visual spec (https://link/to/visual/spec/) that displays the filters on
phone devices.
At step 2 the filter view should be visible.
```

> Notice that in the example we reference a visual spec/mockup instead of a behavior spec. This can vary depending on the nature of the bug.