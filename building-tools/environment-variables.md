# Environment variables

Your Lair can reference environment variables on process execution. For additional security, you can add both an `.env` or `.secrets` file. Your `.secrets` file should be used for any sensitive data, such as private keys, as it is end-to-end encrypted.

### Example .env & .secrets files

```yaml
# my-lair-a > .env
USER=nihar
VERSION=1.0.3

# my-lair-a > .secrets (example only, data is end-to-end encrypted)
API_KEY=hfy92kadHgkk29fahjsu3j922v9sjwaucahf
```

### Creating environment variables

First, create an `.env` or `.secrets` file in your Lair by selecting the \(+\) icon or manually initializing an empty file.

![](https://codahosted.io/docs/2kDMDaZ6QP/blobs/bl-Iqkx-tphjD/3d584a55f32dbc8c4e8cf462e3eb9867bbcaf47440586f29d25f94abb1d90be28f4433566d59fc5bfeef80fb761d4e93785f99ec6a64bd561d70e8c2785ae52f342dcf4729de3a496500f8f7ee8d21e20f6ee3321ca9844abc41275391641b8d1fff3ebe)

Open the `.env` or `.secrets` file from your Lair file system. Select “+ Add New Env/Secret” and enter a key and value for your environment variable.

{% hint style="danger" %}
To maintain strict security practices, environment variables added to the .secrets file cannot be modified after creation. Additionally, creating new variables within your .secrets file will require a network connection to avoid local persistence of any unencrypted data.
{% endhint %}

![](https://codahosted.io/docs/2kDMDaZ6QP/blobs/bl-y6VBct0x43/8df62ca809cc4d4d26a8a856c73b01cd85ea91a043dc7ac093aa6a8ba6e44ff43383a44b2f93ee58a6f0044e34a2bd5453accaa946ddacf696adfc35fb7a828f2201f863a71b42fd5d87f6701749822cdd4b30c762c01f7cab5686667c4e61356263d8fa)

### Accessing environment variables

Environment variables are injected into your Lair’s environment during process execution, and can be accessed using standard os libraries.

#### **Python example**

```python
### main.py
import os

# Get environment variable values
USER = os.getenv('USER')
KEY = os.environ.get('API_KEY')

# Getting non-existent keys
FOO = os.getenv('FOO') # None
BAR = os.environ.get('BAR') # None
BAZ = os.environ['BAZ'] # KeyError: key does not exist.
```

#### Security considerations

Your `.secrets` file is end-to-end encrypted and we employ the leading data practices to keep your sensitive data secure. Please see [Security](https://coda.io/d/WayScript-X-Docs_d2kDMDaZ6QP/Security_suGvs) for more details.

