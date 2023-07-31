# Chain Analytics API

_IoTeX Analytics_ is a service built upon IoTeX core API which extracts data from IoTeX blockchain and indexes them for applications to use via API calls or a GraphQL web interface.

The GraphQL endpoint is [https://analyser-api.iotex.io/graphql](https://analyser-api.iotex.io/graphql)

**Obtaining and API Key**

Access to the analytics API requires an API token, which you can obtain using the `ioctl` tool. **The service is entirely free**, and you can generate your API token using the following command:

```bash
ioctl jwt sign --with-arguments '{"exp":"1767024000","sub":"AnalyserAPI","scope":"Read"}' -s user
```

See the [ioctl reference documentation](../reference/ioctl-cli-reference/#install) on how to install the tool and hot to use it to [issue a JWT token](../reference/ioctl-cli-reference/jwt-tokens.md#use-ioctl-to-issue-jwt).

After generating the token, you can use it to access the API and perform the necessary operations.&#x20;

Keep the token secure and do not share it with unauthorized users to ensure the security of your API interactions.

#### Full API documentation

{% embed url="https://analyser-api.iotex.io/docs" %}

#### Playground

{% embed url="https://analyser-api.iotex.io/graphql" %}

### Included modules

<details>

<summary><a href="https://analyser-api.iotex.io/docs/#chain-service-api">Chain</a></summary>

The Chain service provides general information on the current status of the IoTeX blockchain and the IOTX token, like chain height, current epoch, total supply, total votes, etc...

[Go to this module documentation »](https://analyser-api.iotex.io/docs/#chain-service-api)

</details>

<details>

<summary><a href="https://analyser-api.iotex.io/docs/#delegate-service-api">Delegate</a></summary>

The Delegate service provides detailed data about the IoTeX delegates, block producers, staking deposits, mining rewards, and more.&#x20;

[Go to this module documentation » ](https://analyser-api.iotex.io/docs/#delegate-service-api)

</details>

<details>

<summary><a href="https://analyser-api.iotex.io/docs/#account-service-api">Account</a></summary>

The Account service provides all the information related to blockchain accounts, from balances to transactions to aliases for known addresses.

[Go to this module documentation » ](https://analyser-api.iotex.io/docs/#account-service-api)

</details>

<details>

<summary><a href="https://analyser-api.iotex.io/docs/#voting-service-api">Voting</a></summary>

The Voting service specializes in delegates ranking and votes.

[Go to this module documentation » ](https://analyser-api.iotex.io/docs/#voting-service-api)

</details>

<details>

<summary><a href="https://analyser-api.iotex.io/docs/#action-service-api">Action</a></summary>

The Action service allows any query to list transactions filtered by different criteria, like actions by date, address, type, etc...&#x20;

[Go to this module documentation »](https://analyser-api.iotex.io/docs/#action-service-api)

</details>

<details>

<summary><a href="https://analyser-api.iotex.io/docs/#xrc20-service-api">XRC20</a></summary>

The XRC20 service gives easy access to XRC20 fungible tokens data, like token holders and contract addresses.

[Go to this module documentation » ](https://analyser-api.iotex.io/docs/#xrc20-service-api)

</details>

<details>

<summary><a href="https://analyser-api.iotex.io/docs/#xrc721-service-api">XRC721</a></summary>

The XRC721 service gives easy access to XRC721 non-fungible tokens data, like token holders and contract addresses.

[Go to this module documentation » ](https://analyser-api.iotex.io/docs/#xrc721-service-api)

</details>

<details>

<summary><a href="https://analyser-api.iotex.io/docs/#hermes-service-api">Hermes</a></summary>

The Hermes service gives access to rewards distributed by the IoTeX official [Hermes system](https://hermes.to/).

[Go to this module documentation » ](https://analyser-api.iotex.io/docs/#hermes-service-api)

</details>
