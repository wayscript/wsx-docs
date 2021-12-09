# Lairs

**Your tools live in Lairs, the basic building block of WayScript.**\
Lairs are preconfigured, containerized, and flexible development environments for your code. Lairs are ready to deploy, and come with production capabilities such as auto-logging, multiple environments, and more. Once deployed, WayScript will auto-orchestrate and execute your tool based on your configurations.

{% hint style="warning" %}
While Lairs live within your workspace, Lairs are isolated environments. Files cannot be referenced and processes cannot interact between Lairs.
{% endhint %}

### Supported protocols

Lairs are built on Linux-based Docker images with attached storage and available memory.

WayScript currently supports the execution of tools built with the following protocols. The WayScript team is working to adding support for additional protocols and flexible image and container size options.

* Python 3.9+
  * Packages compatible with pip 20+ (see [Hosted environments](../managing-tools/environments.md)) on how to install packages)
  * Support for Flask 1.1+ web applications
* **(Coming soon)** Node.js 14+
  * Packages compatible with npm
  * Support for Node’s http module

### Managing your Lairs

#### **Creating a Lair**

Navigate to your “Lairs” view and select “+ New Lair” to create a new Lair. Lairs are initialized as a directory within your workspace root directory, containing a `.wayscript` folder for platform metadata and `.triggers` file.

#### **Duplicating a Lair**

Lairs can be duplicated from your “Lairs” view through the right-click menu. The files will be duplicated from a Lair’s development environment, not its production environment. See [File system](file-system.md) and [Hosted environments](../managing-tools/environments.md) for more details.

#### **Deleting a Lair**

Lairs can be deleted from your “Lairs” view through the right-click menu. Lairs are deleted for all members of the workspace and cannot be recovered, so please exercise caution.
