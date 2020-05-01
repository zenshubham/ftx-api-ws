# ftx-api-ws

    npm install ftx-ws

API wrapper for the [FTX WS API](https://docs.ftx.com/#ws-api). Please refer to [their documentation](https://docs.ftx.com/#ws-api) for eveything explained. Check out `sample.js` for lib usage.

# Sample
```
const FTXWs = require('ftx-ws');

// including private channels:
// const ftx = new FTXWs({
//   key: 'x',
//   secret: 'y',
//   subaccount: 'z'
// })

// only public channels:
const ftx = new FTXWs();

const go = async () => {
  await ftx.connect();

  ftx.subscribe('ticker', 'BTC-PERP');
  ftx.on('BTC-PERP::ticker', console.log);

  if you passed api credentials:
  ftx.subscribe('fills');
  ftx.on('fills', console.log);

  if you want to know when the status of underlying socket changes
  ftx.on('statusChange', console.log);
}

go();
```