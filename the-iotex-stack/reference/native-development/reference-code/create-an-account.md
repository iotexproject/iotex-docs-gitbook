# Create an account

{% tabs %}
{% tab title="Javscript" %}
```javascript
import Antenna from "iotex-antenna";

(async () => {
  const antenna = new Antenna("https://api.testnet.iotex.one");

  // create a new wallet which contains a public key, a private key, and an address.
  const wallet = antenna.iotx.accounts.create();

  // recover the whole wallet from a single private key
  const unlockedWallet = antenna.iotx.accounts.privateKeyToAccount(
    "69805ee813eadffa8fae53d0e6063e5fbf6a6e0fb9e90f6eaad7bc67f3d6c4bd"
  );

  // get the balance, nonce, number of actions, pendingNonce of the account
  const accountDetails = await antenna.iotx.getAccount({
    address: wallet.address
  });
})();package main
```


{% endtab %}

{% tab title="Go Lang" %}
```go
package main

import (
	"fmt"
	"log"

	"github.com/iotexproject/iotex-antenna-go/v2/account"

)

func main() {

	// create a new wallet which contains a public key, a private key, and an address.
	wallet, err := account.NewAccount();
	if err != nil {
		log.Fatal(err)
	}

	// recover the whole wallet from a single private key
	acc, err := account.HexStringToAccount("69805ee813eadffa8fae53d0e6063e5fbf6a6e0fb9e90f6eaad7bc67f3d6c4bd")
	if err != nil {
		log.Fatalf("create account error: %v", err)
	}
	fmt.Println(acc.Address)
}
```


{% endtab %}

{% tab title="Swift" %}
```swift
// create account from private key
let account = try Account(privateKey: "0806c458b262edd333a191e92f561aff338211ee3e18ab315a074a2d82aa343f")
let iotx = try IOTX(provider: "api.testnet.iotex.one:443", secure: true)

// query account meta
let response = try iotx.currentProvider().getAccount(Iotexapi_GetAccountRequest.with {
    $0.address = account.address
})
print(response)
```
{% endtab %}

{% tab title="Java" %}
```java
// create account from private key
Account account = IotexAccount.create(IotexAccountTest.TEST_PRIVATE);
IOTX iotx = new IOTX("api.testnet.iotex.one:80");
```
{% endtab %}
{% endtabs %}

