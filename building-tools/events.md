# Events

Events are data payloads that are passed to your processes when your Lair’s triggers are invoked. For example, when making a request to a Lair configured with a `http` trigger, your event would contain any query parameters or json data that is included in the request.

### Access**ing** events within your Lair

Events can be accessed using WayScript X’s `context` package. Simply import the package and call `get_event()` to output your event data \(see [SDK](sdk.md) for more details\). The event will be returned as a json dictionary object.

**Import** **context** **package and get event**

```python
# my-file-a.py

import wayscript.context as context
test_event = context.get_event()
```

### Using test events

Your event payload can be replaced by sample event data during manual invocation of your triggers so you can test processes without using dummy requests or switching between services.

#### **Creating test event** **json** **file**

You can pass any valid `json` file to your trigger to use as a test event. Here is a sample test event `json` file to use with a `http` trigger.

```text
# http_test.json

{
  "raw_data": "",
  "request": {
    "query_params": {},
    "json_data": {},
    "metadata": {
      "accept_encodings": "",
      "accept_languages": "",
      "accept_mimetypes": "",
      "base_url": "",
      "content_length": 0,
      "content_type": "",
      "content_md5": "",
      "data": "",
      "date": "2021-09-09T16:21:39.084628+00:00",
      "form": "{}",
      "full_path": "",
      "host": "",
      "host_url": "",
      "if_modified_since": "2021-09-09T16:21:39.084651+00:00",
      "if_unmodified_since": "2021-09-09T16:21:39.084657+00:00",
      "is_json": false,
      "is_secure": false,
      "json": "{}",
      "mimetype": "",
      "mimetype_params": "{}",
      "method": "",
      "path": "",
      "query_string": "",
      "remote_addr": "",
      "remote_user": "",
      "referrer": "",
      "scheme": "",
      "url": "",
      "url_root": "",
      "user_agent": ""
    }
  }
}
```

#### **Attaching test events to triggers**

Select your `json` file in the trigger configuration to use the test event. You must “Push” your file system to pass the configuration to your Lair’s remote instance.

![](https://codahosted.io/docs/2kDMDaZ6QP/blobs/bl-ZvkAGMtwpC/654a4729427fa7b799e060171153c156f4a780bd5bd1d78c6bea20bfeb67e513f8f71615a5a49aa22c59c714f14a281a253c50a0ec74c739d5cd080b5a53a910368b45e6d1b24539900cb506369a88615d7c456dbc8168751bda5e60fc66d73468975979)

#### **Passing test event data to your processes**

Test events are only passed to your process on manual invocations of your Lair’s triggers. Please see [Triggers](triggers.md) for more details.  

