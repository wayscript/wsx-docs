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
  * Utilize WayScript SDK
  * Install packages compatible with pip 20+ (see [Hosted environments](deployments.md) on how to install packages)
  * Basic support for Flask 1.1+ web applications
* Node.js 14+
  * Utilize WayScript SDK
  * Install packages compatible with npm
  * Basic support for build toolsets such as webpack, yarn, and gulp (React)
* Golang 1.18+ (partial support)

### Managing your Lairs

#### **Creating a Lair**

Navigate to your “Lairs” view and select “+ New Lair” to create a new Lair. Lairs are initialized as a directory within your workspace root directory, containing a `.wayscript` folder for platform metadata and `.triggers` file.

{% hint style="info" %}
You can also create a Lair from a template, or a GitHub URL. If you are creating a Lair from a private GitHub repo, be sure to [setup your Version Control SSH credentials](../account/version-control.md#setup) first.
{% endhint %}

#### **Duplicating a Lair**

Lairs can be duplicated from your “Lairs” view through the right-click menu. The files will be duplicated from a Lair’s development environment, not its production environment. See [File system](file-system/) and [Hosted environments](deployments.md) for more details.

#### **Deleting a Lair**

Lairs can be deleted from your “Lairs” view through the right-click menu. Lairs are deleted for all members of the workspace and cannot be recovered, so please exercise caution.



{% hint style="info" %}

{% endhint %}
