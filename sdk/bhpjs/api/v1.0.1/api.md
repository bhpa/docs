# api

The `api` module is available as the plugin .

```js
const Bhp = require("./bhp-js");
var api = Bhp.api;

api.makeTransaction(config);
```

The `api` module rely on external services for the information required.

However, do note that these APIs rely on hosted nodes by 3rd party and thus use them at your own risk.

This module is structured slightly different from the rest of the modules. While the rest of the modules are flat in terms of hierachy, this module is composed of largely many other submodules. Only the core methods are found at the top level of the module.

---

## Core

They operate by taking in a configuration object which contains all the information necessary to request, construct and send a transaction. At the end, the same configuration object is returned.

## makeTransaction

```js
  All hexadecimal strings(like prevHash and assetId) cannot begin with "0x".
```

```js
const Bhp = require("./bhp-js");
var api = Bhp.api;

//You can access bhpnetapi(mainnet:https://api.bhpa.io/getUtxo?address=youaraddress, testnet:http://47.103.46.191/interface/getUtxo?address=youraddress) to get UTXO of the specified address.
const input = {     
    //utxo txid
    prevHash: "6a9d19b9a960d809759c0823c19f32245b38ea18f6783c595f8567010f14b188",
    //utxo tx n
    prevIndex: 0,
    //utxo asset
    assetId: "13f76fabfe19f3ec7fd54d63179a156bafc44afc53a7f07a7a15f6724c0aa854",
    //utxo value
    value: 0.1,
    //utxo address
    scriptHash: "AL2Eo2B1bWRSjizgRsFWoUShAYvv4NMiFq"
};

var inputs = [];
inputs.push(input);

var config = {
    //UTXO Input Address
    inputs: inputs,
    //transfer asset id
    assetId: "13f76fabfe19f3ec7fd54d63179a156bafc44afc53a7f07a7a15f6724c0aa854",
    //transfer to address
    toAddress: "AL2Eo2B1bWRSjizgRsFWoUShAYvv4NMiFq",
    //transfer value
    value: 0.1,
    //transfer change address
    changeAddress: "AL2Eo2B1bWRSjizgRsFWoUShAYvv4NMiFq",
    //if transferred to BHP or GAS, bhpFeeAddress is invalid. When IS_BHP_FEE is configured as true, the address is bhp fee change dress (no token fee is currently charged).
    bhpFeeAddress: "AL2Eo2B1bWRSjizgRsFWoUShAYvv4NMiFq",
    //private key of input address
    priKeys: ["910183411298293648578c14f4d34bf8ba5ff03e28a026b3eb0a744f589b05d3"]
}

api.makeTransaction(config)
    .then(config => {
    console.log("\n\n--- Response ---");
    console.log(config);
})
    .catch(config => {
    console.log(config);
});
```
