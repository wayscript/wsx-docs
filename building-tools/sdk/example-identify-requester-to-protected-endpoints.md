# Example: identify requester to protected endpoints

### General steps

1. Get `application_key` from request Authorization header or from session cookie
2. Pass `application_key` to  `context.get_user_by_application_key` method

{% tabs %}
{% tab title="Server-side (Flask)" %}
```python
from flask import Flask, request
from wayscript import context

app = Flask(__name__)

@app.route('/')
def get_user_details():
  # Parse application key from bearer token in request header 
  application_key = request.headers.get('Authorization')[7:]
  # Query user object from application key
  user = context.get_user_by_application_key(application_key)
  return user

if __name__ == '__main__':
  app.run()
```
{% endtab %}

{% tab title="Server-side (Node)" %}
```javascript
const express = require('express');
const wayscript = require("wayscript");

const app = express();
const port = 3000;

app.get('/', (req, res) => {
    // Parse application key from bearer token in request header
    const applicationKey = req.headers.authorization.substr(7);
    // Query user object from application key
    let user = wayscript.context.getUserByApplicationKey(applicationKey);
    res.send(user);
});

app.listen(port, () => console.log(`Hello world app listening on port ${port}!`));
```
{% endtab %}

{% tab title="Client-side (React)" %}
WayScript also sets the `application_key` as the value for a cookie with name `ws_workspace_application_key_<workspace_id>` for client-side processing. You can determine your `workspace_id` by inspecting cookies for a protected endpoint.&#x20;

```javascript
import React from 'react';
import Cookies from 'js-cookie';
const wayscript = require("wayscript");

class App extends React.Component {
    // Retrieve application key from session cookie
    const applicationKey = Cookies.get('ws_workspace_application_key_<workspace_id>');
    // Query user object from application key
    const user = wayscript.context.getUserByApplicationKey(state.applicationKey);  
}  
```
{% endtab %}
{% endtabs %}

#### Sample user metadata

```json
{
  "avatar": "https://lh3.googleusercontent.com/a-/AOh14Gj_lywgCvZF1oDt0Z0iW3n01MtyyYA0YTRYxlxq=s96-c",
  "created_date": "2022-01-27T19:31:11.719832",
  "email": "support@wayscript.com",
  "first_name": "Barry",
  "last_name": "Allen",
  "id": "186f48b6-57c5-4dd4-9422-f7d503ad5b9c",
  "groups": [
    {
      "id": "195d0f07-1b9f-4c7e-ae48-227dcf63556a",
      "name": "product_team",
      "owner_id": "186f48b6-57c5-4dd4-9422-f7d503ad5b9c",
      "system_managed": false,
      "workspace_id": "40dea282-d83b-48d1-9427-f01171da45f6"
    }
  ],
}
```
