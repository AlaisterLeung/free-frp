# Getting Started

## Installation

Download the latest release from [Github](https://github.com/fatedier/frp/releases/latest) and extract the file.

```bash
$ wget https://github.com/fatedier/frp/releases/download/v0.35.1/frp_0.35.1_linux_amd64.tar.gz -O frp.tar.gz
$ tar -xvzf frp.tar.gz
```

{% hint style="info" %}
You may need to change the version number above if it is outdated or change the architecture depends on your local server.
{% endhint %}

## Configuration

Then, modify the file 'frpc.ini' inside the extracted folder.

```bash
$ cd frp_0.35.1_linux_amd64
$ chmod 755 frpc
$ nano frpc.ini
```

In the following example, we will expose the SSH server to the Internet so that it can be accessed with the 'server\_addr' 192.245.62.27 and the 'remote\_port' \(e.g. 34567\). Of course, you can expose any TCP services.

{% hint style="info" %}
Currently, only TCP proxies are tested. You may use other proxy types provided by FRP, but they aren't guaranteed to work with my proxy server.
{% endhint %}

{% code title="frpc.ini" %}
```text
# Don't change these configurations
[common]
server_addr = 198.245.62.27
server_port = 46375

# Change the configurations below
[ssh]
type = tcp
local_ip = 127.0.0.1
local_port = 22
remote_port = 34567
```
{% endcode %}

{% hint style="danger" %}
You should change the 'remote\_port' and it should be between 30000 and 50000. Click [here](https://free-frp-api.alaister.net:42881/) to generate a port number, then change the 'remote\_port'. If FRPC failed to start the proxy, the port number may be taken. Learn more [here](faq.md#why-does-my-proxy-fail-to-start).
{% endhint %}

{% hint style="warning" %}
Please don't mix up 'remote\_port' with 'server\_port'. You should **NEVER** change the 'server\_port' and 'server\_addr' unless you know what you are doing.
{% endhint %}

{% hint style="info" %}
The section name '\[ssh\]' can be changed to anything you want. You may also add up to five sections \(to prevent abuse of this free service\).
{% endhint %}

## Starting the Reverse Proxy

Make sure you are still inside the folder. Now run the following command.

```bash
$ ./frpc -c ./frpc.ini
```

To stop it, press 'Ctrl + C'.

### Starting in Background

You may want to keep the connection alive even you close the terminal. To do so, run:

```bash
$ nohup ./frpc -c ./frpc.ini &
```

{% hint style="info" %}
Don't forget about the '&' at the end!
{% endhint %}

Now, you should be able to access your local server with our IP address and the port number you set in the 'frpc.ini' file. In the example on this page, they are '198.245.62.27:34567'.

