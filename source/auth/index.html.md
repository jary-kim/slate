---
title: API Reference

includes:
  - errors

code_clipboard: true

meta:
  - name: Main page
    content: Documentation for the ABC WaaS API
---
# WaaS 2.0

> Version 1.0.0

## Path Table

| Method | Path | Description |
| --- | --- | --- |
| GET | [/v2/address/verify](#getv2addressverify) | verify |
| GET | [/v2/gas/price](#getv2gasprice) | price |
| GET | [/v2/gas/suggestedGasFees](#getv2gassuggestedgasfees) | suggestedGasFees |
| POST | [/v2/mpc/wallets](#postv2mpcwallets) | create/recover |
| GET | [/v2/mpc/wallets/info](#getv2mpcwalletsinfo) | wallet info |
| GET | [/v2/mpc/wallets/nonce](#getv2mpcwalletsnonce) | nonce |
| POST | [/v2/mpc/wallets/check/device-password](#postv2mpcwalletscheckdevice-password) | checkDevicePassword |
| POST | [/v2/mpc/wallets/check/device-password/share](#postv2mpcwalletscheckdevice-passwordshare) | checkDevicePasswordShare |
| POST | [/v2/sign](#postv2sign) | sign |
| POST | [/v2/sign/typed-data](#postv2signtyped-data) | typedDataSign |
| POST | [/v2/sign/raw-tx/send](#postv2signraw-txsend) | sendTransaction |
| GET | [/v2/token/transfer-data](#getv2tokentransfer-data) | transfer-data |
| GET | [/v2/token/info](#getv2tokeninfo) | info |
| GET | [/v2/token/approve-data](#getv2tokenapprove-data) | approve-data |
| GET | [/v2/token/allowance](#getv2tokenallowance) | allowance |
| GET | [/v2/transactions](#getv2transactions) | transactionList |

## Reference Table

| Name | Path | Description |
| --- | --- | --- |
| bearerAuth | [#/components/securitySchemes/bearerAuth](#componentssecurityschemesbearerauth) |  |

## Path Details

***

### [GET]/v2/address/verify

- Summary  
verify

#### Parameters(Query)

```ts
address?: string
```

#### Responses

- 200 Successful response

`application/json`

***

### [GET]/v2/gas/price

- Summary  
price

#### Parameters(Query)

```ts
isEIP1559?: boolean
```

```ts
chainId?: integer
```

#### Responses

- 200 Successful response

`application/json`

***

### [GET]/v2/gas/suggestedGasFees

- Summary  
suggestedGasFees

#### Parameters(Query)

```ts
chainId?: string
```

#### Responses

- 200 Successful response

`application/json`

***

### [POST]/v2/mpc/wallets

- Summary  
create/recover

#### Headers

```ts
Secure-Channel?: string
```

#### RequestBody

- application/x-www-form-urlencoded

```ts
{
  email?: string
  devicePassword?: string
}
```

#### Responses

- 200 OK

`application/json`

```ts
{
}
```

***

### [GET]/v2/mpc/wallets/info

- Summary  
wallet info

#### Responses

- 200 OK

`application/json`

```ts
{
}
```

***

### [GET]/v2/mpc/wallets/nonce

- Summary  
nonce

#### Responses

- 200 Successful response

`application/json`

***

### [POST]/v2/mpc/wallets/check/device-password

- Summary  
checkDevicePassword

#### Headers

```ts
Secure-Channel?: string
```

#### RequestBody

- application/x-www-form-urlencoded

```ts
{
  devicePassword?: string
  encryptDevicePassword?: string
}
```

#### Responses

- 200 OK

`application/json`

```ts
{
}
```

***

### [POST]/v2/mpc/wallets/check/device-password/share

- Summary  
checkDevicePasswordShare

#### Headers

```ts
Secure-Channel?: string
```

#### RequestBody

- application/x-www-form-urlencoded

```ts
{
  devicePassword?: string
  pvencstr?: string
}
```

#### Responses

- 200 OK

`application/json`

```ts
{
}
```

***

### [POST]/v2/sign

- Summary  
sign

#### Headers

```ts
Secure-Channel?: string
```

#### RequestBody

- application/x-www-form-urlencoded

```ts
{
  from?: string
  to?: string
  value?: string
  data?: string
  nonce?: integer
  gasPrice?: string
  gasLimit?: string
  maxPriorityFeePerGas?: string
  maxFeePerGas?: string
  chainId?: integer
  encryptDevicePassword?: string
  pvencstr?: string
  uid?: string
  wid?: string
  sid?: string
  type?: string
}
```

#### Responses

- 200 OK

`text/plain`

```ts
{
  "type": "string"
}
```

***

### [POST]/v2/sign/typed-data

- Summary  
typedDataSign

#### Headers

```ts
Secure-Channel?: string
```

#### RequestBody

- application/x-www-form-urlencoded

```ts
{
  messageJson?: string
  encryptDevicePassword?: string
  pvencstr?: string
  uid?: string
  wid?: string
  sid?: string
  chainId?: integer
  version?: string
}
```

#### Responses

- 200 OK

`text/plain`

```ts
{
  "type": "string"
}
```

***

### [POST]/v2/sign/raw-tx/send

- Summary  
sendTransaction

#### RequestBody

- application/x-www-form-urlencoded

```ts
{
  signedSerializeTx?: string
  chainId?: integer
}
```

#### Responses

- 200 Successful response

`application/json`

***

### [GET]/v2/token/transfer-data

- Summary  
transfer-data

#### Parameters(Query)

```ts
from?: string
```

```ts
to?: string
```

```ts
value?: string
```

```ts
chainId?: integer
```

#### Responses

- 200 OK

`text/plain`

```ts
{
  "type": "string"
}
```

***

### [GET]/v2/token/info

- Summary  
info

#### Parameters(Query)

```ts
coa?: string
```

```ts
eoa?: string
```

```ts
chainId?: integer
```

#### Responses

- 400 Bad Request

`application/json`

```ts
{
}
```

***

### [GET]/v2/token/approve-data

- Summary  
approve-data

#### Parameters(Query)

```ts
spender?: string
```

```ts
value?: string
```

```ts
chainId?: integer
```

#### Responses

- 200 Successful response

`application/json`

***

### [GET]/v2/token/allowance

- Summary  
allowance

#### Parameters(Query)

```ts
coa?: string
```

```ts
owner?: string
```

```ts
spender?: string
```

```ts
chainId?: integer
```

#### Responses

- 200 Successful response

`application/json`

***

### [GET]/v2/transactions

- Summary  
transactionList

#### Parameters(Query)

```ts
chainId?: integer
```

```ts
address?: string
```

```ts
cursor?: string
```

```ts
size?: string
```

```ts
fromBlock?: string
```

```ts
toBlock?: string
```

```ts
toDate?: string
```

```ts
fromDate?: string
```

#### Responses

- 200 Successful response

`application/json`

## References

### #/components/securitySchemes/bearerAuth

```ts
{
  "type": "http",
  "scheme": "bearer"
}
```
