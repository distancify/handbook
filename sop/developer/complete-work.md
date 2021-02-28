[Handbook](../../README.md) / Standard Operating Proceedures / Developer

# Complete Work

Once you have:

- [gotten all acceptance tests/scenarios reviewed and approved](test-and-submit-results.md)
- gotten the code Pull Request(s) reviewed and approved
- recorded a demo

It's now time to wrap up and hand the work over to the Release Manager and stakeholders.

1. Navigate to the **Releases** in Azure DevOps and find the appropriate **Release work item**.

    **IF** there is no release, create a new one. It should be named after the current sprint, for example "J47".

    **IF** you're pushing for a hotfix, create a release called &lt;sprint&gt;-hotfix# where the **#** is the next available number based on previous hotfixes of the same sprint release. For example J47-hotfix1

    Make sure that new releases are put in the correct **Area** (/Releases/&lt;customer or project name&gt;) and assign it whoever is managing this release (could be yourself, refer to [Assigning Release Manager to a Release](../release-manager/assigning-release-manager-to-a-release.md) for more details).

2. Add your feature/fix to the **RC Next** section in **Description** field, creating it if it's not there. Each RC generally has a **Features** and **Fixes** section, as this simplifies for the reader.
    
    Each item should start by pointing to it's related work item (using a #1234 style link, as DevOps automatically makes these into proper work item links). By referencing the link in text, a hard link between the items is created, so it's possible to see from the work item which release it's part of (and whether it's deployed to production).

Below is an example of a **Description** field:

```
## RC 1

### Features

- #5501
- #5530
- #4050
- Optimized CSS bundle. Notice that there can be changes not tied to a work item like this one
- #4525
  It's also possible to further explain what the change from a work item does if necessary, like this

### Fixes

- #5601
- #3054

## RC Next

### Features

- #5506
```