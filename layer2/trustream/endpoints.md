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

#### Query additional device data

```graphql
query getDevices {
  pebble_device (limit: 1, where: {owner: {_eq: "0x259c0a4251ee7CD3cbA0a437973443c9C7cd2D4f"} }) {
    id
    name
    owner
    address
    firmware
    avatar
    beep
    config
    configurable
    created_at
    data_channel
  }
}
```

Result:

```json
{
  "data": {
    "pebble_device": [
      {
        "id": "351358810263431",
        "name": "My Living Room",
        "owner": "0x259c0a4251ee7CD3cbA0a437973443c9C7cd2D4f",
        "address": "0x6ff4142596AaD08e95362EA9b4e03c50645E187a",
        "firmware": "Riverrock 1.0.8",
        "avatar": "https://storageapi.fleek.co/uu-z-team-bucket/b7a5acf3-c513-4279-944b-72f4dbf17e8c",
        "beep": 1000,
        "config": null,
        "configurable": false,
        "created_at": "2022-01-06T16:45:40.118+00:00",
        "data_channel": 8183
      }
    ]
  }
}
```

#### Query the most recent datapoint with valid GPS for a device

```graphql
query getDevices {
  pebble_device_record(limit: 1,  order_by: {timestamp: desc}, where: {imei: {_eq: "351358810263431"}, latitude: {_neq: "200.0000000"}}) {
      latitude, longitude, timestamp
    }
}
```

Result:

```graphql
{
  "data": {
    "pebble_device_record": [
      {
        "latitude": "45.4799999",
        "longitude": "9.1500000",
        "timestamp": 1641854726
      }
    ]
  }
}
```
