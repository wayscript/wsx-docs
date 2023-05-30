# Usage

The Usage view shows usage analytics for Lairs in your Workspace. To access it, click on Usage in the left nav bar from the home page.

### Usage Components

<table><thead><tr><th width="194">Component</th><th>Definition</th></tr></thead><tbody><tr><td>Runtime</td><td>Monthly runtime hours is the total amount of time your scripts spend running. As an example, If you have a single HTTP endpoint that gets queried once per day and the script takes 5 seconds to run - that would be 150 seconds of runtime that month.</td></tr><tr><td>Invocations</td><td>Invocations are the number of times a script is kicked off via a trigger. This includes cron triggers, deployments, and HTTP endpoints. If a script runs once a day on a cron trigger, that is 30 invocations per month. If an HTTP endpoint is queried once per hour, that is 24 invocations in a day. </td></tr><tr><td>Triggers per Workspace</td><td>The number of triggers in a workspace. These include Cron, HTTP, and Deploy triggers. Note, a trigger in both a development and production environment counts as a single trigger. </td></tr><tr><td>Members</td><td>The number of team members in a workspace. </td></tr><tr><td>Lairs</td><td>The number of unique Lairs created within a workspace.</td></tr></tbody></table>
