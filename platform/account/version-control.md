# Version Control

To most effectively use Version Control with WayScript, you must set up your SSH credentials.

## Setup

#### **Generate an ssh key pair on your local computer.**

Do this step on your local terminal or command prompt.

[Follow this guide](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#generating-a-new-ssh-key) on GitHub for help generating an SSH key.

### Copy the SSH private key

This command will copy your private key file to your clipboard, you can paste it to the private key field Note: your private key file name default is id\_ed25519.

**Mac:**

```
pbcopy < ~/.ssh/<YOUR_PRIVATE_KEY_FILE_NAME> 
```

**Windows:**

```
clip < ~/.ssh/<YOUR_PRIVATE_KEY_FILE_NAME> 
```

{% hint style="info" %}
If `clip` or `pbcopy` isn't working, you can locate the hidden `.ssh` folder, open the file in your favorite text editor, and copy it to your clipboard.
{% endhint %}

### Enter your credentials in WayScript

Head to Settings > Version Control

Paste your Git SSH key, passphrase, email, and username.

![](<../../.gitbook/assets/Screen Shot 2022-09-20 at 1.17.33 PM.png>)

### Copy your ssh public key and paste it to your GitHub account

[Head over to GitHub](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/testing-your-ssh-connection) and make sure your SSH key is setup there.

## Using Version Control

Once your credentials are setup in WayScript, you can use GitHub in the terminal just like you would on your local computer.

With the Desktop App, you can use WayScript in conjunction with GitHub Desktop or whatever version control system you prefer.
