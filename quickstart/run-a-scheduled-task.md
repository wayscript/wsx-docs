# Schedule a task

WayScript X allows you to configure your Lair to schedule task execution in minutes.

### Create `task.py`

Use the boilerplate code below to create a `task.py` file in your Lair’s root directory. See [File system](../building-tools/file-system.md) for more details on how to manipulate files in your workspace file system.

![](https://codahosted.io/docs/2kDMDaZ6QP/blobs/bl-Iqkx-tphjD/3d584a55f32dbc8c4e8cf462e3eb9867bbcaf47440586f29d25f94abb1d90be28f4433566d59fc5bfeef80fb761d4e93785f99ec6a64bd561d70e8c2785ae52f342dcf4729de3a496500f8f7ee8d21e20f6ee3321ca9844abc41275391641b8d1fff3ebe)

#### Boilerplate `task.py`

```python
# my-lair-a > task.py

i = 0
while i < 5:
    print("This prints five times.")
    i += 1
```

### Configure `cron` trigger

Open your Lair’s `.triggers` file and add a new `cron` trigger. Create a name for your trigger, input the following run command, and set an interval or custom cron syntax for your task. See [Triggers](../building-tools/triggers.md) for more details.

```text
$ python task.py
```

### Test your task execution in development environment

Press “Run” to push your files to remote \(see [File system](../building-tools/file-system.md) for more details\), execute the run command, and start your task’s process execution. Open your “Processes” list and select the running process to see the generated log.

![](../.gitbook/assets/screen-shot-2021-09-14-at-1.58.17-pm.png)

### Deploy to production environment

Your task will not be scheduled within your Lair’s development environment. Once you have finished testing, press “Deploy” to create a production environment for your task. See [Hosted environments](../managing-tools/environments.md) for more details.

