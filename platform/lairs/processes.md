# Processes

Your Lair is built to execute processes from its files, triggers, or events. When a process is started, WayScript isolates its execution in an optimized container.

### Executing a process

A process can be executed in the following ways:

* Manual invocation of a trigger - see [Triggers](triggers.md) for more details
* Event-based invocation of a trigger - see [Triggers](triggers.md) for more details
* Run command entered into the terminal - see [Terminal](terminal.md) for more details

{% hint style="info" %}
Your processes are executed against your Lair’s remote file system, not the files on your local machine. If your process execution does not reflect file changes made locally, you must first “Push” your file system. See [file-system](file-system/ "mention") for more details on file sync.
{% endhint %}

### Viewing running processes

A list of your Lair’s running processes is located on the bottom of your Lair editor. Each row is an independent process. You can see when the process was started and ended, what run command was used to execute the process, how the process was invoked (from which trigger), and the current process status.

![](https://codahosted.io/docs/2kDMDaZ6QP/blobs/bl-1PS\_-4J1B7/5841d717fe4375eac3353aaeaff675d326e8bc64b659499a5aa02278ff43f94ba524fa0326ab3172d1c7fbf3d0493e5cccf1ae04e0b2859ab90a7906596cea938ca1e8a7a5a8345a701769699ce90371ebdb8c6eaa8bf40327a651321c4f4f064f944d3e)

{% hint style="danger" %}
Your Lair’s process list does not show processes executed from the Lair terminal. The Lair terminal should be used for testing and any terminal sub-processes will be exited when the terminal session has been terminated.
{% endhint %}

#### Process statuses

* **Running**: process is being executed
* **Done**: process has exited without error (exit code 0), commonly from end-of-file
* **Killed**: process exited due to manual interruption
* **Failed**: process has exited due to error (exit code > 0)

### Terminating running processes

Running processes can be manually terminated by right-clicking on the respective row in the process list. Please allow for a few seconds delay as your process is terminated and its allocated container is spun down.

![](https://codahosted.io/docs/2kDMDaZ6QP/blobs/bl-1rRLXx3sKT/53614ecaa60630df33e8fdb77ca02224e956ea490df8133050f00d6b23e9628b45fe7187b88178822750fc3fcf4b53ede66a55c87e4c5590d2b58d31f0bc157ad8cdfe9e0ce944887d113596b414d6d719dfbeb9c7fadc43d628e8414d1bf9482436b435)
