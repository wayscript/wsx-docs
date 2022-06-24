# Integrations

Your WayScript workspace can be configured with integrations that allow your team to setup "blueprints" that establish defaults, across categories such as monitoring, deployment pipelines, secrets management, and more, for each Lair in your workspace.&#x20;

#### Supported integrations

| Integration         | Category   | Overview                                                                                                                            |
| ------------------- | ---------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| New Relic           | Monitoring | Auto-initialize infrastructure agent in your Lair processes and pass relevant environment variables to setup APM and log forwarding |
| AWS Secrets Manager | Secrets    | _(coming soon)_                                                                                                                     |
| CircleCI            | Pipelines  | _(coming soon)_                                                                                                                     |



### New Relic

WayScript's NewRelic integration allows you to connect to your NewRelic account and setup default monitoring across your workspace's Lairs.&#x20;

Adding the integration with enable two monitoring capabilities in your workspace Lairs:

* Auto-initialized infrastructure monitoring
* Ability to configure APM agents and log forwarding

{% hint style="info" %}
Currently, the integration offers the ability to automatically initialize New Relic's [infrastructure agent](https://docs.newrelic.com/docs/infrastructure/infrastructure-monitoring/get-started/get-started-infrastructure-monitoring) in your Lair processes and inject relevant environment variables for you to setup New Relic's APM agent and log forwarding for your service or script. The WayScript team plans to add additional functionality; please contact us  at nihar@wayscript.com with any requests.&#x20;
{% endhint %}

#### Enabling the New Relic integration (with default infrastructure monitoring)

1. [Sign up](https://newrelic.com/signup/) for a New Relic account or login to an existing acount.
2. Create a New Relic integration in WayScript, and enter your New Relic `account_id` and `license_key`. These values can be found by navigating to the WayScript partner page at [https://one.newrelic.com/external-install](https://one.newrelic.com/external-install) or selecting "Add more data" and then choosing WayScript from the "Partners" view.&#x20;
3. Navigate to your New Relic console and selects "Hosts" under "Infrastructure".
4. Invoke a process in your Lair (by pressing "Test" on a Lair trigger or navigating to a Lair endpoint).
5. Wait a few minutes for New Relic to start receiving your data.
6. Select a host to view live infrastructure metrics.&#x20;

#### Setting up a New Relic APM agent in your Lair

After enabling the integration, the following New Relic protected environment variables will be injected into your Lair's environments before process execution.&#x20;

* `NEW_RELIC_LICENSE_KEY`&#x20;
* `NEW_RELIC_APP_NAME` - set to `wayscript-<workspace_name>-<lair_name>-<env>`
* `NEW_RELIC_LABELS` - set to `wayscript:<workspace_name>-<lair_name>-<env>`&#x20;

You can use these values to setup the New Relic APM agent and log forwarding for your services or scripts. Please follow New Relic's [Python](https://docs.newrelic.com/docs/apm/agents/python-agent/installation/standard-python-agent-install) or [Node](https://docs.newrelic.com/docs/apm/agents/nodejs-agent/installation-configuration/install-nodejs-agent) documentation for detailed instructions. You will need to add New Relic package dependency and may need to modify your Lair trigger's run command, depending the language, framework, and your specified agent configuration.&#x20;
