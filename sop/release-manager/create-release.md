[Handbook](../../README.md) / Standard Operating Proceedures / Release Manager

# Create Release Board Item

Releases are tracked on the "Release" board in Azure DevOps.

## When to Create

The naming and timing of releases differs between *SaaS* and *Shipped Software* projects.

### SaaS Project

At the beginning of a new sprint (with planned work), we create a *work item* to track all changes going into the release.

The naming of a SaaS release should match the name of the sprint, for example "J55" for Jedi sprint 55.

### Shipped Software

For shipped software, we create a new Release item when there is a new feature or bugfix about to the merged into an upcoming release.

The naming of Shipped Software releases follow [SemVer](https://semver.org/). Consult a related Developer for understanding the nature of the release.

## Create work item

1. Go to the [Release Board](https://dev.azure.com/distancify/Dev/_boards/board/t/Releases)
2. Click "New Item"
3. Select "Release" in the drop-down
4. Enter the name of the release, for example "J55" for a SaaS project, or "1.2" for Shipped Software
5. Open the newly created Work item
6. Set Area to match the current project: "Dev/Releases/&lt;project&gt;"
7. Click "Save & Close"
8. Drag the Release into the "Development" column and the correct Swimlane

## Identify and link branches

> This is only really related to **SaaS projects**, as shipped software are generally released from the master/main branch at the time of locking a release. A Shipped Software Release item generally don't have a specific branch until it's released, in which case major and minor versions gets their own branches to maintain parallell bugfixing.
>
> Refer to [Lock Release](lock-release.md) for Shipped software branch links.

Once the Release item is created an in the correct place:

1. Open it up again
2. In the "Development" section on the right hand of the item form, click "Add link"
3. In "Link type", select **Branch**
4. Select a related "Repository"
5. Select the related branch
