# Address
## EOA 주소 검증

올바른 EVM 기반의 블록체인 주소 체계인지 검증한다.

> 성공시 200 status 반환

```json
{
  "result": true
}
```

<aside class="notice">
실제 존재하는 주소인지 확인하는 것이 아닌 주소 체계가 올바른지 확인한다.
</aside>

### HTTP Request

`GET https://dev-api.waas.myabcwallet.com/wapi/v2/address/verify`


### Request Header

Name | Require | Description
--------- | ------- | -----------
Authorization | true | 인증 JWT

### Query Parameters

Parameter | Require | Description
--------- | ------- | -----------
address | true | 검증하고자하는 주소

## 잔액 조회

Address에 소유한 잔액을 조회한다.

> 성공시 200 status 반환

```json
{
    "result": "0x1"
}
```

### HTTP Request

`GET https://dev-api.waas.myabcwallet.com/wapi/v2/address/balance`


### Request Header

Name | Require | Description
--------- | ------- | -----------
Authorization | true | 인증 JWT

### Query Parameters

Parameter | Require | Description
--------- | ------- | -----------
address | true | 조회할 지갑 주소
chainId | true | 10진수 Chain ID

## Nonce 조회

Address nonce 조회

> 성공시 200 status 반환

```json
{
    "result": "0x1"
}
```

### HTTP Request

`GET https://dev-api.waas.myabcwallet.com/wapi/v2/address/nonce`


### Request Header

Name | Require | Description
--------- | ------- | -----------
Authorization | true | 인증 JWT

### Query Parameters

Parameter | Require | Description
--------- | ------- | -----------
address | true | 조회할 지갑 주소
chainId | true | 10진수 Chain ID
