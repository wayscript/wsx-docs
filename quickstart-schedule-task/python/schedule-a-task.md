# Schedule a Python cron task

WayScript allows you to configure your Lair to schedule task execution in minutes.

### Create `task.py`

Use the boilerplate code below to create a `task.py` file in your Lair’s root directory. See [File system](../../platform/lairs/file-system.md) for more details on how to manipulate files in your workspace file system.

#### Boilerplate `task.py`

```python
i = 0
while i < 5:
    print("This prints five times.")
    i += 1
```

### Configure `cron` trigger

Open your Lair’s [Triggers Panel](../../platform/lairs/triggers.md) and add a new `cron` trigger. Create a name for your trigger, input the following run command, and set an interval or custom cron syntax for your task. See [Triggers](../../platform/lairs/triggers.md) for more details.

```
python task.py
```

<figure><img src="../../.gitbook/assets/python-cron" alt=""><figcaption><p>Example Cron Trigger Setup</p></figcaption></figure>

### Test your task execution in the development environment

Press “Test” to execute the run command and start your task’s process execution. A process tab should open in your Terminal view.&#x20;

<figure><img src="../../.gitbook/assets/python-cron-task.png" alt=""><figcaption><p>Press Test in your Triggers view to test your cron Trigger. When ready, deploy it to production!</p></figcaption></figure>

### Deploy to a Production environment

Your task will not be scheduled within your Lair’s development environment. Once you have finished testing, Go to the [Deploy Panel](../../platform/lairs/deployments.md) to deploy a production instance of your task.&#x20;

{% hint style="info" %}
In order for your scheduled task to run, you must [Deploy](../../platform/lairs/deployments.md) the lair!
{% endhint %}

### View Logs

[Logs](../../platform/lairs/logs.md) are automatically stored for both Development tests and Production runs of your task.&#x20;
