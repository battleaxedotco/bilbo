# Bilbo

Paddle Billing report converter

Live at: https://battleaxe.dev/bilbo

![UI](https://github.com/battleaxedotco/bilbo/assets/8580225/b7137d9c-ace1-419c-980a-e5cd367ae2e2)

## Usage

1. Download a report for the desired date range from paddle.com
2. Drop the downloaded CSV file into [the app](https://battleaxe.dev/bilbo/)
3. Copy out the total earnings for each product with tabs for pasting into another spreadsheet

## Whats the point?

We were previously on gumroad.com and moved to paddle.com and began using the Paddle Billing platform. This empowers us to sell multiple items in a single transaction. The challenge is that each line of a report CVS is the entire transaction and will contain multiple products that could vary in price. 

**Bilbo** parses these multi-item purchases and adds everything up together. 

### Innacuracies

The calculator processes assumes that multi-item purchases contain the same quantity for each item. Example:

- 2x Overlord
- 2x Rubberhose

If the customer purchases irregular numbers the calculation will be wrong:

- 3x Overlord
- 1x Rubberhose



## Building your own

A few elements are hard coded. A list of products:

```js
const products = {
  pri_01h7jacqjse1pmpds97q8aetzk: {
    name: "Rubberhose",
    price: 65
  },
  pri_01h7gcp07yacazx9rs35sgeryd: {
    name: "Overlord",
    price: 55
  },
  pri_01h7jb6nxqbhkhqfg1w5myqfhd: {
    name: "Timelord",
    price: 45
  },
  pri_01h7jb3z5a4zkj97t1wj62mkq8: {
    name: "Anubis",
    price: 25
  },
};
```

With matching priceIDs 
```js
totalEarnings: {
  pri_01h7jacqjse1pmpds97q8aetzk: 0,
  pri_01h7gcp07yacazx9rs35sgeryd: 0,
  pri_01h7jb6nxqbhkhqfg1w5myqfhd: 0,
  pri_01h7jb3z5a4zkj97t1wj62mkq8: 0,
},
```

Update those values with the prices from your own Paddle Dashboard.

### Disclaimer

**Bilbo** is used exclusively for getting a general idea of product sales.

This is probably inaccurate and should not be used for calculating taxes or anything legal. 

No warranties are given. Use at your own risk. 