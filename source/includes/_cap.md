# Market Capitalization

## Get All Alt Currencies

```shell
curl "https://rate.imtouch.io/alt_currencies"
```

> The above command returns JSON structured like this:

```json
[
  "USD",
  "CNY",
  "HKD",
  "KRW",
  "JPY",
  "EUR",
  "AUD",
  "BRL",
  "CAD",
  "CHF",
  "CLP",
  "CZK"
]
```

This endpoint retrieves all alt currencies.

### HTTP Request

`GET https://rate.imtouch.io/alt_currencies`

## Get Rates

```shell
curl "https://rate.imtouch.io/rates?fsyms=BTC,ETH&tsyms=USD,CNY"
```

> The above command returns JSON structured like this:

```json
{
  "BTC": {
    "USD": {
      "rate": 4341.09,
      "change": -0.02,
      "volume": 3786450000
    },
    "CNY": {
      "rate": 30119.0076,
      "change": -0.02,
      "volume": 3786450000
    }
  }
}
```

This endpoint retrieves all faitrates.
                                                                                               
### HTTP Request

`GET https://bithub.imtouch.io/rates`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
fsyms | false | The cryptocurrency symbol of interest.
tsyms | false | Comma separated cryptocurrency symbols list to convert into.

## Streaming

### Subs Watchlist

Event | For Example | Description
--------- | ----------- | -----------
`fsym`->`tsym` | `BTC->USD`: 3511.47 | realtime rate in the specified currency.
`symbol`-C | `BTC-C`: -0.02 | daily rate change in the specified currency.
`symbol`-V | `BTC-V`: 3786450000 | daily volume in the specified currency.