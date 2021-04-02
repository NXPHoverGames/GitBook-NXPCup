# Installation of NXP Gazebo

## Setting up SSH keys

{% hint style="info" %}
To use NXP Gazebo, you will need to have a GitHub account. The installation scripts require a GitHub account with an SSH key.
{% endhint %}

### Creating an SSH key

To create an SSH key, run the following in a terminal:

```text
$ ssh-keygen
```

Follow the prompt. We suggest just pressing enter until you reach the end. It will be easier if you just use the default path for the id\_rsa file and if you go without a passphrase \(though you're welcome to use one!\). You should get the output below. Note that the RSA key is not shown here for security reasons:

![](../.gitbook/assets/image%20%2834%29.png)

Next, you'll want to install `xclip`. This program will allow you to copy the contents of the id\_rsa.pub file to your clipboard so you can paste it into GitHub. To install `xclip`, run the following command:

```text
$ sudo apt install xclip
```

Once you've installed xclip, you need to copy the id\_rsa.pub file to your clipboard. To do so, run the following command:

```text

```

