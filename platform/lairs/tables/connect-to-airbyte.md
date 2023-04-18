# Connect to Airbyte

{% hint style="info" %}
Tables are currently in Alpha release. To try out this feature and join the Alpha, please contact us at [team@wayscript.com](mailto:team@wayscript.com) with the subject line “WayScript Tables Alpha”.
{% endhint %}

Use WayScript Tables as a Postgres data destination for your Airbyte connections. Follow these instructions to set up the connection.

1. Login to [Airbyte](https://airbyte.com/)
2. Create new connection
3. Select or setup your source (ex Google Sheets)
4. Select "Set up the destination" and then select  "Postgres"
5. Add your provided WayScript Table Credentials and click "Set up destination"
6. Back in Airbyte, under “Configuration”, set the “Replication Frequency” to “Manual”
7. Press “Setup Connection”
8. In Sync History, press “Sync Now” to update your WayScript Table
9. Set up a Lair to access your WayScript Table database. See an example setup.[postgres-database.md](../../../resources/code-snippets/postgres-database.md "mention")&#x20;
10. Using the example above, you can run `python main.py` in your Lair's terminal to query your WayScript Table
