# Proxy Test 2: Tunneling Option

## Setup
1. Clone the branch `add-tunneling-option`.
2. Install dependencies: `npm install`
3. Build the code: `npm run build`

## Testing

Below is a code snippet demonstrating usage of the fix to try:

```js
const DiscoveryV1 = require('./node-sdk/discovery/v1'); // path to wherever the cloned repo is

const discovery = new DiscoveryV1({
  iam_apikey: '<my apikey>',
  version: '<my version date>',
  proxy: {
    host: '<my proxy host>',
    port: '<my proxy port>',
  },
  httpsOverHttp: true, // NEW OPTION, WILL TELL SDK TO CREATE A TUNNEL
});

discovery.listEnvironments()
  .then(res => {
    console.log(res);
  })
  .catch(err => {
    console.log(err);
  });
```

_Note: This new option is only available for Discovery and Assistant (v1 and v2)._
