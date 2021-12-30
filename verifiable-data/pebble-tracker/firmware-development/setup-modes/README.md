# Setup modes

When developing an application for Pebble, you can configure your environment in two modes, namely _developer_ and _production_ modes, depending on the choice of the backend architecture.

### Developer Mode <a href="#developer-mode" id="developer-mode"></a>

The developer mode facilitates development of Pebble applications on a single machine using the _dockerized_ applications listed below. In such mode, MQTT communications between a Pebble and the hmq are **not secure**:

* [hmq](https://github.com/fhmq/hmq): A free and high performance MQTT broker
* [minIO](https://min.io): A Kubernetes native, high performance object storage
* [ThingsBoard](https://thingsboard.io): An open-source IoT platform

![](<../../../../.gitbook/assets/image (37).png>)

See [Setup in Developer Mode](development-mode/) for instructions on how to configure the backend service

### Production Mode <a href="#production-mode" id="production-mode"></a>

In the production mode, the backend is built using the following AWS services and open-source software.

* [AWS IoT Core](https://aws.amazon.com/iot-core/): A managed cloud service that lets connected devices easily and securely interact with cloud applications and other devices
* [AWS S3](https://aws.amazon.com/s3/): An object storage service that offers industry-leading scalability, data availability, security, and performance
* [ThingsBoard](https://thingsboard.io): An open-source IoT platform

![](<../../../../.gitbook/assets/image (31).png>)

The production mode enables a developer to connect and manage a large number of Pebble devices. In such mode, MQTT communications between Pebble devices and AWS IoT Core are protected by the Transport Layer Security (TLS) protocol.

See [Setup in Production Mode](production-mode/) for instructions on how to configure AWS IoT to connect with Pebble devices.
