# Schedule a task

WayScript X allows you to configure your Lair to schedule task execution in minutes.

### Create `task.py`

Use the boilerplate code below to create a `task.py` file in your Lair’s root directory. See [File system](https://coda.io/d/WayScript-X-Docs_d2kDMDaZ6QP/File-system_sua4L) for more details on how to manipulate files in your workspace file system.  
\[add file menu\]

#### Boilerplate task.py

```python
# my-lair-a > api.py

import time

while i > 5:
    print("This prints once a minute.")
    time.sleep(60)
```

### Configure `cron` trigger

Open your Lair’s `.triggers` file and add a new `cron` trigger. Create a name for your trigger, input the following run command, and set an interval or custom cron syntax for your task. See [Triggers](https://coda.io/d/WayScript-X-Docs_d2kDMDaZ6QP/Triggers_suAFX) for more details.

```text
$ python task.py
```

### Test your task execution in development environment

Press “Run” to push your files to remote \(see [File system](https://coda.io/d/WayScript-X-Docs_d2kDMDaZ6QP/File-system_sua4L) for more details\), execute the run command, and start your task’s process execution. Open your “Processes” list and select the running process to see the generated log.

### Deploy to production environment

Your task will not be scheduled within your Lair’s development environment. Once you have finished testing, press “Deploy” to create a production environment for your task. See [Hosted environments](https://coda.io/d/WayScript-X-Docs_d2kDMDaZ6QP/Hosted-environments_suwGe) for more details.

