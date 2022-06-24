# File system

Each Lair comes with an attached file system that is fully encapsulated, i.e., cannot be accessed by files or processes within other Lairs. Each Lair is represented as a directory within the workspace, but modifying its contents is most similar to rebuilding a Docker image.&#x20;

### Example file system for your workspace

```
my-workspace/
├── my-lair-a/
    ├── .triggers
    ├── README.md
    └── my-file.py
└── my-lair-b/
    ├── src/
    |   └── my-app.py
    ├── .triggers
    └── .secrets
```

Files can be referenced by their relative path (the current directory is your Lair directory), and certain directories and files are protected, including:

* Lair directory
* `.triggers` file
* `.secrets` file
* `.wayscript` directories and nested files

{% hint style="warning" %}
You may not access files within other Lair directories from a selected Lair. Any files that need to be accessed by multiple Lairs should be served through an independent service.
{% endhint %}

### Completing file operations

**Create a new file or directory**

Create a file or directory within your Lair's file system by pressing ＋ next to the search bar.&#x20;

![](../.gitbook/assets/image.png)

You can also upload a file or directory from your local device's file system by dragging it into your Lair's file system.&#x20;

{% hint style="danger" %}
Uploading large files or folders may take a few moments to complete. Do not navigate away from your current Lair until your upload is complete.&#x20;
{% endhint %}

**Editing files**

Select a file to open and modify its contents within WayScript's in-built editor.&#x20;

{% hint style="warning" %}
File edits do not auto-save; you must use `cmd+s` or `ctrl-s` to save edits to your Lair's files. You will see a :red\_circle: (red dot) next to your file name if it has not been saved.
{% endhint %}

### Using file sync through the WayScript desktop app

When using the WayScript desktop app, your file system exists in two places:

* **Remote** - on cloud infrastructure (self-hosted or WayScript managed)
* **Local** - on your local device

The WayScript desktop app creates and accesses files on your local device and then syncs those files to your remote infrastructure.

{% hint style="info" %}
Both your remote and local file systems are connected to your Lair’s development environment. Please see [Hosted environments](deployments.md) for more details on your Lair’s environments.
{% endhint %}

**Setting up your file sync between remote and local**

On first launch of the WayScript desktop app, follow the prompts to choose a local `home` directory to sync WayScript files between remote and your local device. Our tool will then create a new directory with the names of your workspaces within the specified directory and download files present on remote.

![](https://codahosted.io/docs/2kDMDaZ6QP/blobs/bl-ctT1lSpsA8/897d5cb37c8557ad9b149526e93a87b16af4e7f0f0be3aa51e4bd08c6d58007c44949fb53d3f804d60ab6953bb3c4909efbdda87870c6cf9e4af93f351cc2f42f482aa8e814a011346a8e71807b8ad97ce8824146ad13a8b7a1b3d966da21b512ef7ef54)

{% hint style="success" %}
Now that your WayScript files are present on your local machine, you can initialize `git` or other VCS on the workspace directory or for individual Lair directories to track changes or push to other remote locations. You can also clone repos directly into your workspace or Lair directories.
{% endhint %}

#### **Opening & saving files on local**

The WayScript file system accesses your local files through the in-app file browser. You can open multiple files in a tab view and edit file content using the app's in-built text editor.&#x20;

#### **Fetching file system status from remote**

Pressing “Fetch” will evaluate whether there are changes that have not be downloaded from remote to your local machine. The app will also automatically “Fetch” before protected actions such as starting a new process or updating your integrations.

#### **Pulling file system from remote**

Pressing “Pull” will attempt to download files from remote to your local machine, based on the following rules:

* If the file has been modified or created in remote and NOT modified on your local machine, the remote file will replace your local file.
* If the file has been modified on your local machine, you will be asked if you would like to overwrite the local file with the remote file.

{% hint style="info" %}
Currently, this function is not destructive, i.e., workspaces, Lairs, and files deleted within your remote workspace will NOT be deleted on your local workspace. You must delete these directories from your local file system to avoid their re-creation.&#x20;
{% endhint %}

#### **Pushing file system to remote**

Pressing “Push” will attempt to upload your local machine’s workspace to replace your remote workspace.&#x20;

### Considerations

Your `home` directory on your local machine is initialized with a strict directory structure and helper files to ensure data integrity in the WayScript file system. Please exercise caution when completing the following local file operations:

* Adding package directories with an extremely high number of files (such as `node_modules`) to your Lair directory may result in an error while syncing. We recommend building your tool outside the Lair filesystem and then copying your project folder into your Lair directory.&#x20;
* Placing files outside of Lair directories (e.g., `myworkspace > myfile.py`) may result in an invalid workspace state and require you to reconfigure your `home` directory.
* Modifying the `.wayscript` directories and nested files stored under your workspace root directory and Lair directories may result in an unresponsive app state. These files are used for configuration or identification purposes.&#x20;
