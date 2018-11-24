# Insight

## Request New Address

```shell
curl "https://insight.imtouch.io/addresses"
  -X POST
  -H "Content-Type: application/json"
  -d '{"xPubKey":"xpub6CrixgtR7pjYQjAkt86DPbPAwmgtoa9sRVWiHbqEV8aGdMWBsYAs93F6cM1HhawcVMUevAsNzbVUt6QpwvpqKFJohtTVq7cC1SQiqzwEtgE"}'
```

> The above command returns JSON structured like this:

```json
{
  "address": "0xB48B9b88a99CC5b7Ee8d986D341a4cE31214CC49",
  "path": "m/0/0"
}
```

This endpoint request new address.

### HTTP Request

`POST https://insight.imtouch.io/addresses`

## Balances

```shell
curl "https://insight.imtouch.io/balances?xPubKey=xpub6CrixgtR7pjYQjAkt86DPbPAwmgtoa9sRVWiHbqEV8aGdMWBsYAs93F6cM1HhawcVMUevAsNzbVUt6QpwvpqKFJohtTVq7cC1SQiqzwEtgE"
```

> The above command returns JSON structured like this:

```json
{
  "confirmed": 0,
  "unconfirmed": 0
}
```

### HTTP Request

`GET https://insight.imtouch.io/balances?xPubKey=<xPubKey>`

### URL Parameters

Parameter | Default | Description
--------- | ------- | -----------
xPubKey | false | Extended Public Key for wallet.

## Get All FeeLevels

```shell
curl "https://insight.imtouch.io/feelevels"
```

> The above command returns JSON structured like this:

```json
{
  "superEconomy": {
    "fee": 4000000000,
    "estDuration": 1089
  },
  "economy": {
    "fee": 22000000000,
    "estDuration": 32
  },
  "normal": {
    "fee": 32000000000,
    "estDuration": 23
  },
  "priority": {
    "fee": 42000000000,
    "estDuration": 11
  },
  "urgent": {
    "fee": 53000000000,
    "estDuration": 11
  }
}
```

### HTTP Request

`GET https://insight.imtouch.io/feelevels`

## Get All Transactions

```shell
curl "https://insight.imtouch.io/txns?xPubKey=xpub6CrixgtR7pjYQjAkt86DPbPAwmgtoa9sRVWiHbqEV8aGdMWBsYAs93F6cM1HhawcVMUevAsNzbVUt6QpwvpqKFJohtTVq7cC1SQiqzwEtgE"
```

> The above command returns JSON structured like this:

```json
{
  "total": 1,
  "limit": 10,
  "skip": 0,
  "data": [
    {
      "txid": "0x419fea4d855e88a481c0b342d397123c57b12e53c607e975d1fa5e4269214ebc",
      "fee": 520680000000000,
      "confirmations": 55295,
      "time": "2018-11-13T09:55:32.000Z",
      "status": "succeed",
      "inputs": [
        {
          "address": "0x886c712d41bf9f031ebf4bc265f2ba45558ba103",
          "amount": 0
        }
      ],
      "outputs": [
        {
          "address": "0x818fc6c2ec5986bc6e2cbf00939d90556ab12ce5",
          "amount": 0
        }
      ],
      "action": "unknown",
      "amount": 0
    }
  ]
}
```

### HTTP Request

`GET https://insight.imtouch.io/txns?xPubKey=<xPubKey>`

### URL Parameters

Parameter | Default | Description
--------- | ------- | -----------
xPubKey | false | Extended Public Key for wallet.

## Build a Transaction

```shell
curl "https://insight.imtouch.io/txns"
  -X POST
  -H "Content-Type: application/json"
  -d '{"xPubKey":"xpub6CrixgtR7pjYQjAkt86DPbPAwmgtoa9sRVWiHbqEV8aGdMWBsYAs93F6cM1HhawcVMUevAsNzbVUt6QpwvpqKFJohtTVq7cC1SQiqzwEtgE","addressTo": "0x886c712d41bf9f031ebf4bc265f2ba45558ba103", "amount": "1000000000"}'
```

> The above command returns JSON structured like this:

```json
{
  "nonce": "0x4c",
  "gas": "0x5208",
  "gasPrice": "0x306dc4200",
  "to": "0xdFa8C1872c5a702a02f1F721f79B3fEd7a603DAB",
  "value": "0xa",
  "data": "0x",
  "hex": "e44c850306dc420082520894dfa8c1872c5a702a02f1f721f79b3fed7a603dab0a801c8080"
}
```

### HTTP Request

`POST https://insight.imtouch.io/txns`

### Body Parameters

Parameter | Default | Description
--------- | ------- | -----------
xPubKey | false | Extended Public Key for wallet.
addressTo | false | Recive address.
amount | false | all currency amounts are in units of best less.

## Broadcast Raw Transaction

```shell
curl "https://insight.imtouch.io/broadcast_raw"
  -X POST
  -H "Content-Type: application/json"
  -d '{"raw":"f86480843b9aca00830186a094efba531fb35e3ffe381028631e4343be497952f701801ba01186defe7ae83fd09698efcc03517df49c06ada7fa11268ce2a306179e03be9da01a8a15c193f88048e2e1b13f783b80dfb7763063a06d52bf7914c350c8f9c2af"}'
```

> The above command returns JSON structured like this:

```json
{
  "txid": "0x419fea4d855e88a481c0b342d397123c57b12e53c607e975d1fa5e4269214ebc",
  "fee": 520680000000000,
  "confirmations": 55295,
  "time": "2018-11-13T09:55:32.000Z",
  "status": "succeed",
  "inputs": [
    {
      "address": "0x886c712d41bf9f031ebf4bc265f2ba45558ba103",
      "amount": 0
    }
  ],
  "outputs": [
    {
      "address": "0x818fc6c2ec5986bc6e2cbf00939d90556ab12ce5",
      "amount": 0
    }
  ],
  "action": "unknown",
  "amount": 0
}
```

### HTTP Request

`POST https://insight.imtouch.io/broadcast_raw`

### Body Parameters

Parameter | Default | Description
--------- | ------- | -----------
raw | false | signed transaction hex string.