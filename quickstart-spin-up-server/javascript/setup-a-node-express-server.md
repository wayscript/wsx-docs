# Setup a Node Express server

WayScript allows you to configure your Lair to host a running microservice in minutes. Follow this guide to setup a simple NodeJS app in your Lair.&#x20;

{% embed url="https://www.youtube.com/watch?v=v6opIdJYGnI" %}

### Create server.js or load node files

Use the boilerplate code below to create a server.js file in your Lair’s root directory. Or if you have an existing project, copy or clone your project files into your Lair’s directory. See [File system](../../platform/lairs/file-system/) for more details on how to manipulate files in your workspace file system.

#### Boilerplate server.js

```javascript
const express = require('express')
const app = express()
const port = 8080

app.get('/', (req, res) => {
  res.send('Hello World!')
})

app.listen(port, () => {
  console.log(`Example app listening on port ${port}`)
})
```

### Create package.json file for dependencies

Create a `package.json` file in your Lair’s root directory. You can also specify any additional dependencies your app requires. See [Hosted environments ](../../platform/lairs/deployments.md)for more details.

#### Boilerplate package.json

```json
{
    "scripts": {
      "start": "node ./server.js"
    },
    "dependencies": {
      "express": "^4.17.2"
    }
}
```

### Configure `deploy` trigger

Open your Lair’s `.triggers` file and add a new `deploy` trigger. Create a name for your trigger and input the following run command and port number `8080` (or modified command and port number based on your app requirements). See [Triggers](../../platform/lairs/triggers.md) for more details.

```
npm install && npm run start
```

{% hint style="info" %}
Make sure to set the Port to 8080 on your Deploy Trigger!
{% endhint %}

### Test app in development environment

Press “Test” to execute the run command and start your web server process (see [Processes](../../platform/lairs/processes.md) for more details). Navigate to the `*.wayscript.cloud` endpoint generated to see your Node app in action!

### Deploy to production environment

Once you have finished testing, press “Deploy” to create a production environment for your Node app.&#x20;

{% hint style="warning" %}
By default, your Lair's endpoints are protected against unauthenticated requests. See [endpoints.md](../../platform/lairs/endpoints.md "mention") on how to public expose your endpoints or authenticate using your application key.
{% endhint %}

