# Require

As bhp-js package uses ES6 module conventions, `require` will need to specify which module do they want exactly:

```js
var Bhp = require("./bhp-js")

// Semantic Style by using default import
var bhpDefault = Bhp.default

// Named imports are available too
var wallet = Bhp.wallet
var tx = Bhp.tx

const account = new wallet.Account(privateKey)
```

# Web

bhp-js is also packaged for the web. You can add it through a script tag

```html
  <script src="./browser.js"></script>
```

The library will be available as a global variable `Bhp`. Similar to `require` style, you will have the semantic style under `default` and the rest of the named modules exposed at the same level.
