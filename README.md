# Proxy Test 1: Sharing Axios Parameters with Token Exchange

## Setup
1. Clone this branch: `proxy-test-share-axios-config`.
2. Install dependencies: `npm install`
3. Install `tunnel`: `npm install tunnel`
4. Build the code: `npm run build`

## Testing

Below is a code snippet demonstrating usage of the fix to try:

```js
const tunnel = require('tunnel');
const DiscoveryV1 = require('./node-sdk/discovery/v1'); // path to wherever the cloned repo is

const discovery = new DiscoveryV1({
  iam_apikey: '<my apikey>',
  version: '<my version date>',
  httpsAgent: tunnel.httpsOverHttp({ // CREATE A CUSTOM TUNNEL TO PASS TO AXIOS
    proxy: {
      host: '<my proxy host>',
      port: '<my proxy port>',
    },
  }),
  proxy: false, // DISABLE AXIOS PROXY
});

discovery.listEnvironments()
  .then(res => {
    console.log(res);
  })
  .catch(err => {
    console.log(err);
  });
```

_Note: This new behavior is only available for Discovery and Assistant (v1 and v2)._
