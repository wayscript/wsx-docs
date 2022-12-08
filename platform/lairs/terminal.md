# Terminal

Opening a Lair creates a new Unix terminal session connected to the remote instance of your Lair’s file system. You can use standard `bash` commands to navigate the file system or execute processes.

### Using your Lair’s terminal

The terminal is located on the bottom of your Lair editor. On initialization, your terminal’s current directory will be your Lair’s root directory.

{% hint style="info" %}
Your terminal is connected to your Lair’s remote file system, not the files on your local machine. When using the WayScript desktop app, if your terminal does not reflect file changes made locally, you must first “Push” your file system. See [file-system.md](file-system.md "mention") for more details on file sync.
{% endhint %}

![](https://codahosted.io/docs/2kDMDaZ6QP/blobs/bl-8PVo0YkeT7/297cbb366a84adc9875f31a5a6cd1b95c9cdefc45ee26f8546385da7fdcb7274734063f277db07161bfc316ad2719cc70ad55fbe73dc09edf421bdf6882b7d2cde2f0430e4f0afa0e7b9132c9b19bb8ba19a5b755cdff2a0bb775f9c479034968b555f06)

You can use your Lair’s terminal is to execute processes, create files and directories, and much more. For example, you can run a Python file in your Lair directory.

```python
# my-file.py
print('Hello world!')
```

```bash
# Terminal connected to my-lair-a
~/my-lair-a $ python my-file.py 
Hello world!
```

{% hint style="danger" %}
Exiting the Lair editor will terminate the terminal session and any processes that have been executed synchronously or asynchronously through the terminal.
{% endhint %}

### Terminal considerations

* Pressing ▶ on a code file will enter the respective default run command, e.g. `python my-file.py`, into the Lair terminal.
* Each Lair terminal can only access the files within the current Lair directory. See [File system](file-system.md) for more details.
* Terminal sessions use independent containerized environments, so changes made to the environment will not persist across sessions or within your Lair environment. For example, installed Python libraries (through `pip`) will be discarded on session close. However, you can use standard `requirements.txt` or `package.json` dependency files to load packages on session start; see [Hosted environments](deployments.md) for more details.
* The Lair terminal currently does not render terminal programs or abstractions such as `vim` . Please use these at your own risk.

### Troubleshooting Reported Issues

Tensorflow:

{% hint style="info" %}
If trying to install Tensorflow, use the following install command: `pip install tensorflow --no-cache-dir`
{% endhint %}

