# Self-hosting

WayScript is available for self-hosting on your organization's AWS infrastructure through easy provisioning using Terraform. Self-hosting WayScript ensures that all access to internal data is managed within your own cloud environment. You also have the flexibility to control the overall deployed footprint of WayScript to fit your organization’s needs and ability to configure SSO for your team.&#x20;

> Please contact us at [nihar@wayscript.com](mailto:nihar@wayscript.com) if you are interested in early access to this hosting option. The WayScript team will then provide access to the full self-hosted documentation hosted on the `wayscript-self-hosted` private [repo](https://github.com/wayscript/wayscript-self-hosted).&#x20;

### WayScript Release Process

We plan to distribute a new release of WayScript every two weeks to your account's ECR repo. In most cases, we recommend deploying the latest release available.

{% hint style="danger" %}
#### <mark style="color:red;">Avoid downgrading to a lower version</mark>

Downgrading can cause unpredictable issues due to database migrations that were run during your upgrades to the latest WayScript release.

Before you deploy a WayScript artifact from your ECR repo, check which numbered version of WayScript you're currently running. Then make sure that the artifact you want to deploy is pointing to a version that is ahead of your current version from the artifact details.

You can check your current WayScript version by visiting `https://<configured domain>/auth-service/health`.
{% endhint %}

### Releases

| Version   | Date       | Notes                                 |
| --------- | ---------- | ------------------------------------- |
| 1.0.2.193 | 2022-04-14 | Improve file handling and other fixes |
| 1.0.2.117 | 2022-03-30 | Add higher memory to Lair containers  |
| 1.0.2.114 | 2022-02-22 | Supports release of desktop app       |
| 1.0.2.90  | 2022-02-04 | Includes database migrations          |
| 1.0.2.71  | 2022-01-28 |                                       |
