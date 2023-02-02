# Quickstart: Spin up a web server or framework

### **1) Create a workspace**

* Access WayScript at [app.wayscript.com](https://app.wayscript.com) or download the WayScript desktop app available for MacOS and Windows at [https://www.wayscript.com/downloads](https://wayscript.com/downloads).
* Enter a name for your workspace.&#x20;

![](<../.gitbook/assets/Env 1.png>)

The WayScript desktop app will create files on your local machine and sync them to a remote server. You be able to sync your files to a local directory if accessing WayScript from your browser. See [Configuring your workspace](../platform/workspace/) for more details on workspaces.&#x20;

![](https://codahosted.io/docs/2kDMDaZ6QP/blobs/bl-ctT1lSpsA8/897d5cb37c8557ad9b149526e93a87b16af4e7f0f0be3aa51e4bd08c6d58007c44949fb53d3f804d60ab6953bb3c4909efbdda87870c6cf9e4af93f351cc2f42f482aa8e814a011346a8e71807b8ad97ce8824146ad13a8b7a1b3d966da21b512ef7ef54)

### **2) Create a Lair**

[Lairs](../platform/lairs/) are preconfigured, containerized, and flexible development environments for your code.

* Inside your workspace, select “+ New Lair” to create your first Lair!

![](../.gitbook/assets/screen-shot-2021-09-14-at-1.50.08-pm.png)

Now that you have created a Lair, follow one of our 5-minute tutorial to get started building tools on WayScript:

{% content-ref url="../quickstart-webhook-microservice/build-an-api.md" %}
[build-an-api.md](../quickstart-webhook-microservice/build-an-api.md)
{% endcontent-ref %}

{% content-ref url="../quickstart-schedule-task/python/schedule-a-task.md" %}
[schedule-a-task.md](../quickstart-schedule-task/python/schedule-a-task.md)
{% endcontent-ref %}

{% content-ref url="host-a-flask-server.md" %}
[host-a-flask-server.md](host-a-flask-server.md)
{% endcontent-ref %}

{% content-ref url="set-up-fastapi-server.md" %}
[set-up-fastapi-server.md](set-up-fastapi-server.md)
{% endcontent-ref %}

### **3)** Deploy a Lair &#x20;

* Once You have created a lair and built a tool, deploy your lair. Deploying affects different triggers and their functionality ( i.e. cron triggers only execute in deployed lairs )

<figure><img src="../.gitbook/assets/DeployWayScriptLairExample.jpg" alt=""><figcaption></figcaption></figure>

* Click deploy twice more on the following interfaces to confirm the deployment of your lair.

{% hint style="info" %}
Once deployed, triggers may activate or provide new production endpoints. For additional information on how deployment works with specific triggers, please view the [triggers page](../platform/lairs/triggers.md).
{% endhint %}

{% hint style="warning" %}
To avoid automatic Lair de-deployment, [subscribe to a paid plan](https://www.wayscript.com/pricing) or make sure to log into your WayScript account at least once every 3 months.&#x20;
{% endhint %}

### 4) Invite Teammates&#x20;

Workspaces can be shared with others. This allows them to access, edit, and use the applications within the workspace depending on their [collaborating permissions](../platform/workspace/members.md). To invite new members into your workspace:

* Access the home view of your workspace

<figure><img src="../.gitbook/assets/workspacehomeview.jpg" alt=""><figcaption></figcaption></figure>

* Select the drop down menu located next to your workspace name ( top left corner of the application )
* Select Settings&#x20;
* Then select members

{% hint style="info" %}
An alternative hotkey to access workspace settings is `W` then `S`
{% endhint %}

* On the members page of your workspace settings, select "Add Members" in the top right corner
*

    <figure><img src="../.gitbook/assets/workspace-members-invite.jpg" alt=""><figcaption><p>( Purple Button in top right )</p></figcaption></figure>
* Enter the emails of the members you would like to invite.

