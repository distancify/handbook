[Handbook](../README.md) / Policies

# Code Owners

Every repository must have a code owner. The code owner should be configured as a required code reviewer for PRs against the **master** branch in the repository.

The Code Owner provides conceptual integrity of the projects architecture, and is ultimately responsible for the quality of the project.

## How to configure Code Owner in Azure DevOps

1. Go to **Project Settings** -> **Repositories**
2. Expand the repository you want to configure
3. Expand the **Branches** node
4. Click the **master** branch
5. Go to tab **Policies**
6. Click **+ Add automatic reviewers**
7. Select the Code Owner
8. Set **Policy requirement** to **Required**
9. Click **Save**

## How to configure Code Owner in Github

1. Add a file called **CODEOWNERS** to the root of the repository with the following content: `* @<github username>`
2. Open the repository on **github.com**
3. Go to **Settings** -> **Branches**
4. Click **Add rule**
5. In **Branch name pattern**, type in `master`
6. Check **Require pull request reviews before merging**
7. Check **Require review from Code Owners**
