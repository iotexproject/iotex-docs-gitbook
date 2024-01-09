---
description: A short introduction to ioctl, the IoTeX command line client
---

# Install ioctl cli

You can easily download and install the latest releases of **ioctl** by typing the following command in a terminal window:

{% tabs %}
{% tab title="Linux" %}
Using `curl`:

```bash
# install ioctl latest stable
curl https://raw.githubusercontent.com/iotexproject/iotex-core/master/install-cli.sh | sh
```

```bash
# install ioctl latest unstable build
curl https://raw.githubusercontent.com/iotexproject/iotex-core/master/install-cli.sh | sh -s "unstable"
```
{% endtab %}

{% tab title="macOS" %}
Using `brew`:

```bash
# install ioctl latest stable
brew install ioctl
```

```bash
# install ioctl latest unstable build
brew install ioctl-unstable
```

Using `curl`:

```bash
# install ioctl latest stable
curl https://raw.githubusercontent.com/iotexproject/iotex-core/master/install-cli.sh | sh
```

```bash
# install ioctl latest unstable build
curl https://raw.githubusercontent.com/iotexproject/iotex-core/master/install-cli.sh | sh -s "unstable"
```
{% endtab %}

{% tab title="Windows" %}
{% hint style="danger" %}
Currently, **ioctl** is not supported on Windows systems.
{% endhint %}
{% endtab %}
{% endtabs %}

Once ioctl is installed in your system, you must configure the endpoint of an IoTeX full node that acts as a Gateway to the network. Anyone can install an IoTeX full node and configure it as a gateway. Here we will use the public endpoints provided by the IoTex team for the mainnet and testnet networks:

```bash
# Point ioctl to the IoTeX Mainnet
ioctl config set endpoint api.mainnet.iotex.one:443

# Point ioctl to the IoTeX Testnet
ioctl config set endpoint api.testnet.iotex.one:443
```

{% content-ref url="../../reference/ioctl-cli-reference/" %}
[ioctl-cli-reference](../../reference/ioctl-cli-reference/)
{% endcontent-ref %}
