# Analytics Bookkeeping

**Bookkeeping** is a GraphQL web interface for rewards distribution, which collects voting status and calculates corresponding voters' reward for a given delegate, within a certain epoch range.

{% hint style="success" %}
While we still keep the Bookkeeping tool for analytics purposes, we recommend delegates use the [Hermes ](http://hermes.to/)system for auto-distribute voters' rewards.
{% endhint %}

## Get Voters' Rewards Given a Delegate Name

**Usage**: Please refer to the bookkeeping usage in the [Analytics Documentation](analytics-bookkeeping.md). To generate the rewards distribution:

#### 1. Access the Analytics website

{% embed url="https://analytics.iotexscan.io" caption="IoTeX Analytics website" %}

#### 2. Send the bookkeeping request

The following request will generate rewards amounts for a specific delegate with the following options:

**Delegate Name**: iotexlab \(must be your delegate unique name\)  
**Epochs range**: \[ 17000, 17099 \]   
**Epoch Bonus delegate fee**: 10%  
**Foundation Bonus delegate fee**: 10% 

Please notice that the bookkeeping Analytics request:

* **does not allow** to compute a share of the Block Rewards, therefore the delegate fee for the block rewards will always result in 100% \(no block rewards shared with voters9
* it either allows you to include the foundation bonus, or to exclude it. If you include it, then the shared amount of the foundation bonus **will always match** the same  amount chosen for the epoch rewards. In the example we share 90% of the epoch rewards \(i.e. delegate fee = 10%\) and include the foundation bonus, so also 90% of the foundation bonus will be computed in the share

```javascript
{
   delegate(delegateName:"iotexlab", startEpoch:17000, epochCount:100) {
    bookkeeping(percentage:90, includeFoundationBonus:false) {
      rewardDistribution(pagination:{ skip:100, first:100 }) {
        voterIotexAddress, amount
      }
    }
  }
}
```

You should also take into account pagination, considering that the server will never return more than 500 items per request, we do this in the rewardsDistriubution part of the request, where we set to get the results in pages of 100 items, and ask for the second "page" of results by "skipping" the fiskip 100 and asking for the next 100:

```javascript
rewardDistribution(pagination:{ skip:100, first:100 }) {
```

eventually, the request command will return a JSON object containing an array of `{ address, amount }` objects wher the `address` is the IoTeX native address of the voter, and `amount` is the total amount of rewards due to that user, for the specified epocs range, **accounting for all the buckets staked by that address.** 

```javascript
{
  "data": {
    "delegate": {
      "bookkeeping": {
        "rewardDistribution": [
          {
            "voterIotexAddress": "io1qqyamc23ar4vfrstkhgje7hu6t7pv6duw00h6v",
            "amount": "2701331503921172814"
          },
          {
            "voterIotexAddress": "io1e4uky58gst54cwdket8u8wns8j9ajeu9nn7lw8",
            "amount": "1368066446236365371"
          }
        ]
      }
    }
  }
}
```

## Send Out Voters' Rewards

The generated JSON can be used by to actually send out the voters' rewards with your own scripts in conjunction with the [ioctl client](../../reference/ioctl-cli-reference/), keeping in mind that the amount is represented in Rau, while ioctl expectes IOTX!

