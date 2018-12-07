# Bithub

## Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "X-Wallet-ID: meowmeowmeow"
  -H "X-Signature: meowmeowmeow"
```

> Make sure to replace `meowmeowmeow` with your API key.

In order to access a wallet, clients are required to send the headers:

Header | Description
--------- | -----------
X-Wallet-ID | Identity is the Peer-ID, this will identify the peer and its wallet.
X-Signature | Signature is the current request signature, using requestSigningKey, the m/1/1 derivative of the Extended Private Key.

## Register a Walelt

```shell
curl "https://bithub.imtouch.io/wallets"
  -X POST
  -H "Content-Type: application/json"
  -d '{"requestPubKey":"03a3bec0d0cb725121ed4534a7857600079"}'
```

This endpoint register a walelt.

### HTTP Request

`POST https://bithub.imtouch.io/wallets`

### Body Parameters

Parameter | Default | Description
--------- | ------- | -----------
requestPubKey | false | Public Key used to check requests from this wallet.

## Patch a Specific Wallet

```shell
curl "https://bithub.imtouch.io/wallets/5bde947a9f53d4384e2eea95"
  -X PATCH
  -H "Content-Type: application/json"
  -d '{"name":"Wallet Name","assetIds:[3]"}'
```

> The above command returns JSON structured like this:

```json
{
  "_id": "5bde947a9f53d4384e2eea95",
  "requestPubKey": "03a3bec0d0cb725121ed4534a7857600079",
  "assets": [
    {
      "_id": 3,
      "defaulted": true,
      "verified": true,
      "enabled": true,
      "name": "Ethereum",
      "symbol": "ETH",
      "derivationPath": "m/44'/60'/0'",
      "platform": "Ethereum",
      "network": "mainnet",
      "insight": "https://insight.imtouch.io",
      "createdAt": "2018-11-20T09:11:09.470Z",
      "updatedAt": "2018-11-20T09:11:09.470Z",
      "units": [
        {
          "name": "Wei",
          "decimals": 0
        },
        {
          "name": "GWei",
          "decimals": 9
        },
        {
          "name": "ETH",
          "decimals": 18
        }
      ],
      "feeUnits": [
        {
          "name": "Wei",
          "decimals": 0
        },
        {
          "name": "GWei",
          "decimals": 9
        },
        {
          "name": "ETH",
          "decimals": 18
        }
      ],
      "blockExplorer": "https://etherscan.io",
    }
  ],
  "createdAt": "2018-11-04T06:40:58.798Z",
  "updatedAt": "2018-11-04T06:40:58.798Z"
}
```

### HTTP Request

`PATCH https://bithub.imtouch.io/wallets/<ID>`

### URL Parameters

Parameter | Default | Description
--------- | ------- | -----------
ID | false | The ID of the wallet to patch.

### Body Parameters

Parameter | Default | Description
--------- | ------- | -----------
name | false | Name of the wallet.
assetIds | false | Asset ID with json array.

## Check For Updates

```shell
curl "https://bithub.imtouch.io/releases/latest?paltform=android&channel=release"
```

> The above command returns JSON structured like this:

```json
{
  "version": "1.0.0",
  "build": 123,
  "logs": "Supports Ethereum Classic.",
  "forced": true,
  "dls": {
    "direct": "https://imtouch.io/download/android/v1/Touch-1.0.0-123.apk",
    "store": "https://play.google.com/store/apps/details?id=io.imtouch.gil"
  }
}
```

### HTTP Request

`GET https://bithub.imtouch.io/releases/latest?paltform=<PLATFORM>&channel=<CHANNEL_NAME>`

### URL Parameters

Parameter | Default | Description
--------- | ------- | -----------
PLATFORM | false | `ios`, `android`.
CHANNEL_NAME | false | `master`, `release`, `development`