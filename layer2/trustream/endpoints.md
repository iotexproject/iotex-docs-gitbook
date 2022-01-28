# Endpoints

### Mainnet

Use the GraphQL endpoint below to query the TruStream network mainnet:

[https://pebble.iotex.me/v1/graphql ](https://pebble.iotex.me/v1/graphql)

### Testnet

Use the GraphQL endpoint below to query the TruStream testnet:

[ https://dev.iotex.io/v1/graphql](https://dev.iotex.io/v1/graphql)

### Example queries

You can use a public GraphQL endpoint like [https://tray.io/docs/api/sandbox](https://tray.io/docs/api/sandbox) to test some queries:

#### List devices owned by a specific account

```graphql
query getDevices {
      pebble_device (limit: 10, where: {owner: {_eq: "0x259c0a4251ee7CD3cbA0a437973443c9C7cd2D4f"} }) {
        id
        owner
      }
    }
```

**Result**:

```json
{
  "data": {
    "pebble_device": [
      {
        "id": "351358810263431",
        "owner": "0x259c0a4251ee7CD3cbA0a437973443c9C7cd2D4f"
      },
      {
        "id": "351358813374789",
        "owner": "0x259c0a4251ee7CD3cbA0a437973443c9C7cd2D4f"
      }
    ]
  }
}
```

