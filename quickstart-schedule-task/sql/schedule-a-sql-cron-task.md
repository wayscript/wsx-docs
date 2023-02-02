# Schedule a SQL cron task

WayScript allows you to configure your Lair to schedule task execution in minutes.

### Create `sql-cron.py`

Use the boilerplate code below to create a `sql-cron.py` file in your Lair’s root directory. See [File system](../../platform/lairs/file-system.md) for more details on how to manipulate files in your workspace file system.

#### Boilerplate `sql-cron.py`

```python
import os
import mysql.connector


# These credentials can be found via your database credentials page
# For additional help with these values, please visit the docs of where your database is hosted.
mydb = mysql.connector.connect(
  host='lcpbq9az4jklobvq.cbetxkdyhwsb.us-east-1.rds.amazonaws.com',
  user='srwmp6imz2v547os',
  password=os.environ.get('password'),
  port=3306,
  database='c9h0n4i2bk671ofb'
)

# SQL statement to execute 
sql = "SELECT * FROM earnings;"
mycursor = mydb.cursor()
mycursor.execute(sql)
myresult = mycursor.fetchall()
print(myresult)
```

#### create a `requirements.txt` file:

```python
mysql-connector-python
```

### Configure `cron` trigger

Open your Lair’s `.triggers` file and add a new `cron` trigger. Create a name for your trigger, input the following run command, and set an interval or custom cron syntax for your task. See [Triggers](../../platform/lairs/triggers.md) for more details.

```
python sql-cron.py
```

<figure><img src="../../.gitbook/assets/cron-sql.jpg" alt=""><figcaption></figcaption></figure>

### Test your task execution in development environment

Press “Run” to execute the run command and start your task’s process execution. Open your “Processes” list and select the running process to see the generated log.

Be sure to install your requirements.txt via your terminal.

```
pip install -r requirements.txt
```

### Deploy to production environment

Your task will not be scheduled within your Lair’s development environment. Once you have finished testing, press “Deploy” to create a production environment for your task. See [Hosted environments](../../platform/lairs/deployments.md) for more details.
