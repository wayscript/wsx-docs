# Setup a Django Server (Python)

WayScript allows you to configure your Lair to host a running microservice in minutes. Follow this guide to setup a simple Django app in your Lair.&#x20;

{% embed url="https://youtu.be/LoXVosOzvJg" %}

### Add packages to `requirements.txt`

Create a `requirements.txt` file in your Lair’s root directory and specify the django package. You can install the django package via `pip` in your Lair [Terminal](../platform/lairs/terminal.md). You can also specify any additional dependencies your app requires. See [Hosted environments ](../platform/lairs/deployments.md)for more details.

```
pip install django
pip freeze > requirements.txt
```

### Start Django Project&#x20;

Enter into the [Terminal](../platform/lairs/terminal.md):

```
django-admin startproject mysite
```

This creates your Django project

{% hint style="info" %}
`mysite` can be changed to whatever you want as a project name
{% endhint %}

### Configure `deploy` trigger

Open your Lair’s `.triggers` file and add a new `deploy` trigger. Create a name for your trigger and input the following run command and port number `8080` (or modified command and port number based on your app requirements). See [Triggers](../platform/lairs/triggers.md) for more details.

```
python mysite/manage.py runserver 0.0.0.0:8080
```

### Setting Django Hosts

Once your project is created, Django will require the domain that hosts your application to be added to the `settings.py` file in your application directory. You can grab the domain from your Deploy [Trigger](../platform/lairs/triggers.md) or from the [Endpoints](../platform/lairs/endpoints.md) tab.&#x20;

```
ALLOWED_HOSTS = ['<DOMAIN_FROM_DEPLOY_TRIGGER>']
```

### Test app in development environment

Press “Run” to execute the run command and start your web server process (see [Processes](../platform/lairs/processes.md) for more details). Navigate to the `*.wayscript.cloud` endpoint generated to see your Flask app in action!

### Deploy to production environment

Once you have finished testing, press “Deploy” to create a production environment for your Flask app. Select `<Lair_name>.prod` in the Lair selector menu and view the `on deploy` trigger to access your app’s production endpoint. See [Hosted environments](../platform/lairs/deployments.md) for more details.

{% hint style="warning" %}
By default, your Lair's endpoints are protected against unauthenticated requests. See [endpoints.md](../platform/lairs/endpoints.md "mention") on how to public expose your endpoints or authenticate using your application key.
{% endhint %}
