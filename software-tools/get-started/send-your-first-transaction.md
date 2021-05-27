# Send your first transaction

The IoTeX **Transfer** action allows sending `IOTX` tokens from one IoTeX account \(the _sender_ account\) to another IoTeX account \(the _recipient_ account\).

Below is the command to send **10 IOTX** from our **dev-acc** account to the IoTeX account with the address **io1mflp9m6hcgm2qcghchsdqj3z3eccrnekx9p0ms**

```text
ioctl action transfer io1mflp9m6hcgm2qcghchsdqj3z3eccrnekx9p0ms 10 -s dev-acc
```

ioctl will ask for the password of our _dev-acc_ account, then it will send the action to the running gateway node and provide the hash of the action.

