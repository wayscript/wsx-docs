# Schedule a Task (cron)

WayScript allows you to configure your Lair to schedule task execution in minutes.

### Create `task.py`

Use the boilerplate code below to create a `task.py` file in your Lair’s root directory. See [File system](../platform/lairs/file-system.md) for more details on how to manipulate files in your workspace file system.

#### Boilerplate `task.py`

```python
i = 0
while i < 5:
    print("This prints five times.")
    i += 1
```

### Configure `cron` trigger

Open your Lair’s `.triggers` file and add a new `cron` trigger. Create a name for your trigger, input the following run command, and set an interval or custom cron syntax for your task. See [Triggers](../platform/lairs/triggers.md) for more details.

```
python task.py
```

### Test your task execution in development environment

Press “Run” to execute the run command and start your task’s process execution. Open your “Processes” list and select the running process to see the generated log.

![](../.gitbook/assets/screen-shot-2021-09-14-at-1.58.17-pm.png)

### Deploy to production environment

Your task will not be scheduled within your Lair’s development environment. Once you have finished testing, press “Deploy” to create a production environment for your task. See [Hosted environments](../platform/lairs/deployments.md) for more details.

{% hint style="info" %}
In order for your scheduled task to run, you must [Deploy](../platform/lairs/deployments.md) the lair!
{% endhint %}
