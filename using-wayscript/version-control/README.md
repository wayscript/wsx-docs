---
description: >-
  WayScript is designed to allow you to continue managing your code as you see
  fit with your own version control system (VCS).
---

# Version Control

### Lairs vs Repositories

A code repository typically has a durable 'main' branch, and other, temporary, feature branches. Once the code is production-ready, it is only the 'main' branch that is typically 'pushed' to production. Code is only merged into this 'main' branch with confidence that it is production-ready.

A WayScript lair has two hosted environments: **development** and **production**, with a [deployment](../../platform/lairs/deployments.md) mechanism for 'pushing' the development environment into production. Just as a repository branch is a representation of a file system comprising your code, each Lair environment has a single file system.&#x20;

### Working with Lairs and Repositories together

Different workflows and VCS's exist, but typically developers want to edit their code locally using their favorite IDE, then commit changes to their VCS. Once you understand how to [connect a WayScript Lair to a local directory](../desktop-app/working-with-a-local-directory.md) using the [Desktop App](../desktop-app/), it suffices to know how to clone your repository to your local machine.&#x20;

To illustrate examples, we will use the popular tools: Github and its associated application GitHub Desktop.

1. [Clone repository](https://docs.github.com/en/desktop/contributing-and-collaborating-using-github-desktop/adding-and-cloning-repositories/cloning-a-repository-from-github-to-github-desktop) to local directory.
2. Create WayScript Lair
3. Use WayScript Desktop to connect the Lair to the same local directory

### Ignoring Files

Similar to the `.gitignore` file used to specify which files should not be pushed to version control, when a WayScript Lair is synced to a local directory, a`.wsignore` file is automatically created to specify which files should not be synced between the local directory and the hosted Lair environment. This file is seeded with some defaults, including ignoring the `.git` folder. You are free to add or remove any values from this file.

### Managing git branches

WayScript, as it stands currently, doesn't know anything about git or the repo that you are developing in. As described in the docs on [Working with a Local Directory](../desktop-app/working-with-a-local-directory.md), the syncing mechanism is looking only at this local directory, and ignoring any files in the `.wsignore` file. Since the `.git` folder is ignored by default, WayScript doesn't know about the branch you are working in, or any other git metadata. Switching branches locally is perceived by WayScript as simply updating the local file system, and those changes will be synced to the hosted Lair environment.
