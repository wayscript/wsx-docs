---
description: >-
  Our API provides access to many of the functions and data available to the
  WayScript client application.
---

# WayScript HTTP API

{% swagger method="get" path="/processes/{process_id}/detail" baseUrl="https://api.wayscript.com" summary="Get Process Details" %}
{% swagger-description %}
Get detailed information about a specific process
{% endswagger-description %}

{% swagger-parameter in="path" required="true" name="process_id" %}
UUID of the process

\


(most often from 

`WS_PROCESS_ID`

 environment variable)
{% endswagger-parameter %}

{% swagger-parameter in="header" name="authorization" required="true" %}
Authentication key for API access.

Set equal to:&#x20;

"Bearer " + `WAYSCRIPT_EXECUTION_USER_TOKEN`
{% endswagger-parameter %}

{% swagger-parameter in="header" name="content-type" required="true" %}
Defines expected return types from the HTTP request.

Set equal to: "application/json"
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="JSON payload of process details" %}
```json
{
    event: {
        id: <uuid>,
        trigger_type: <str>,
        data: <json>,
        meta: <json>,
        created_date: <datetime>,
    },
    process: {
        id: <uuid>,
        lair_id: <uuid>,
        trigger_id: <str>,
        service_id: <str>,
        event_id: <uuid>,
        workspace_id: <uuid>,
        user_id: <uuid>,
        command: <str>,
        port: <str>,
        created_date: <datetime>,
        commpleted_date: <datetime>,
        last_activity: <datetime>,
    },
    lair_trigger: {
        trigger_id: <uuid>,
        lair_id: <uuid>,
        workspace_id: <uuid>,
        type: <str>,
        test_event: <str>,
        command: <str>,
        workspace_integration_id: <uuid>,
        settings: <json>,
        data: <json>,
        created_date: <datetime>,
        archived_date: <datetime>,
    },
}
```
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="" %}

{% endswagger-response %}

{% swagger-response status="404: Not Found" description="Process not found" %}

{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/workspaces/{workspace_id}" baseUrl="https://api.wayscript.com" summary="Get Workspace Details" %}
{% swagger-description %}
Get detailed information about a specific workspace
{% endswagger-description %}

{% swagger-parameter in="header" name="authorization" required="true" %}
Authentication key for API access.

Set equal to:&#x20;

"Bearer " + `WAYSCRIPT_EXECUTION_USER_TOKEN`
{% endswagger-parameter %}

{% swagger-parameter in="header" name="content-type" required="true" %}
Defines expected return types from the HTTP request.

Set equal to: "application/json"
{% endswagger-parameter %}

{% swagger-parameter in="path" name="workspace_id" required="true" %}
UUID of the workspace (most frequently from 

`/processes/{process_id}/detail`

)
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="JSON payload of workspace details" %}
```json
{
    id: <uuid>,
    name: <str>,
    owner_id: <uuid>,
    account_tier_id: <uuid>,
    cron_timezone: <str>,
    created_date: <datetime>,
}
```
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="" %}

{% endswagger-response %}

{% swagger-response status="404: Not Found" description="Workspace not found" %}

{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/workspaces/{workspace_id}/users/self" baseUrl="https://api.wayscript.com" summary="Get User Details via Application Key" %}
{% swagger-description %}
Get details about a specific user
{% endswagger-description %}

{% swagger-parameter in="header" name="authorization" required="true" %}
Authentication key for API access.

Set equal to:&#x20;

"Bearer " + `WAYSCRIPT_EXECUTION_USER_APPLICATION_KEY`
{% endswagger-parameter %}

{% swagger-parameter in="header" name="content-type" required="true" %}
Defines expected return types from the HTTP request.

Set equal to: "application/json"
{% endswagger-parameter %}

{% swagger-parameter in="path" name="workspace_id" required="true" %}
UUID of the workspace (most frequently from 

`/processes/{process_id}/detail`

)
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="JSON payload of user details" %}
```json
{
    id: <uuid>,
    email: <str>,
    first_name: <str>,
    last_name: <str>,
    avatar: <str>,
    created_date: <str>,
    last_login: <str>,
    groups: [
        {
            id: <uuid>,
            name: <str>,
            workspace_id: <uuid>,
            owner_id: <uuid>,
            system_managed: <boolean>,
        },
        ...
    ],
}
```
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="" %}

{% endswagger-response %}

{% swagger-response status="404: Not Found" description="Workspace not found" %}

{% endswagger-response %}

{% swagger-response status="404: Not Found" description="Application Key not found" %}

{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/lairs/{lair_id}" baseUrl="https://api.wayscript.com" summary="Get Lair Details" %}
{% swagger-description %}
Get details about a specific lair
{% endswagger-description %}

{% swagger-parameter in="header" name="authorization" required="true" %}
Authentication key for API access.

Set equal to:&#x20;

"Bearer " + `WAYSCRIPT_EXECUTION_USER_TOKEN`
{% endswagger-parameter %}

{% swagger-parameter in="header" name="content-type" required="true" %}
Defines expected return types from the HTTP request.

Set equal to: "application/json"
{% endswagger-parameter %}

{% swagger-parameter in="path" name="lair_id" required="true" %}
UUID of the lair (most frequently from 

`/processes/{process_id}/detail`

)
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="JSON payload of lair details" %}
```json
{
    id: <uuid>,
    internal_id: <int>,
    name: <str>,
    friendly_name: <str>,
    workspace_id: <uuid>,
    manager_id: <uuid>,
    last_run_date: <datetime>,
    is_public: <boolean>,
    endpoints_are_private: <boolean>,
    created_date: <datetime>,
    default_path: <str>,
    environment: <str>,
    last_deployed: <datetime>,
    endpoint: <str>
}
```
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="" %}

{% endswagger-response %}

{% swagger-response status="404: Not Found" description="Lair not found" %}

{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/workspace-integrations/{workspace_integration_id}" baseUrl="https://api.wayscript.com" summary="Get Workspace Integration Details" %}
{% swagger-description %}
Get details about a specific workspace integration
{% endswagger-description %}

{% swagger-parameter in="path" name="workspace_integration_id" required="true" %}
UUID of the workspace integration
{% endswagger-parameter %}

{% swagger-parameter in="header" name="authorization" required="true" %}
Authentication key for API access.

Set equal to:&#x20;

"Bearer " + `WAYSCRIPT_EXECUTION_USER_TOKEN`
{% endswagger-parameter %}

{% swagger-parameter in="header" name="content-type" required="true" %}
Defines expected return types from the HTTP request.

Set equal to: "application/json"
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="JSON payload of workspace integration details" %}
```json
{
    id: <uuid>,
    name: <str>,
    user_id: <uuid>,
    workspace_id: <uuid>,
    type: <str>,
    credentials: <str>, //json blob as string
    credentials_state: <str>,
    external_account_id: <str>,
    settings: <str>, //json blob as string
}
```
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="" %}

{% endswagger-response %}

{% swagger-response status="404: Not Found" description="Workspace integration not found" %}

{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/workspace-integrations/workspace/{workspace_id}" baseUrl="http://api.wayscript.com" summary="Get All Workspace Integrations Details" %}
{% swagger-description %}
Get all workspace integration details for a workspace
{% endswagger-description %}

{% swagger-parameter in="path" name="workspace_id" required="true" %}
UUID of the workspace (most frequently from 

`/processes/{process_id}/detail`

)
{% endswagger-parameter %}

{% swagger-parameter in="header" name="authorization" required="true" %}
Authentication key for API access.

Set equal to:&#x20;

"Bearer " + `WAYSCRIPT_EXECUTION_USER_TOKEN`
{% endswagger-parameter %}

{% swagger-parameter in="header" name="content-type" required="true" %}
Defines expected return types from the HTTP request.

Set equal to: "application/json"
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="List of JSONs of workspace integration details" %}
```
[
    {
        id: <uuid>,
        name: <str>,
        user_id: <uuid>,
        workspace_id: <uuid>,
        type: <str>,
        credentials: <str>, //json blob as string
        credentials_state: <str>,
        external_account_id: <str>,
        settings: <str>, //json blob as string
    },
    ...
]
```


{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="" %}

{% endswagger-response %}

{% swagger-response status="404: Not Found" description="Workspace not found" %}

{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="/webhooks/http-trigger/response/{process_id}" baseUrl="https://api.wayscript.com" summary="Post HTTP Trigger Response" %}
{% swagger-description %}
Send a response to the caller of an 

`http`

 trigger
{% endswagger-description %}

{% swagger-parameter in="path" name="process_id" %}
UUID of the process

\


(most often from 

`WS_PROCESS_ID`

 environment variable)
{% endswagger-parameter %}

{% swagger-parameter in="header" name="authorization" %}
Authentication key for API access.

Set equal to:&#x20;

"Bearer " + `WAYSCRIPT_EXECUTION_USER_TOKEN`
{% endswagger-parameter %}

{% swagger-parameter in="header" name="content-type" %}
Defines expected return types from the HTTP request.

Set equal to: "application/json"
{% endswagger-parameter %}

{% swagger-parameter in="body" name="payload" type="JSON" %}
JSON payload containing the desired resposne for the `http` trigger process given via process\_id



{ data: \<json>, headers: \<json>, status\_code: \<int> }


{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}

{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="" %}

{% endswagger-response %}

{% swagger-response status="404: Not Found" description="Process not found" %}

{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="/files/lairs/{lair_id}/secrets" baseUrl="https://api.wayscript.com" summary="Set Lair Secret" %}
{% swagger-description %}
Set/update a secret key-value pair on a specific lair
{% endswagger-description %}

{% swagger-parameter in="path" name="lair_id" %}
UUID of the lair (most frequently from 

`/processes/{process_id}/detail`

)
{% endswagger-parameter %}

{% swagger-parameter in="body" name="data" type="JSON" %}
JSON payload containing the desired secret key-value pair to set/update



{ key: \<str>, value: \<str> }
{% endswagger-parameter %}

{% swagger-parameter in="header" name="authorization" %}
Authentication key for API access.

Set equal to:&#x20;

"Bearer " + `WAYSCRIPT_EXECUTION_USER_TOKEN`
{% endswagger-parameter %}

{% swagger-parameter in="header" name="content-type" %}
Defines expected return types from the HTTP request.

Set equal to: "application/json"
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}

{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="" %}

{% endswagger-response %}

{% swagger-response status="403: Forbidden" description="Requesting user cannot edit lair" %}

{% endswagger-response %}

{% swagger-response status="404: Not Found" description="Lair not found" %}

{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="/auth/refresh" baseUrl="https://api.wayscript.com" summary="Request New Authorization Token" %}
{% swagger-description %}
Update the authorization token for the requesting process
{% endswagger-description %}

{% swagger-parameter in="header" name="authorization" %}
Authentication key for API access.

Set equal to:&#x20;

"Bearer " + `WAYSCRIPT_EXECUTION_USER_TOKEN`
{% endswagger-parameter %}

{% swagger-parameter in="header" name="content-type" %}
efines expected return types from the HTTP request.

Set equal to: "application/json"
{% endswagger-parameter %}

{% swagger-parameter in="body" name="data" type="JSON" %}
JSON payload with the refresh token



{ refresh\_token: `WAYSCRIPT_EXECUTION_USER_REFRESH_TOKEN` }
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="JSON payload with tokens" %}
```
{
    refresh_token: <str>,
    access_token: <str>,
}
```
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="" %}

{% endswagger-response %}
{% endswagger %}

#### IMPORTANT NOTE ABOUT AUTHORIZATION

For all calls, it is possible that the process's authorization token can expire during runtime. If this occurs, subsequent API requests will return `401 - Unauthorized`. In order to obtain a new authorization token, follow these steps:

1. Obtain the refresh token from the `WAYSCRIPT_EXECUTION_USER_REFRESH_TOKEN` environment variable
2. Call the `Request New Authorization Token` API function to receive a new access token
3. Save the access token into the `WAYSCRIPT_EXECUTION_USER_TOKEN` environment variable

After these steps, retry any failed call and continue.
