---
description: >-
  Since a Lair's development environment has a single file system
  representation, supporting multiple developers working in the same repo
  simultaneously requires provisioning multiple Lairs.
---

# As a Team

### Allocating Lairs for a Development Project

When working with an external VCS, we recommend **one Lair designated to only the "main" branch, and one additional Lair per developer**. The "main" Lair is used to serve your "customers" and should be deployed with the latest in the "main" branch. Other lairs should be used for development only. Deploying to these lairs would be analogous to deploying to a test environment.

{% hint style="info" %}
To keep lairs orgnaized, use naming conventions for such as`{repo_name}-{dev_name}`, and/or add tags to your lairs.
{% endhint %}

<figure><img src="../../.gitbook/assets/lairs_table (1).png" alt=""><figcaption></figcaption></figure>

### Development

For a developer developing in a feature branch locally, life should feel the same as it always did. As a developer you will makes and commit's changes as you normally do. then whenever you need the power of WayScript to help test your code, simply spin up the [Desktop App](../desktop-app/) and open your development lair (or keep it open) to sync your local changes to the hosted Lair environment.

### Deployment

When a feature branch is ready to be merged to the main branch, use your normal workflow to make it so. Normally this involves opening a pull request, seeking reviews, running tests, etc. Once the main branch is updated, and you're ready to use WayScript to ship your new code to your customers, you will:

1. Ensure your local directory reflects the latest code in the main branch
2. Open your production Lair used for this repo
3. Connect your lair to the local directory containing your latest code
4. Wait for updates to finish syncing to your Lair development environment
5. Inspect your Lair development environment and ensure changes are correct.
6. [Deploy](as-a-team.md#deployment) your lair to production.
