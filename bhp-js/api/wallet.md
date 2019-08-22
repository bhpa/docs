# Wallet

The `wallet` module is exposed as:

```js
const Bhp = require("./bhp-js");
var bhpDefault = Bhp.default;
var wallet = Bhp.wallet;

const acct = new Bhp.wallet.Account(privateKey);
const account = bhpDefault.create.account(privateKey);
const alternative = new wallet.Account(privateKey);

Bhp.wallet.isAddress(address);
bhpDefault.is.address(address);
wallet.isAddress(address);
```

The `wallet` module contains methods for manipulating keys, creating signatures and verifying keys.

---

## Classes

### Account

The `Account` class is used to store and transform keys to its various formats. It can be instantiated with any key format and is smart enough to recognise the format and store it appropriately.

```js
const a = new Bhp.wallet.Account();
const b = new Bhp.wallet.Account(privateKey);
const c = new Bhp.wallet.Account(address);
const d = new Bhp.wallet.Account(publicKey);
const e = new Bhp.wallet.Account(wif);
```

The class enables us to easily retrieve keys in any derivable format without needing to remember any methods. However, we can only retrieve formats that can be derived from our input. For example, we cannot retrieve any formats other than address and scripthash from `c` because we instantiated it with an address, we can only retrieve address, scripthash and publicKey from `d` because we instantiated it with an publicKey. However, we can get any format from `a` , `b` and  `e` because it was instantiated with a private key, which is the lowest level key available.

```js
console.log(c.publicKey); // throws an error
console.log(d.publicKey); // prints the public key
console.log(b.address); // prints the address
```

The order of the keys are:

0. encrypted (BRC2)
1. privateKey / WIF
1. publicKey
1. scriptHash
1. address

When you instantiate an `Account` with a key, you can retrieve any format that is below it in the list. For example, if we instantiate with a public key, we can get the public key, scriptHash and address but not the private key.

The Account class can be instantiated from encrypted key, private key, public key, address or ScriptHash.

The `encryptedKey` is special as it is the lowest level key but requires the user to unlock it first before we can derive anything from it. This can be done through the `decrypt` method.

```js
const c = new wallet.Account(
  "6PYQ4eQZsboaigc45NWzvdfzezPjZ77zhtVnZrjdaiZ9QQqnoAPvghMJzA"
);
console.log(c.encrypted); // encrypted key
console.log(c.address); // throws error
c.decrypt("1").then(() => console.log(c.address)); // AL2Eo2B1bWRSjizgRsFWoUShAYvv4NMiFq
```

You can encrypt the key by using the `encrypt` method. This is necessary if you want to export this key to a JSON file.

```ts
c.encrypt("new password").then(() => c.export());
```

This action will encrypt the private key with the provided password and replace any old BRC2 key.

### Wallet

The `Wallet` class implements the BRC-6 convention which is a standard way set by BHP council on how to export keys in a JSON file. By doing this, we can move keys across different software providers without worry.

The `Wallet` class is essentially a collection of encrypted keys as well as the parameters used to encrypt them.

```js
const Bhp = require("./bhp-js");
var bhpDefault = Bhp.default;
var wallet = Bhp.wallet;

const a = new wallet.Account(
  "910183411298293648578c14f4d34bf8ba5ff03e28a026b3eb0a744f589b05d3"
);
const b = new wallet.Account(
  "6PYQ4eQZsboaigc45NWzvdfzezPjZ77zhtVnZrjdaiZ9QQqnoAPvghMJzA"
);

// We create a wallet with name 'myWallet'. This is optional. The constructor is fine with no arguments.
const w1 = bhpDefault.create.wallet({ name: "myWallet" });

// We generate a new Account and add it to the wallet
w1.addAccount();
// We add Account a to the wallet.
w1.addAccount(a);
// We add Account b to the wallet.
// Note that Account b is unencrypted and we can add this Account.
// The wallet will only error when trying to export an unencrypted key but does not prevent you from adding it.
w1.addAccount(b);
```

## Methods

### Core

The core methods available are methods to convert key formats and generate new private keys.

Do note that the methods available is not the full set but only the minimum required. Generally, there is a method to retrieve the lower key from the higher key. For example, `getPublicKeyFromPrivateKey` exists but not `getAddressFromPrivatKey` or `getPrivateKeyFromPublicKey`. For conversions across all formats, you are encouraged to use the `Account` class.

```js
const privateKey1 = bhpDefault.create.privateKey();
const privateKey2 = wallet.generatePrivateKey();
const privateKey3 = wallet.getPrivateKeyFromWIF(wif);
const publicKey = wallet.getPublicKeyFromPrivateKey(privateKey);
const wif = wallet.getWIFFromPrivateKey(privateKey);
const scriptHash = wallet.getScriptHashFromPublicKey(publicKey);
const address = wallet.getAddressFromScriptHash(scriptHash);
```

There are no checks in place for this set of methods to ensure the inputs are proper. Errors may be thrown when conversion fails for certain methods.

### Components

These are methods used to convert JS objects into their respective `bhp-js` implementation.

These methods are exposed for completeness but you are encouraged to use the constructors of the main objects `Balance` and `Claims` instead of manually recreating your own objects.

### BRC2

The BRC2 standard describes the procedure to encrypt or decrypt a private key. The encryption method accepts either a WIF or HEX private key. However, the decryption method will always return a WIF for consistency.

Do note that the encryption/decryption takes a long time and might not work very nicely in browsers.

```js
const privateKey1 = bhpDefault.create.privateKey();
const privateKey2 = wallet.generatePrivateKey();
const WIF = new wallet.Account(privateKey).WIF
const brc2Key = wallet.encrypt(WIF, 'myPassword')
```

### Verify

Verification methods for the various key formats are available::

```js
bhpDefault.is.address(addrStr);
bhpDefault.is.privateKey(keyStr);
bhpDefault.is.encryptedKey(keyStr);
bhpDefault.is.publicKey(publicKeyStr);
bhpDefault.is.wif(wifStr);
bhpDefault.is.scriptHash(scriptHashStr);

wallet.isAddress(addrStr);
wallet.isPrivateKey(keyStr);
wallet.isBRC2(keyStr);
wallet.isPublicKey(publicKeyStr);
wallet.isWIF(wifStr);
wallet.isScriptHash(scriptHashStr);
```

These methods will return a boolean regarding the key format. No errors will be thrown.
