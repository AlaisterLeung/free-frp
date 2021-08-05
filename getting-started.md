# Getting Started

## Installation

Download the latest release from [Github](https://github.com/fatedier/frp/releases/latest) and extract the file.

## Configuration

Modify the frpc.ini file and change the **server\_addr** to **172.245.34.140** and the **server\_port** to **5678** as follows:

{% code title="frpc.ini" %}
```text
[common]
server_addr = 172.245.34.140
server_port = 5678

# Below is optional
protocol = kcp

```
{% endcode %}

{% hint style="info" %}
We also support KCP protocol. You may learn more about KCP [here](https://github.com/fatedier/frp#support-kcp-protocol).
{% endhint %}

### Supported Ports and Protocols

You may use any port numbers **between 40000 and 50000**. Each user can use up to **10 ports**. We support **TCP**/**STCP** \(secure TCP\) and **HTTP\(S\)** protocols. Currently, TCPMux, UDP/SUDP, and P2P are not yet supported.

## More Examples

[https://github.com/fatedier/frp\#example-usage](https://github.com/fatedier/frp#example-usage)

## Starting the FRP Client

Run the following command:

```bash
$ ./frpc -c ./frpc.ini
```

To stop it, press 'Ctrl + C'.

### Starting in Background

You may want to keep the proxy alive even you close the terminal. To do so, run:

```bash
$ nohup ./frpc -c ./frpc.ini &
```

{% hint style="info" %}
Don't forget about the '&' at the end!
{% endhint %}

Now, you should be able to access your local server through our IP address **172.245.34.140** and the **remote\_port** number you set in your frpc.ini file.

