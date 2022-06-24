# Triggers

Your Lair can be configured with triggers that can execute processes through internal or external events. The WayScript team plans to add additional triggers based on user request. Please visit our [feedback page](http://wayscript.canny.io/wayscript-x) to vote for your favorites!

**Internal triggers**

* `cron` - invoke process on schedule
* `deploy` - invoke process when Lair is deployed; used to start long-running processes such as active services

**External triggers**

* `http` - invoke process when a request is made to a HTTP endpoint

{% hint style="info" %}
**Special considerations for triggers:**

* `deploy` and `http` triggers generate custom endpoints for your Lair. See [endpoints.md](endpoints.md "mention") for more details on how to manage endpoints.&#x20;
* `cron` triggers only invoke processes in your Lair's production environment. See [deployments.md](deployments.md "mention") for more details on how to deploy your tool to your Lair's production environment.
{% endhint %}

## Trigger operations

### Adding a trigger to your Lair

Triggers are configured through the `.triggers` file stored within your Lair’s root directory. Open the `.triggers` file from your file system and select “+ New Trigger” to add a new trigger.

![](https://codahosted.io/docs/2kDMDaZ6QP/blobs/bl-7r4AdieLZI/38dea46748c5d047a11db97c4601a98185f5e092db6ec6d77cf93090a2e8471f521de7d93e446c3906aab2a48ef7a6b81454d5843dbe4c5bc244fb267c21e5e76908db7a36b091a2278b90dbca0d8be3e4fe7283b6a47890feb67d3c83f84904b0049115)

Choosing a trigger will open a configuration modal. Along with custom fields specific to the intended functionality, triggers have the following basic configuration elements:

* Choose a **name** for your trigger.
* Set a **run command** to invoke a process for your trigger.
* (Optional) Select a JSON file that contains a test event object. See [Events](events.md) for more details.

![](https://codahosted.io/docs/2kDMDaZ6QP/blobs/bl-KKu-fOByjs/e45a4b3e1c99a95e4823d58ea3f21d4667ab25d2f3abab80100cd00a986a778a58761f29dcfe928034207914b3dec2b62a354202641f4d874a489f3e5b75ef68c44102604b6dbc3f297bf01fd4cfd429e962ff9d9e6ff39a35b2a7613134941adfaced02)

After editing your trigger’s configuration, press “Save” to add your configuration to the `.triggers` file. You will also have to “Push” your workspace’s file system to update this configuration on your remote Lair.

{% hint style="warning" %}
Configured triggers only invoke processes in production Lair environments. However, you can test your triggers by manually running them through the configuration modal or using the generated development endpoints. See [Hosted environments](deployments.md) for more details on development vs. production environments.
{% endhint %}

### Manually invoking your trigger

After opening the `.triggers` file, select an existing trigger to open the configuration modal. Press “Run” to execute your trigger’s run command and start the process execution. See [Processes](../testing-and-visiblity/processes.md) for more details on how to view and manage processes.

### Accessing your trigger’s events

Your triggers can pass data payloads, called events in WayScript, to your processes. See [Events](events.md) for more details on how these events can be accessed.

## Implementation considerations

Your triggers in WayScript are flexible, whereas they can invoke a process through any run command. However, in general, the `http` trigger routes HTTP requests to independent, asynchronous processes running in separate containers, while using the `deploy` trigger routes HTTP requests to a running service process in a single container.&#x20;

Therefore, when designing your tool, it is useful to consider the following system characteristics to optimize performance of your tool.&#x20;

#### Request latency

Requests made to `http` triggers vs. running service processes deployed via the `deploy` trigger will _**ALWAYS**_ have higher latency due to serverless execution. When a request is made to an `http` trigger, the WayScript system must provision a new container, install any new dependencies, and attach logs before the request can be returned.&#x20;

#### Request volume

If your tool will receive a high volume of requests, we recommend setting up a running service to reduce the number of logs generated and mitigate any losses of latency during periods of high WayScript system use (usually during ET business hours).&#x20;

However, the WayScript team is actively working on improving the system's container orchestration, so this issue may be less pronounced in the future.&#x20;

#### Scalability of endpoints

You can add multiple `http` triggers to your Lair and specify different paths for each trigger, but setting up a running service process gives you unlimited scalability of endpoints and more fine-tuned control of endpoint characteristics.&#x20;

#### Runtime usage

While WayScript has not yet implemented workspace runtime restrictions, the team may add these in the future. Containers provisioned for processes invoked by `http` triggers will be torn down on process exit, and therefore in cases of low volume of requests, this approach will use less system runtime.&#x20;

