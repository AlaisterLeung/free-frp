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

{% code title="frpc.ini" %}
```text
# Don't change these values
[common]
server_addr = 198.245.62.27
server_port = 46375

# Change the values below
[ssh]
type = tcp
local_ip = 127.0.0.1
local_port = 22
remote_port = 34567
```
{% endcode %}

{% hint style="warning" %}
Currently, only TCP connections are tested and stable. You may use other types, but I won't guarantee they will work.
{% endhint %}

{% hint style="danger" %}
The remote\_port must be between 30000 and 50000. If FRPC failed to start the proxy, the port number may be already used. Learn more [here](faq.md).
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

Now, you should be able to connect to your local server with our IP address and the port number you set in the frpc.ini file. In the example on this page, they are '198.245.62.27:34567'.

