# Deployments

Your Lair is configured with two hosted environments: **development and production**. While building your tools in WayScript, you are interacting with your Lair’s development environment. Once your tool is ready for use, it can be deployed to your Lair’s production environment.

Both development and production environments are use WayScript’s base container image (see [Lairs](lairs.md) for more details), so tools that have been tested on your development environment will have identical execution without any configuration. However, there are a few key operational distinction between development and production environments:

* Triggers are not invoked in development environments. You must use manual invocations and test events in your Lair’s development environment to test your triggers’ functionality. See [Triggers](triggers.md) for more details.
* Files cannot be directly modified in production environments. Please modify files in your Lair’s development environment and then deploy to your production environment. See [File system](file-system.md) for more details.
* WayScript will generate different endpoints for your development and production environments. Please ensure you are using the correct endpoint when accessing your tools.

### Deploying your Lair to production environment

Once your tool has been tested with your Lair’s development environment, simply click “Deploy” to setup a production environment.

![](https://codahosted.io/docs/2kDMDaZ6QP/blobs/bl-AXtnWh-Z-8/6b2594d660acf4d949ac26910a64efb47bb0d25bdaba678f08f20eefb795aa54b1ac27fd5df373c743ce313e4573b77d5507526f11059aacfd3984e69e2d5a2e9615c546209f4441b104eafbe749c7df5746e4e58821781c81a2cbea00dd729793e951f5)

### Accessing your Lair’s production environment

After your first deployment, your production environment can be accessed by selecting `<Lair_name>.prod>` in the Lair selector menu.

![](https://codahosted.io/docs/2kDMDaZ6QP/blobs/bl-f3PLYNXimn/42911fbf2b98e2bbf6165b336fa36c73ac0738805ea70a4c859459fb45ef874a3edad2c2740b15754d7d4ccf14b392ce9fb44b9b8987247ac439c52cf90ac22ba24059eb019a8e9de3ba30f1ee4178faad9e6f032e766d2f48e01cd0b6daa87d2d76f6d9)

{% hint style="warning" %}
Warning Your Lair’s production environment is hosted on remote, so it can only be accessed through a network connection. Files from your production environments will also not sync to your local machine when using the WayScript X desktop app.
{% endhint %}

### Using external packages within your hosted environments

External packages can be installed into your Lair’s environments for your tools to access. Packages will be installed in your environments during your Lair’s first process execution and cached for future execution.

{% hint style="info" %}
WayScript currently supports Python packages through the `pip` package manager, but our team is working on supporting other protocols in the near future.
{% endhint %}

**Python**

External packages must be added to a `requirements.txt` file located at the root level of your Lair directory to persist in your Lair’s hosted environments.

```
# my-lair-a > requirements.txt
Flask==2.0.1
beautifulsoup4==4.6.3
pandas==0.23.3
```

If you install packages using your Lair terminal (e.g., through `pip install`) while testing your tools, you can generate your `requirements.txt` file using `pip freeze` .

```
~/my-lair-a $ pip install pandas
~/my-lair-a $ pip freeze > requirements.txt
```

{% hint style="warning" %}
When using local file sync, you must “Fetch” and “Pull” after using `pip freeze` to see your `requirements.txt` file in your Lair’s file system. See [File system](file-system.md) more details.
{% endhint %}
