# Example: send response to http trigger

### Python

```python
# Returns json response to http trigger
from wayscript.triggers import http_trigger

payload = {"hello": "world"}
headers = {"content-type": "application/json"}
status_code = 200

http_trigger.send_response(data=payload, headers=headers, status_code=status_code)
```

### JavaScript

```javascript
// Returns json response to http trigger
const wayscript = require("wayscript");

let data = {"hello": "world"};
let headers = {"content-type": "application/json"};
let status_code = 200;

wayscript.http_trigger.sendResponse(data, headers, status_code);
```
