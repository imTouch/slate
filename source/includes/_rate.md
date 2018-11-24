# Rates

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

This endpoint retrieves all faitrates.

### HTTP Request

`GET https://rate.imtouch.io/faitrates`

## Get All Rates

```shell
curl "https://rate.imtouch.io/rates?fsyms=BTC,ETH&tsyms=USD,CNY"
```

> The above command returns JSON structured like this:

```json
{
  "BTC": {
    "USD": 4341.09,
    "CNY": 30119.00769189
  },
  "ETH": {
    "USD": 124.05,
    "CNY": 860.6739100499999
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