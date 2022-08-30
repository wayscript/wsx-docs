# New Relic

WayScript's NewRelic integration allows you to connect to your NewRelic account and set up default monitoring across your workspace's Lairs. You’ll get automatic visibility into the health of all pre-production, staging, and production environments via New Relic.

Adding the integration with enable two monitoring capabilities in your workspace Lairs:

* Auto-initialized infrastructure monitoring (only available in self-hosted deployments)
* Ability to configure APM agents and log forwarding

There are four main steps for connecting WayScript and New Relic:&#x20;

* Open a workspace for your team
* Create your first Lair&#x20;
* Enable the New Relic integration in WayScript
* Set up a New Relic APM agent in your Lair

### **Open a workspace for your team**

1. Sign up for a free WayScript account or sign in to an existing account.&#x20;

* Access WayScript at[ app.wayscript.com](https://app.wayscript.com/) or download the WayScript desktop app available for MacOS and Windows at[ wayscript.com/downloads](https://wayscript.com/downloads).&#x20;
* Create your account by following the [sign up instructions](https://app.wayscript.com/).

2\. [Create a workspace.](https://wsxdocs.wayscript.com/collaborating/configuring-your-workspace) Your WayScript workspace is where you and your team will collaborate on managing and shipping software. Note that you can invite others on your team to the workspace by selecting **+ Invite Team Member** at the bottom left of the screen.

### Create your first Lair

To create a Lair in your workspace:

1. Select the **Lair** tab in the left panel to navigate back to the Lair view.
2. In the Lair view, select **+ New Lair** in the top right of the screen.&#x20;
3. To get started coding from scratch, select a pre-built template to customize or create a blank Lair. Follow this [WayScript guide](https://wsxdocs.wayscript.com/quickstart) for some inspiration for tools to build. For now, you can select the **Flask** template under **Frameworks.**

### Enable the New Relic integration in WayScript

{% hint style="warning" %}
Note: To ensure your data moves seamlessly from WayScript to New Relic, make sure to complete the integration by following these steps before you deploy a Lair, which is covered in the next section.
{% endhint %}

1. Log in to New Relic or [sign up](https://newrelic.com/signup/?utm\_source=external\_partners\&utm\_medium=referral\&utm\_campaign=global-ever-green-io-partner\&utm\_content=wayscript) for a free account.
2. Create a New Relic integration in WayScript. In WayScript, go to integrations by selecting the **Workspace** dropdown menu in the top left corner. Select **Settings**, and then **Integrations.** On the integrations page, select **+New Integration**, and then **New Relic**.
3. Enter your New Relic `account_id` and `license_key`
   * You can find these values on the [WayScript data source page](https://onenr.io/0dQeVpxaDwe) in New Relic.
   * Optionally, you can choose to use a new license key. If so, read the [New Relic API key documentation](https://docs.newrelic.com/docs/apis/intro-apis/new-relic-api-keys) for instructions.
4. In WayScript, complete the integration by selecting **Create integration.**

### Set up APM for your Lairs (Python example)

Next, install a New Relic APM agent to monitor your Lair and anything you build inside it. WayScript supports development in any language, but this example uses  the [Python agent](https://docs.newrelic.com/docs/apm/agents/python-agent/installation/standard-python-agent-install/). To see all the APM agents available in New Relic, go to **** [**Add data**](http://one.newrelic.com/marketplace), and filter for [**Application monitoring**](https://onenr.io/0dQeVybYYwe).

1\. Configure the APM agent in the WayScript terminal. Select the Lair you want to monitor and select the **Develop** tab in the left panel. In the terminal that opens in the right panel, run these commands to generate the `newrelic.ini` config file for the Lair:\
pip install newrelic&#x20;

```
pip install newrelic 
newrelic-admin generate-config YOUR_LICENSE_KEY newrelic.ini
```

2\. Add New Relic to your `requirements.txt` file. Open the code editor by clicking on the **Show Code** icon in the bottom left pane. Select the `requirements.txt` file and add the following at the bottom of the file. If your Lair does not have a `requirements.txt` file, you can create one directly in the code editor:

```
newrelic
```

3\. Add a deploy trigger. Open the Triggers panel by clicking the last icon, **Show Triggers**, in the bottom left pane. Click the **+** icon at the top of the Triggers panel and select **deploy**. Paste the following command in **Command to Run**:

```
NEW_RELIC_CONFIG_FILE=newrelic.ini newrelic-admin run-program $YOUR_COMMAND_OPTIONS
```

Be sure to replace **`$YOUR_COMMAND_OPTIONS`** with your app’s command line, for example, `python app.py`.

1. Test the connection. Invoke a process in your Lair. (Select the play icon under Run on the deploy trigger or navigate to the Lair endpoint.)
2. Deploy your Lair to prod. Select **Deploy** from the left panel to open the deploy view and click **Deploy.** This promotes your changes from your development environment to an identical production environment with unique endpoints and will automatically run your deploy trigger.
3. Wait a few minutes for New Relic to start receiving your data. It should only take 5-10 minutes.
4. That’s it! Now you should be able to see your Lair and applications in [New Relic](http://one.newrelic.com/).

