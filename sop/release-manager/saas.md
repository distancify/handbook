[Handbook](../../README.md) / Standard Operating Proceedures / Release Manager

# SaaS Releases

This document serves as a step-by-step guide on how to create and deploy a SaaS release.

Releases follows the sprints:

- At the beginning of a sprint:
  - Create Release Board Item
- After the sprint:
  - Create and Deploy Release Candidate (RC) to Staging
- After testing and approval by client:
  - Deploy to production

## Create Release Board Item

1. Go to the [Release Board](https://dev.azure.com/distancify/Dev/_boards/board/t/Releases)
2. Click "New Item"
3. Select "Release" in the drop-down
4. Enter the name of the release, for example "J55" for a SaaS project, or "1.2" for Shipped Software
5. Open the newly created Work item
6. Set Area to match the current project: "Dev/Releases/&lt;project&gt;"
7. Click "Save & Close"
8. Drag the Release into the "Development" column and the correct Swimlane

## Create and Deploy Release Candidate (RC) to Staging

Each project generally have one repository (with a few exceptions, refer to project-specific documentation). In this repository, there should be a `next` branch which is the target for PRs.

1. For each Approved Pull Request (PR) against `next`:
   1. Merge the PR
   2. If the PR is **not** connected to a PBI:
      1. Add a link to the PR in the Release work item description using the `!<number>` notation.
   2. If the PR is connected to a PBI:
      1. Add a link to the PBI in the Release work item description using the `#<number>` notation.
      2. Open up the PBI
      3. Verify that the PBI has a Customer summary (text or video link)
      4. Set the PBI to `Done`
      5. If the PBI has child Task work items, move them to the Release work item, as they are to be performed at deploy
3. Create a `tag` on the latest commit of the `next` branch, name the tag `v<sprint>.1`, for example `v66.1` for the first RC of sprint 66.
   This will autmatically build and deploy the RC to a staging environment.
4. Notify testers (internal and client) that there is a new RC available for test.

If the testers find bugs, they are to be added to the Release work item and fixed by developers. Once fixed, another RC should be deployed. Simply create a new tag named `v66.2`, increasing the second number for each new RC.

## Deploy to Production

After the client have approved the RC, decide on a time to deploy together with the client. Although deploys are generally seamless, it's always good to pick a time based on user activities, to avoid uneccessary interruptions in case there's a problem. 

Production deploys are done through Octopus Deploy. All deploys should be fully automated.

1. Find the RC in Octopus and click `Deploy to Production`.
2. Once deployed, perform any post-deployment tasks
   These tasks should be added to the Release work item (see [Create and Deploy Release Candidate (RC) to Staging](create-and-deploy-release-candidate-rc-to-staging) section). If possible, they should be performed by the Release Manager, but if not possible, a Developer may be called in during the deployment.
3. Merge the `next` branch to `master/main` branch (but don't delete it, leave it for future PRs)
4. Write a proper Release Notes document in the project's related customer accessible wiki

