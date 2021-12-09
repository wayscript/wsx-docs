# Triggers

Your Lair can be configured with triggers that can execute processes through internal or external events. The WayScript team plans to add additional triggers based on user request. Please visit our [feedback page](http://wayscript.canny.io/wayscript-x) to vote for your favorites!

**Internal triggers**

* `cron` - invoke process on schedule
* `deploy` - invoke process when Lair is deployed

**External triggers**

* `http` - invoke process when a request is made to a HTTP endpoint
* _**(coming soon)**_ `email`

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
Configured triggers only invoke processes in production Lair environments. However, you can test your triggers by manually running them through the configuration modal or using the generated development endpoints. See [Hosted environments](../managing-tools/environments.md) for more details on development vs. production environments.
{% endhint %}

### Manually invoking your trigger

After opening the `.triggers` file, select an existing trigger to open the configuration modal. Press “Run” to execute your trigger’s run command and start the process execution. See [Processes](../testing-and-visiblity/processes.md) for more details on how to view and manage processes.

### Accessing your trigger’s events

Your triggers can pass data payloads, called events in WayScript X, to your processes. See [Events](events.md) for more details on how these events can be accessed.
