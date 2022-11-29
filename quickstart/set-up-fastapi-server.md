# Setup a FastAPI Server (Python)

WayScript allows you to configure your Lair to host a running microservice in minutes. Follow this guide to set up a simple FastAPI app in your Lair.&#x20;

{% embed url="https://www.youtube.com/watch?v=ura1p4W0D0k" %}

### Create `main.py` or load FastAPI files

Use the boilerplate code below to create a `main.py` file in your Lair’s root directory. Or if you have an existing FastAPI project, copy or clone your project files into your Lair’s directory. See [File system](../platform/lairs/file-system.md) for more details on how to manipulate files in your workspace file system.

### Set Up main.py

```python
from fastapi import FastAPI

# Creates our FastAPI application
app = FastAPI()

# Home route
# returns JSON response of dictionary after the return statement
@app.get("/")
def home():
    return {'data': 'Hello world'}
```

### Add packages to `requirements.txt`

Create a `requirements.txt` file in your Lair’s root directory and specify the fastapi and uvicorn packages. You can do so by `pip` installing them in your WayScript [Terminal](../platform/lairs/terminal.md). You can also specify any additional dependencies your app requires. See [Hosted environments ](../platform/lairs/deployments.md)for more details.

```
pip install fastapi
pip install uvicorn
pip freeze > requirements.txt
```

### Configure `deploy` trigger

Open your Lair’s `.triggers` file and add a new `deploy` trigger. Create a name for your trigger and input the following run command and port number `8080` (or modified command and port number based on your app requirements). See [Triggers](../platform/lairs/triggers.md) for more details.

```
python -m uvicorn main:app --reload --host 0.0.0.0 --port 8080
```

Press the play button on your triggers table to execute the run command and start your web server process (see [Processes](../platform/lairs/processes.md) for more details). Navigate to the `*.wayscript.cloud` endpoint generated to see your FastAPI app in action!

### Deploy to production environment

Once you have finished testing, press “Deploy” to create a production environment for your FastAPI app. Select `<Lair_name>.prod` in the Lair selector menu and view the `on deploy` trigger to access your app’s production endpoint. See [Hosted environments](../platform/lairs/deployments.md) for more details.

{% hint style="warning" %}
By default, your Lair's endpoints are protected against unauthenticated requests. See [endpoints.md](../platform/lairs/endpoints.md "mention") on how to public expose your endpoints or authenticate using your application key.
{% endhint %}

{% hint style="success" %}
For a cloneable version of a FastAPI lair, see [this template](https://app.wayscript.com/lairs/cac77abc-3c44-4299-8cc3-f5fde7d6fe10/public/).
{% endhint %}

