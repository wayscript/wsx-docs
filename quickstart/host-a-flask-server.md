# Host a Flask app

WayScript X allows you to configure your Lair to host a Flask app in minutes.

### Create `main.py` or load Flask files

Use the boilerplate code below to create a `main.py` file in your Lair’s root directory. Or if you have an existing Flask project, copy or clone your project files into your Lair’s directory. See [File system](../building-tools/file-system.md) for more details on how to manipulate files in your workspace file system.  
\[add file menu\]

#### Boilerplate `main.py`

```python
# my-lair-a > main.py

from flask import Flask

app = Flask(__name__)

@app.route('/')
def hello_world():
    return 'Hello World'
    
if __name__ == '__main__':
    app.run()
```

### Add packages to `requirements.txt`

Create a `requirements.txt` file in your Lair’s root directory and specify the `flask` package. You can also specify any additional dependencies your app requires. See [Hosted environments ](../managing-tools/environments.md)for more details.

```text
# my-lair > requirements.txt
flask==2.0.1
```

### Configure `on deploy` trigger

Open your Lair’s `.triggers` file and add a new `on deploy` trigger. Create a name for your trigger and input the following run command and port number 8080 \(or modified command and port number based on your app requirements\). See [Triggers](../building-tools/triggers.md) for more details.

```text
$ FLASK_APP=main.py FLASK_ENV=development flask run --port 8080
```

### Test app in development environment

Press “Run” to push your files to remote \(see [File system](../building-tools/file-system.md) for more details\), execute the run command and start your web server process \(see [Processes](../testing-and-visiblity/untitled.md) for more details\). Navigate to the `*.wayscript.cloud` endpoint generated to see your Flask app in action!  
\[run button and endpoint\]

{% hint style="success" %}
After setting your FLASK\_ENV to development, modifying your app’s files will automatically restart your server process.
{% endhint %}

### Deploy to production environment

Once you have finished testing, press “Deploy” to create a production environment for your Flask app. Select `<Lair_name>.prod` in the Lair selector menu and view the `on deploy` trigger to access your app’s production endpoint. See [Hosted environments](../managing-tools/environments.md) for more details.

