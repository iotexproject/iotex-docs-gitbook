# Create wallet account

Let's begin with creating a new IoTeX wallet [account](../../basic-concepts/accounts.md): similarly to any blockchain wallet app where you can "_create a new wallet"_, this operation consists of [generating a random private key](../../basic-concepts/accounts-cryptography.md) and storing it in an encrypted file, protected by a password of your choice. It also allows you to set an _alias_ for the newly created account (we will use the alias "_dev-acc_" alias in the following sections). Once the alias is set, it can be used instead of the account address in any **ioctl** command:

Create and store an IoTeX account and assign the "dev-acc" alias to it with command below:

```
ioctl account createadd dev-acc
```

**ioctl** will ask you to provide a password that will be used to encrypt your newly created account. From now on when using **ioctl** commands you can refer to this account by using the alias **dev-acc** and the password of your choice.

{% hint style="danger" %}
It's highly recommended that you get used to immediately backup your account passwords in a safe place when you create a new account. Losing your password means losing access to the private key: when you interact with the IoTeX mainnet, **losing access to your private key means you will lose all the funds that you have sent to that account. Forever!**
{% endhint %}

{% hint style="info" %}
### Where does ioctl store accounts data?

All accounts created in **ioctl**, as well as all the aliases, and other settings are stored locally on your computer, in the following path:

`~/.config/ioctl`

You can make a copy of this folder to port your **ioctl** settings and accounts to multiple computers.
{% endhint %}

Check out this introductory video to ioctl accounts management

{% embed url="https://www.youtube.com/watch?v=Q-je019KGUA" %}
