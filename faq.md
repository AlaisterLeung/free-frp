# FAQ

## Is my data secure?

Yes. I **DON'T** collect the data sent through the proxy, but the IP address and the port number used are logged by FRPS.

## Is this service always free?

Yes. This service won't ever cost you money.

## Why does my proxy fail to start?

This might be caused by the following reasons:

* the port number has already been used \(see [below](faq.md#why-my-port-number-has-been-used-even-your-website-said-it-was-available)\)
* something wrong with your frpc.ini file \(check the terminal output\)
* the service is not running or listening to the 'local\_port'
* the proxy server is offline or under maintenance \(if [this page](https://free-frp-api.alaister.net:42881/) is offline or not showing a port number, it's likely the server is also offline\)
* the 'server\_addr' or 'server\_port' is incorrect \(double-check the configuration [here](getting-started.md#configuration)\)
* something wrong with your service or local server

## Why the port number shown on [this page](https://free-frp-api.alaister.net:42881/) is not working?

To prevent users from spamming the website to generate port numbers, the generated port is **cached for 2 minutes**. When more than one users generate port numbers at the same time, as they are the same, they may use your port number. If this happens, please wait for a few minutes and try again.

## Still have questions?

Please send me an email at [contact@alaister.net](mailto:contact@alaister.net). I will reply to you as soon as possible.

