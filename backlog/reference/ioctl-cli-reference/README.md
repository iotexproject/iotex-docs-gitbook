# ioctl cli - Reference

## Install

Install Latest Release Build

```bash
curl https://raw.githubusercontent.com/iotexproject/iotex-core/master/install-cli.sh | sh
```

install Latest Unstable Build

```bash
curl https://raw.githubusercontent.com/iotexproject/iotex-core/master/install-cli.sh | sh -s "unstable"
```

#### Show Version

`Usage: ioctl version`

```
→  ioctl version
Client:
packageVersion:"v0.5.0" packageCommitID:"a4308fc82bea22cfaa45addef679a09f41f3a998" gitStatus:"clean" goVersion:"go version go1.11.5 darwin/amd64" buildTime:"2019-04-20-PDT/18:04:37"

Server: api.iotex.one:443
packageVersion:"v0.5.0" packageCommitID:"a4308fc82bea22cfaa45addef679a09f41f3a998" gitStatus:"clean" goVersion:"go version go1.11.5 linux/amd64" buildTime:"2019-04-21-UTC/01:04:11"
```

## Update

`Usage: ioctl update [-t version-type]`

Update ioctl Release Build:

```
➜  ioctl update
Downloading the latest stable version ...
Password:
ioctl is up-to-date now.
```

update ioctl Latest/Unstable Build:

```
➜  ioctl update -t unstable
Downloading the latest unstable version ...
Password:
ioctl is up-to-date now.
```

## Configure&#x20;

`Variables: [endpoint, wallet, explorer, defaultacc, language, nsv2height]`\
`Explorers: [iotexscan (default), iotxplorer, custom]`

#### Set Config

`Usage: ioctl config set VARIABLE VALUE`

{% tabs %}
{% tab title="Mainnet" %}
```bash
➜  ioctl config set endpoint api.mainnet.iotex.one:443
endpoint is set to api.iotex.one:443

# If the endpoint does not implement SSL, use:
# ioctl config set endpoint api.mainnet.iotex.one:80 --insecure
```
{% endtab %}

{% tab title="Testnet" %}
```bash
➜  ioctl config set endpoint api.testnet.iotex.one:443
endpoint is set to api.iotex.one:443

# If the endpoint does not implement SSL, use:
# ioctl config set endpoint api.testnet.iotex.one:80 --insecure
```
{% endtab %}
{% endtabs %}

#### Get Config

`Usage: ioctl config get VARIABLE | all`

```
➜  ioctl config get wallet
/Users/IoTeX/.config/ioctl/default
```

#### Reset Config

`Usage: ioctl config reset`

```
➜  ioctl config reset
Config reset to default values
```
