# Communication Patterns

W3bStream supports the following two communication patterns with respect to data collection from IoT devices.

### Proxy Mode

In the proxy mode, data collected by IoT devices is first sent to a third-party service or platform. A client application then retrieves data from the third-party service and forwards it to W3bStream node(s). Such a communication pattern enables W3bStream to work with many existing Web 2.0-based IoT systems. However, Dapps should trust that third-party services do not manipulate data in this case. \
\
Note that the proxy mode is essentially based on the Web 2.0 trust model and **many existing blockchain oracle projects obtain IoT data in this way:**

![The Proxy Communication Mode in W3bStream](<../../.gitbook/assets/image (82).png>)

### Direct Mode

In the direct mode, data collected by IoT devices is **directly sent to W3bStream** node(s) without going through third-party services. Such a communication pattern aims for **new types of IoT devices** dedicatedly designed for empowering Web 3.0 applications. Dapps can base their trust on IoT devices themselves in this case: &#x20;

![The Direct Communication Mode in W3bStream](<../../.gitbook/assets/image (27).png>)
