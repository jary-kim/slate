# Aptos
## Account

지갑 정보 반환

```shell
curl --location 'https://dev-api.waas.myabcwallet.com/wapi/v2/aptos/account?address=0x01a17a77b1bad5686ff8e92344cf4dba68cb76d945402ba9158a99be5bf646ca&chainId=2' \
--header 'Authorization: Bearer eyJraWQiOiIxNSIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2In0.eyJzdWIiOiJjYWRjNzZhMWU1MGI0NjY4OGE0ZTA1NTFkY2Q4MjlkYSIsImF1ZCI6Imh0dHBzOi8....'
```
```python
```
```javascript

```
> 성공시 200 status 반환

```json
{
    "authentication_key": "0x01a17a77b1bad5686ff8e92344cf4dba68cb76d945402ba9158a99be5bf646ca",
    "sequence_number": "1"
}
```

### HTTP Request

`GET https://dev-api.waas.myabcwallet.com/wapi/v2/aptos/account`

### Request Header

Name | Require | Value
--------- | ------- | -----------
Authorization | true | 인증 JWT

### Query Parameters

Parameter | Require | Description
--------- | ------- | -----------
address| true | 지갑 주소
chainId | true | 10진수 Chain ID

## Address

pubkey를 통한 지갑 주소 확인

```shell
curl --location 'https://dev-api.waas.myabcwallet.com/wapi/v2/aptos/address?pubkey=0x02563c08c5982ce67cd1c308e5a21cb5133d8c9aae9fc63155d1fbdb08151de7a3&chainId=2' \
--header 'Authorization: Bearer eyJraWQiOiI0MSIsInR5cCI6IkpXVCIsImFsZyI6IkVTMj....'
```
```python
```
```javascript

```
> 성공시 200 status 반환

```json
{
    "result": "0x01a17a77b1bad5686ff8e92344cf4dba68cb76d945402ba9158a99be5bf646ca"
}
```

### HTTP Request

`GET https://dev-api.waas.myabcwallet.com/wapi/v2/aptos/address`

### Request Header

Name | Require | Value
--------- | ------- | -----------
Authorization | true | 인증 JWT

### Query Parameters

Parameter | Require | Description
--------- | ------- | -----------
pubkey | true | 사용자 지갑 생성에서 사용된 pubkey
chainId | true | 10진수 Chain ID

## Balance

지갑 잔액 확인

```shell
curl --location 'https://dev-api.waas.myabcwallet.com/wapi/v2/aptos/balance?address=0x01a17a77b1bad5686ff8e92344cf4dba68cb76d945402ba9158a99be5bf646ca&chainId=2' \
--header 'Authorization: Bearer eyJraWQiOiIxNSIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2In0.eyJzdWIiOiJjYWRjNzZhMWU1MGI0NjY4OGE0ZTA1NTFkY2Q4MjlkYSIsImF1ZCI6Imh0dHBzOi8vbXcubXl....'
```
```python
```
```javascript

```
> 성공시 200 status 반환

```json
{
    "result": "199999299"
}
```

### HTTP Request

`GET https://dev-api.waas.myabcwallet.com/wapi/v2/aptos/balance`

### Request Header

Name | Require | Value
--------- | ------- | -----------
Authorization | true | 인증 JWT

### Query Parameters

Parameter | Require | Description
--------- | ------- | -----------
address | true | 조회할 지갑 주소
chainId | true | 10진수 Chain ID

## GasEstimate

가스비 추론

```shell
curl --location 'https://dev-api.waas.myabcwallet.com/wapi/v2/aptos/gas/estimate?chainId=2' \
--header 'Authorization: Bearer eyJraWQiOiIxNSIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2In0.eyJzdWIiOiJjYWRjNzZhMWU1MGI0NjY4OGE0ZTA1NTFkY2Q4MjlkYSIsImF1ZCI6Imh0dHBzOi8vbXcubXlhYm...'
```
```python
```
```javascript

```
> 성공시 200 status 반환

```json
{
    "deprioritizedGasEstimate": "Some(100)",
    "gasEstimate": "100",
    "prioritizedGasEstimate": "Some(150)"
}
```

### HTTP Request

`GET https://dev-api.waas.myabcwallet.com/wapi/v2/aptos/gas/estimate`

### Request Header

Name | Require | Value
--------- | ------- | -----------
Authorization | true | 인증 JWT

### Query Parameters

Parameter | Require | Description
--------- | ------- | -----------
chainId | true | 10진수 Chain ID

## SequenceNumber

시퀀스넘버 조회

```shell
curl --location 'https://dev-api.waas.myabcwallet.com/wapi/v2/aptos/sequence?address=0x01a17a77b1bad5686ff8e92344cf4dba68cb76d945402ba9158a99be5bf646ca&chainId=2' \
--header 'Authorization: Bearer eyJraWQiOiIxNSIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2In0.eyJzdWIiOiJjYWRjNzZhMWU1MGI0NjY4OGE0ZTA1NTFkY2Q4MjlkYSIsImF1ZCI6Imh0dHBzOi8vbX...'
```
```python
```
```javascript

```
> 성공시 200 status 반환

```json
{
    "result": "1"
}
```

### HTTP Request

`GET https://dev-api.waas.myabcwallet.com/wapi/v2/aptos/sequence`

### Request Header

Name | Require | Value
--------- | ------- | -----------
Authorization | true | 인증 JWT

### Query Parameters

Parameter | Require | Description
--------- | ------- | -----------
address | true | 조회할 지갑 주소
chainId | true | 10진수 Chain ID

## Transfer Pre

Sign에 필요한 데이터를 반환합니다.

```python
```

```shell
curl --location 'https://dev-api.waas.myabcwallet.com/wapi/v2/aptos/transfer/pre' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--header 'Authorization: Bearer eyJraWQiOiI3NSIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2In0.eyJzdWIiOiJjYWRjNzZhMWU1MGI0NjY4OGE0ZTA1NTFkY2Q4MjlkYSIsImF1ZCI6Imh0dHBzOi8vbXcubX...' \
--data-urlencode 'sender=0x01a17a77b1bad5686ff8e92344cf4dba68cb76d945402ba9158a99be5bf646ca' \
--data-urlencode 'receiver=0x2e7ddbd83981345a96acb979855bde73b9e7720deb896706aed00c260c8ca0e9' \
--data-urlencode 'amount=1' \
--data-urlencode 'sequenceNumber=0' \
--data-urlencode 'expirationTimestampSecs=1712140621'
--data-urlencode 'chainId=2'
```

```javascript

```

> The above command returns JSON structured like this:

```json
{
    "mpcToken": "eyJraWQiOiJtcGMiLCJhbGciOiJFZERTQSJ9.eyJ1aWQiOiJhYTMxNjZmZS03NjZjLTQ5MzAtOTg0YS1mZjYwYzJkMjFiM2IiLCJ0aW1lc3RhbXAiOjE3MTIxMDg2NjU2MzYsIm9wIjoiZ2VuIiwiZGF0YSI6eyJkc2EiOiJlY2RzYSIsImN1cnZlIjoic2VjcDI1NmsxIn0sImlhdCI6MTcxMjEwODY2NSwiZXhwIjoxNzEyMTA4Njc1fQ.pgFhTFBhMGzU5uQYUCyN292hZWO2Pyf6kBsBhjvKgztLFXHhl68e5AcGGZoTeIxEpFUA56jM7eVrzHuxP8xeBQ",
    "hash": "614b36f15a6a5982a575d8a4d21e215edb7c38a14b5b19647210490932d9c694"
}
```

### HTTP Request

`POST https://dev-api.waas.myabcwallet.com/wapi/v2/aptos/transfer/pre`

### Request Header

Name | Require | Description
--------- | ------- | -----------
Authorization | true | 인증 JWT
Content-Type | true | application/x-www-form-urlencoded

### Request Body

Parameter | Require | Description
--------- | ----------- | -----------
sender | true | from
receiver | true | to
amount | true | value
expirationTimestampSecs | false | 유효 시간 (linux timestamp)
sequenceNumber | false | nonce
maxGasAmount | false | 최대 가스비
gasUnitPrice | false | gasPrice
chainId | true | 10진수 Chain ID

### Response Body

Field | Type | Description
--------- | ------- | -----------
mpcToken | String | MPC Sign에 사용되는 MPC token
hash | String | MPC Sign에 사용되는 hash

## Simulate transfer

Transaction 검증, MPC Sign 함수 호출 이후 사용

```python
```

```shell
curl --location 'https://dev-api.waas.myabcwallet.com/wapi/v2/aptos/transfer/simulate' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--header 'Authorization: Bearer eyJraWQiOiI3NSIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2In0.eyJzdWIiOiJjYWRjNzZhMWU1MGI0NjY4OGE0ZTA1NTFkY2Q4MjlkYSIsImF1ZCI6Imh0dHBzOi8vbXcubXlhYmN...' \
--data-urlencode 'sender=0x01a17a77b1bad5686ff8e92344cf4dba68cb76d945402ba9158a99be5bf646ca' \
--data-urlencode 'receiver=0x2e7ddbd83981345a96acb979855bde73b9e7720deb896706aed00c260c8ca0e9' \
--data-urlencode 'amount=1' \
--data-urlencode 'sequenceNumber=0' \
--data-urlencode 'expirationTimestampSecs=1712140621' \
--data-urlencode 'pubkey=0x02563c08c5982ce67cd1c308e5a21cb5133d8c9aae9fc63155d1fbdb08151de7a3' \
--data-urlencode 'signatureJson={"signstr":"{\"sig_num\":1,\"sig_list\":[{\"r\":\"0xe7e3d9d8fa2344d57f6399a1a337fdcbbafb39bc7e08b6f40f91e59065506edd\",\"s\":\"0x306f98262b88f9c8b61ea78f7ff9486c426ce0090969f03c671f769b298571f0\",\"der\":\"\",\"vsource\":1}]}","iserr":false,"errmsg":""}' \
--data-urlencode 'chainId=2'
```

```javascript

```

> The above command returns JSON structured like this:

```json
{
    "version": 995472093,
    "transaction": {
        "UserTransaction": {
            "raw_txn": {
                "sender": "01a17a77b1bad5686ff8e92344cf4dba68cb76d945402ba9158a99be5bf646ca",
                "sequence_number": 0,
                "payload": {
                    "EntryFunction": {
                        "module": {
                            "address": "0000000000000000000000000000000000000000000000000000000000000001",
                            "name": "aptos_account"
                        },
                        "function": "transfer",
                        "ty_args": [],
                        "args": [
                            [
                                46,
                                125,
                                219,
                                216,
                                57,
                                129,
                                52,
                                90,
                                150,
                                172,
                                185,
                                121,
                                133,
                                91,
                                222,
                                115,
                                185,
                                231,
                                114,
                                13,
                                235,
                                137,
                                103,
                                6,
                                174,
                                208,
                                12,
                                38,
                                12,
                                140,
                                160,
                                233
                            ],
                            [
                                1,
                                0,
                                0,
                                0,
                                0,
                                0,
                                0,
                                0
                            ]
                        ]
                    }
                },
                "max_gas_amount": 2000000,
                "gas_unit_price": 100,
                "expiration_timestamp_secs": 1712140621,
                "chain_id": 2
            },
            "authenticator": {
                "SingleSender": {
                    "sender": {
                        "SingleKey": {
                            "authenticator": {
                                "public_key": {
                                    "Secp256k1Ecdsa": {
                                        "public_key": "0x04563c08c5982ce67cd1c308e5a21cb5133d8c9aae9fc63155d1fbdb08151de7a3c87168cd89cedc8a4297f9207fd8924a2ab18be027df0e0ece9bd0222e7e3006"
                                    }
                                },
                                "signature": {
                                    "Secp256k1Ecdsa": {
                                        "signature": "0xe7e3d9d8fa2344d57f6399a1a337fdcbbafb39bc7e08b6f40f91e59065506edd306f98262b88f9c8b61ea78f7ff9486c426ce0090969f03c671f769b298571f0"
                                    }
                                }
                            }
                        }
                    }
                }
            }
        }
    },
    "info": {
        "V0": {
            "gas_used": 7,
            "status": "Success",
            "transaction_hash": "853d6846e80b1e9614a9fc3f36a0c4561962c461bda1cdf8a2649cefb64e9933",
            "event_root_hash": "0000000000000000000000000000000000000000000000000000000000000000",
            "state_change_hash": "0000000000000000000000000000000000000000000000000000000000000000",
            "state_checkpoint_hash": null,
            "state_cemetery_hash": null
        }
    },
    "gas_used": "7",
    "max_gas_amount": "2000000",
    "gas_unit_price": "100"
}
```

### HTTP Request

`POST https://dev-api.waas.myabcwallet.com/wapi/v2/aptos/transfer/simulate`

### Request Header

Name | Require | Description
--------- | ------- | -----------
Authorization | true | 인증 JWT
Content-Type | true | application/x-www-form-urlencoded

### Request Body

Parameter | Require | Description
--------- | ----------- | -----------
sender | true | from
receiver | true | to
amount | true | value
expirationTimestampSecs | false | 유효 시간 (linux timestamp)
sequenceNumber | false | nonce
maxGasAmount | false | 최대 가스비
gasUnitPrice | false | gasPrice
pubkey | true | MPC Sign에 사용된 MPC 지갑의 pubkey
signatureJson | true | Sign을 통해 얻은 signatureJson
chainId | true | 10진수 Chain ID

### Response Body

TBD

Field | Type | Description
--------- | ------- | -----------

## Transfer

Transaction send rawTransaction

```python
```

```shell
curl --location 'https://dev-api.waas.myabcwallet.com/wapi/v2/aptos/transfer' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--header 'Authorization: Bearer eyJraWQiOiI3NSIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2In0.eyJzdWIiOiJjYWRjNzZhMWU1MGI0NjY4OGE0ZTA1NTFkY2Q4MjlkYSIsImF1ZCI6Imh0dHBzOi8vbXcubXlhYmN...' \
--data-urlencode 'sender=0x01a17a77b1bad5686ff8e92344cf4dba68cb76d945402ba9158a99be5bf646ca' \
--data-urlencode 'receiver=0x2e7ddbd83981345a96acb979855bde73b9e7720deb896706aed00c260c8ca0e9' \
--data-urlencode 'amount=1' \
--data-urlencode 'sequenceNumber=0' \
--data-urlencode 'expirationTimestampSecs=1712140621' \
--data-urlencode 'pubkey=0x02563c08c5982ce67cd1c308e5a21cb5133d8c9aae9fc63155d1fbdb08151de7a3' \
--data-urlencode 'signatureJson={"signstr":"{\"sig_num\":1,\"sig_list\":[{\"r\":\"0xe7e3d9d8fa2344d57f6399a1a337fdcbbafb39bc7e08b6f40f91e59065506edd\",\"s\":\"0x306f98262b88f9c8b61ea78f7ff9486c426ce0090969f03c671f769b298571f0\",\"der\":\"\",\"vsource\":1}]}","iserr":false,"errmsg":""}'
--data-urlencode 'chainId=2'
```

```javascript

```

> The above command returns JSON structured like this:

```json
{
    "hash": "0x9d12d6ae866823f0d3f86fa61d8fdab0ac907f0bd840dcf9e55feedc9454ffcd",
    "sender": "0x1a17a77b1bad5686ff8e92344cf4dba68cb76d945402ba9158a99be5bf646ca",
    "sequenceNumber": null,
    "maxGasAmount": null,
    "gasUnitPrice": null,
    "expirationTimestampSecs": null,
    "payload": {
        "type": "entry_function_payload",
        "function": "0x1::aptos_account::transfer",
        "typeArguments": null,
        "arguments": [
            "0x2e7ddbd83981345a96acb979855bde73b9e7720deb896706aed00c260c8ca0e9",
            "0x0100000000000000"
        ]
    },
    "signature": {
        "type": "single_sender",
        "publicKey": null,
        "signature": "0xe7e3d9d8fa2344d57f6399a1a337fdcbbafb39bc7e08b6f40f91e59065506edd306f98262b88f9c8b61ea78f7ff9486c426ce0090969f03c671f769b298571f0"
    }
}
```

> SequenceNumber too old error returns JSON structured like this:

```json
{
    "status": 400,
    "timestamp": "2024-04-03T01:49:27.436+00:00",
    "message": "(ecdsa_coin_transfer) message:Invalid transaction: Type: Validation Code: SEQUENCE_NUMBER_TOO_OLD, vm_error_code:3, code:vm_error",
    "errors": [],
    "code": "0"
}
```

> Signature error returns JSON structured like this: sign에 사용한 parameter와 send시 사용한 signature가 다를 경우 발생

```json
{
    "status": 400,
    "timestamp": "2024-04-03T01:50:05.897+00:00",
    "message": "(ecdsa_coin_transfer) message:Invalid transaction: Type: Validation Code: INVALID_SIGNATURE, vm_error_code:1, code:vm_error",
    "errors": [],
    "code": "0"
}
```

### HTTP Request

`POST https://dev-api.waas.myabcwallet.com/wapi/v2/aptos/transfer`

### Request Header

Name | Require | Description
--------- | ------- | -----------
Authorization | true | 인증 JWT
Content-Type | true | application/x-www-form-urlencoded

### Request Body

Parameter | Require | Description
--------- | ----------- | -----------
sender | true | from
receiver | true | to
amount | true | value
expirationTimestampSecs | false | 유효 시간 (linux timestamp)
sequenceNumber | false | nonce
maxGasAmount | false | 최대 가스비
gasUnitPrice | false | gasPrice
pubkey | true | MPC Sign에 사용된 MPC 지갑의 pubkey
signatureJson | true | Sign을 통해 얻은 signatureJson
chainId | true | 10진수 Chain ID

### Response Body

TBD