# Token
## 토큰 전송 데이터 생성

성공 시 응답메시지에 토큰 전송을 위한 data hex 문자열을 반환합니다.

```shell
curl --location 'https://dev-api.waas.myabcwallet.com/wapi/v2/token/transfer-data?from=0xbE616d5b24903efc58149f3c7511FeC2085c176e&to=0xbE616d5b24903efc58149f3c7511FeC2085c176e&value=0x0&chainId=8217'
--header 'Authorization: Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZyI6IkVT....' \
```
```python
import requests

url = "https://dev-api.waas.myabcwallet.com/wapi/v2/token/transfer-data?from=0xbE616d5b24903efc58149f3c7511FeC2085c176e&to=0xbE616d5b24903efc58149f3c7511FeC2085c176e&value=0x0&chainId=8217"

payload = {}
headers: { 
    'Authorization': 'Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZyI6IkV....'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```
```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://dev-api.waas.myabcwallet.com/wapi/v2/token/transfer-data?from=0xbE616d5b24903efc58149f3c7511FeC2085c176e&to=0xbE616d5b24903efc58149f3c7511FeC2085c176e&value=0x0&chainId=8217',
  headers: { 
    'Authorization': 'Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZyI6IkV....'
  }
};

axios.request(config)
.then((response) => {
  console.log(JSON.stringify(response.data));
})
.catch((error) => {
  console.log(error);
});
```
> 성공시 200 status 반환

```json
{
  "result":"0x23b872dd000000000000000000000000be616d5b24903efc58149f3c7511fec2085c176e000000000000000000000000be616d5b24903efc58149f3c7511fec2085c176e0000000000000000000000000000000000000000000000000000000000000000"
}
```

### HTTP Request

`GET https://dev-api.waas.myabcwallet.com/wapi/v2/token/transfer-data`

### Request Header

Name | Require | Value
--------- | ------- | -----------
Authorization | true | 인증 JWT

### Query Parameters

Parameter | Require | Description
--------- | ------- | -----------
chainId | true | 10진수 Chain ID
to | true | target EOA or CA
from | false | 
value| true | 16진수 wei

<aside class="notice">
Sign API 사용시 data 필드에 사용한다.
</aside>

## 토큰 정보 조회
```shell
curl --location 'https://dev-api.waas.myabcwallet.com/wapi/v2/token/transfer-data?from=0xbE616d5b24903efc58149f3c7511FeC2085c176e&to=0xbE616d5b24903efc58149f3c7511FeC2085c176e&value=0x0&chainId=8217'
--header 'Authorization: Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZyI6IkVT....' \
```
```python
import requests

url = "https://dev-api.waas.myabcwallet.com/wapi/v2/token/info?ca=0x043c471bee060e00a56ccd02c0ca286808a5a436&eoa=0xcAcCFD4b61823BC105A7354C2afc1e24F212A962&chainId=8217"

payload = {}
headers = {
  'Authorization': 'Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2In0.eyJzdWIiOiJiMjRjODM3YTZlOWU0M2M4YWVlNGM0MjM4YmNjMzY2MCIsImF1ZCI6Imh0d....'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)

```
```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://dev-api.waas.myabcwallet.com/wapi/v2/token/info?ca=0x043c471bee060e00a56ccd02c0ca286808a5a436&eoa=0xcAcCFD4b61823BC105A7354C2afc1e24F212A962&chainId=8217',
  headers: { 
    'Authorization': 'Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2In0.eyJzdWIiOiJiMjRjODM3YTZlOWU0M2M4YWVlNGM0MjM4YmNjMzY2....'
  }
};

axios.request(config)
.then((response) => {
  console.log(JSON.stringify(response.data));
})
.catch((error) => {
  console.log(error);
});

```
> 성공시 200 status 반환

```json
{
    "tokenName": "Wrapped Klay",
    "decimals": "18",
    "totalSupply": "19082454052396910528774",
    "symbol": "WKLAY",
    "balanceOf": "0"
}
```

### HTTP Request

`GET https://dev-api.waas.myabcwallet.com/wapi/v2/token/info`

### Request Header

Name | Require | Value
--------- | ------- | -----------
Authorization | true | 인증 JWT

### Query Parameters

Parameter | Require | Description
--------- | ------- | -----------
chainId | true | 10진수 Chain ID
ca | true | 토큰 컨트랙트 주소
eoa | false | 보유량을 확인하고 싶은 주소(Optional)

## 토큰 거래 권한 승인

실제 토큰 보유자로부터 대행자에게 토큰 개수에 해당하는 거래 권한을 승인합니다.

```shell
curl --location 'https://dev-api.waas.myabcwallet.com/wapi/v2/token/approve-data?spender=0xcAcCFD4b61823BC105A7354C2afc1e24F212A962&value=0x01&chainId=80001' \
--header 'Authorization: Bearer eyJraWQiOiIyNCIsInR5cCI6IkpX....g'
```
```python
import requests

url = "https://dev-api.waas.myabcwallet.com/wapi/v2/token/approve-data?spender=0xcAcCFD4b61823BC105A7354C2afc1e24F212A962&value=0x01&chainId=80001"

payload = {}
headers = {
  'Authorization': 'Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZyI6IkVT....'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```
```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://dev-api.waas.myabcwallet.com/wapi/v2/token/approve-data?spender=0xcAcCFD4b61823BC105A7354C2afc1e24F212A962&value=0x01&chainId=80001',
  headers: { 
    'Authorization': 'Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZyI6IkVT....'
  }
};

axios.request(config)
.then((response) => {
  console.log(JSON.stringify(response.data));
})
.catch((error) => {
  console.log(error);
});

```
> 성공시 200 status 반환

``` json
{
  "result":"0x095ea7b3000000000000000000000000caccfd4b61823bc105a7354c2afc1e24f212a9620000000000000000000000000000000000000000000000000000000000000001"
}
```

### HTTP Request

`GET https://dev-api.waas.myabcwallet.com/wapi/v2/token/approve-data`

### Request Header

Name | Require | Value
--------- | ------- | -----------
Authorization | true | 인증 JWT

### Query Parameters

Parameter | Require | Description
--------- | ------- | -----------
chainId | true | 10진수 Chain ID
value | true | 권한을 부여할 토큰의 개수
spender | true | 거래 대행자 주소

## 허가된 토큰 수량 조회

실제 토큰 보유자로부터 대행자에게 권한을 부여한 토큰 개수를 조회합니다.

```shell
curl --location 'https://dev-api.waas.myabcwallet.com/wapi/v2/token/allowance?ca=0xB923b52b60E247E34f9afE6B3fa5aCcBAea829E8&owner=0xcAcCFD4b61823BC105A7354C2afc1e24F212A962&spender=0xc18541C89F542E401AD0Cc5C1e81fCa220f3C537&chainId=80001' \
--header 'Authorization: Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2In0.eyJzdWIiOiJiMjRjODM3YTZlOWU0M2M4YWVlNGM0MjM4YmNjMzY2MC....'
```
```python
import requests

url = "https://dev-api.waas.myabcwallet.com/wapi/v2/token/allowance?ca=0xB923b52b60E247E34f9afE6B3fa5aCcBAea829E8&owner=0xcAcCFD4b61823BC105A7354C2afc1e24F212A962&spender=0xc18541C89F542E401AD0Cc5C1e81fCa220f3C537&chainId=80001"

payload = {}
headers = {
  'Authorization': 'Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZyI6IkVTM....'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```
```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://dev-api.waas.myabcwallet.com/wapi/v2/token/allowance?ca=0xB923b52b60E247E34f9afE6B3fa5aCcBAea829E8&owner=0xcAcCFD4b61823BC105A7354C2afc1e24F212A962&spender=0xc18541C89F542E401AD0Cc5C1e81fCa220f3C537&chainId=80001',
  headers: { 
    'Authorization': 'Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZy....'
  }
};

axios.request(config)
.then((response) => {
  console.log(JSON.stringify(response.data));
})
.catch((error) => {
  console.log(error);
});

```
> 성공시 200 status 반환

```json
{
  "result": 0
}
```

### HTTP Request

`GET https://dev-api.waas.myabcwallet.com/wapi/v2/token/allowance`

### Request Header

Name | Require | Value
--------- | ------- | -----------
Authorization | true | 인증 JWT

### Query Parameters

Parameter | Require | Description
--------- | ------- | -----------
chainId | true | 10진수 Chain ID
ca | true | 토큰 컨트랙트 주소
owner | true | 실제 토큰 보유자 주소
spender | true | 거래 대행자 주소
