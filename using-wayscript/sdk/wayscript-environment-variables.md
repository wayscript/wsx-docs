---
description: >-
  WayScript populates several environment variables for use by the SDK or your
  own code.
---

# WayScript Environment Variables

| Name                                       | Value                                                |
| ------------------------------------------ | ---------------------------------------------------- |
| `WAYSCRIPT_EXECUTION_USER_TOKEN`           | The token used by SDK to authenticate with WayScript |
| `WAYSCRIPT_EXECUTION_USER_REFRESH_TOKEN`   | The token used to refresh the user token             |
| `WAYSCRIPT_EXECUTION_USER_APPLICATION_KEY` | The key used to retrieve user metadata               |
| `WAYSCRIPT_LAIR_URL`                       | The URL of the default lair endpoint                 |
| `WAYSCRIPT_ORIGIN`                         | The URL of the WayScript API server                  |
| `WS_PROCESS_ID`                            | The UUID of the process container                    |

Any Secret Variables you added will also be present in the environment.

You can also add variables with you lair's `.env` file.
