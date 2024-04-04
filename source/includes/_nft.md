
# NFT
## NFT 소유 지갑 주소 조회
```shell
curl --location 'https://dev-api.waas.myabcwallet.com/wapi/v2/nft/owner?ca=0xb6f0b37c4f9a7a0b8c11e86e703cd0c498eb3630&chainId=137&tokenId=1' \
--header 'Authorization: Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZyI6....'
```
```python
import requests

url = "https://dev-api.waas.myabcwallet.com/wapi/v2/nft/owner?ca=0xb6f0b37c4f9a7a0b8c11e86e703cd0c498eb3630&chainId=137&tokenId=1"

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
  url: 'https://dev-api.waas.myabcwallet.com/wapi/v2/nft/owner?ca=0xb6f0b37c4f9a7a0b8c11e86e703cd0c498eb3630&chainId=137&tokenId=1',
  headers: { 
    'Authorization': 'Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2....'
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
> 성공 시 200 status 반환

```json
{
  "result":"0xf901be601848b31bc4455d5c405b0fbc2401c9b4"
}
```

### HTTP Request

`GET https://dev-api.waas.myabcwallet.com/wapi/v2/nft/owner`

### Request Header

Name | Require | Description
--------- | ------- | -----------
Authorization | true | 인증 JWT

### Query Parameters

Parameter | Require | Description
--------- | ------- | -----------
chainId | true | 10진수 Chain ID
tokenId | true | 10진수 Token ID
ca | true | 토큰 컨트랙트 주소

## NFT 컨트랙트 정보 조회
```shell
curl --location 'https://dev-api.waas.myabcwallet.com/wapi/v2/nft/contract?ca=0xb6f0b37c4f9a7a0b8c11e86e703cd0c498eb3630&chainId=137&eoa=0xcAcCFD4b61823BC105A7354C2afc1e24F212A962' \
--header 'Authorization: Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZ....'
```
```python
import requests

url = "https://dev-api.waas.myabcwallet.com/wapi/v2/nft/contract?ca=0xb6f0b37c4f9a7a0b8c11e86e703cd0c498eb3630&chainId=137&eoa=0xcAcCFD4b61823BC105A7354C2afc1e24F212A962"

payload = {}
headers = {
  'Authorization': 'Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU....'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)


```
```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://dev-api.waas.myabcwallet.com/wapi/v2/nft/contract?ca=0xb6f0b37c4f9a7a0b8c11e86e703cd0c498eb3630&chainId=137&eoa=0xcAcCFD4b61823BC105A7354C2afc1e24F212A962',
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
> 성공 시 200 status 반환

```json
{
    "symbol": "ABC",
    "name": "ABC Edition",
    "totalSupply": "",
    "balanceOf": "1"
}
```

### HTTP Request

`GET https://dev-api.waas.myabcwallet.com/wapi/v2/nft/contract`

### Request Header

Name | Require | Description
--------- | ------- | -----------
Authorization | true | 인증 JWT

### Query Parameters

Parameter | Require | Description
--------- | ------- | -----------
chainId | true | 10진수 Chain ID
ca | true | 컨트랙트 주소
eoa | false | owner 주소

### Response Body

Field | Type | Description
--------- | ------- | -----------
symbol | String | 토큰 symbol
name | String | 컨트랙트 이름
totalSupply | String | 총 발행량
balanceOf | String | 내 보유 토큰 개수

## NFT 전송 권한 조회
```shell
curl --location 'https://dev-api.waas.myabcwallet.com/wapi/v2/nft/approved?ca=0xb6f0b37c4f9a7a0b8c11e86e703cd0c498eb3630&chainId=137&eoa=0xcAcCFD4b61823BC105A7354C2afc1e24F212A962' \
--header 'Authorization: Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZ....'
```
```python
import requests

url = "https://dev-api.waas.myabcwallet.com/wapi/v2/nft/approved?ca=0xb6f0b37c4f9a7a0b8c11e86e703cd0c498eb3630&chainId=137&eoa=0xcAcCFD4b61823BC105A7354C2afc1e24F212A962"

payload = {}
headers = {
  'Authorization': 'Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU....'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)


```
```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://dev-api.waas.myabcwallet.com/wapi/v2/nft/approved?ca=0xb6f0b37c4f9a7a0b8c11e86e703cd0c498eb3630&chainId=137&eoa=0xcAcCFD4b61823BC105A7354C2afc1e24F212A962',
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
> 성공 시 200 status 반환

```json
{
  "result":"0x0000000000000000000000000000000000000000"
}
```

### HTTP Request

`GET https://dev-api.waas.myabcwallet.com/wapi/v2/nft/approved`

### Request Header

Name | Require | Description
--------- | ------- | -----------
Authorization | true | 인증 JWT

### Query Parameters
Parameter | Require | Description
--------- | ------- | -----------
chainId | true | 10진수 Chain ID
ca | true | 컨트랙트 주소
tokenId | true | 토큰 ID

## 전체 NFT 전송 권한 조회
```shell
curl --location 'https://dev-api.waas.myabcwallet.com/wapi/v2/nft/approved-for-all?ca=0xb6f0b37c4f9a7a0b8c11e86e703cd0c498eb3630&chainId=137&owner=0xcAcCFD4b61823BC105A7354C2afc1e24F212A962&operator=0xAD2596F9506309EA64E81605Aaa4E898134AC1f2' \
--header 'Authorization: Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZyI6IkVTM...'
```
```python
import requests

url = "https://dev-api.waas.myabcwallet.com/wapi/v2/nft/approved-for-all?ca=0xb6f0b37c4f9a7a0b8c11e86e703cd0c498eb3630&chainId=137&owner=0xcAcCFD4b61823BC105A7354C2afc1e24F212A962&operator=0xAD2596F9506309EA64E81605Aaa4E898134AC1f2"

payload = {}
headers = {
  'Authorization': 'Bearer eyJraWQiOiIyNCIsInR5cCI6Ikp...'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```
```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://dev-api.waas.myabcwallet.com/wapi/v2/nft/approved-for-all?ca=0xb6f0b37c4f9a7a0b8c11e86e703cd0c498eb3630&chainId=137&owner=0xcAcCFD4b61823BC105A7354C2afc1e24F212A962&operator=0xAD2596F9506309EA64E81605Aaa4E898134AC1f2',
  headers: { 
    'Authorization': 'Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZyI6IkVT...'
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
> 성공 시 200 status 반환

```json
{
  "result":false
}
```

### HTTP Request

`GET https://dev-api.waas.myabcwallet.com/wapi/v2/nft/approved-for-all`

### Request Header

Name | Require | Description
--------- | ------- | -----------
Authorization | true | 인증 JWT

### Query Parameters

Parameter | Require | Description
--------- | ------- | -----------
chainId | true | 10진수 Chain ID
ca | true | 컨트랙트 주소
owner | true | 토큰 소유주 주소
operator | true | 대행자 주소


## NFT 전송 권한 부여 데이터 생성
```shell
curl --location 'https://dev-api.waas.myabcwallet.com/wapi/v2/nft/approve-data?tokenId=20&chainId=137&approved=0xcAcCFD4b61823BC105A7354C2afc1e24F212A962' \
--header 'Authorization: Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZyI6IkVTM...'
```
```python
import requests

url = "https://dev-api.waas.myabcwallet.com/wapi/v2/nft/approve-data?tokenId=20&chainId=137&approved=0xcAcCFD4b61823BC105A7354C2afc1e24F212A962"

payload = {}
headers = {
  'Authorization': 'Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU...'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```
```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://dev-api.waas.myabcwallet.com/wapi/v2/nft/approve-data?tokenId=20&chainId=137&approved=0xcAcCFD4b61823BC105A7354C2afc1e24F212A962',
  headers: { 
    'Authorization': 'Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZyI6IkVT...'
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
> 성공 시 200 status 반환

```json
{
  "result":"0x095ea7b3000000000000000000000000caccfd4b61823bc105a7354c2afc1e24f212a9620000000000000000000000000000000000000000000000000000000000000014"
}
```

### HTTP Request

`GET https://dev-api.waas.myabcwallet.com/wapi/v2/nft/approve-data`

### Request Header

Name | Require | Description
--------- | ------- | -----------
Authorization | true | 인증 JWT

### Query Parameters

Parameter | Require | Description
--------- | ------- | -----------
chainId | true | 10진수 Chain ID
tokenId | true | 토큰 ID
approved | true | 대행자 주소

## 전체 NFT 전송 권한 부여 데이터 생성
```shell
curl --location 'https://dev-wapi.service.myabcwallet.com/v2/nft/approval-for-all-data?operator=0xb6f0b37c4f9a7a0b8c11e86e703cd0c498eb3630&chainId=137&approved=true' \
--header 'Authorization: Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImF...'
```
```python
import requests

url = "https://dev-wapi.service.myabcwallet.com/v2/nft/approval-for-all-data?operator=0xb6f0b37c4f9a7a0b8c11e86e703cd0c498eb3630&chainId=137&approved=true"

payload = {}
headers = {
  'Authorization': 'Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZyI6IkVTMj...'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```
```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://dev-api.waas.myabcwallet.com/wapi/v2/nft/approval-for-all-data?operator=0xb6f0b37c4f9a7a0b8c11e86e703cd0c498eb3630&chainId=137&approved=true',
  headers: { 
    'Authorization': 'Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZyI6IkVTM...'
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
> 성공 시 200 status 반환

```json
{
  "result":"0xa22cb465000000000000000000000000b6f0b37c4f9a7a0b8c11e86e703cd0c498eb36300000000000000000000000000000000000000000000000000000000000000001"
}
```

### HTTP Request

`GET https://dev-api.waas.myabcwallet.com/wapi/v2/nft/approval-for-all-data`

### Request Header

Name | Require | Description
--------- | ------- | -----------
Authorization | true | 인증 JWT

### Query Parameters

Parameter | Require | Description
--------- | ------- | -----------
chainId | true | 10진수 Chain ID
operator | true | 대행자 주소
approved | true | boolean

## NFT 전송 데이터 생성
```shell
curl --location 'https://dev-api.waas.myabcwallet.com/wapi/v2/nft/transfer-from-data?chainId=137&from=0xcAcCFD4b61823BC105A7354C2afc1e24F212A962&to=0xcAcCFD4b61823BC105A7354C2afc1e24F212A962&tokenId=20&data=' \
--header 'Authorization: Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZyI6IkVTM...'
```
```python
import requests

url = "https://dev-api.waas.myabcwallet.com/wapi/v2/nft/transfer-from-data?chainId=137&from=0xcAcCFD4b61823BC105A7354C2afc1e24F212A962&to=0xcAcCFD4b61823BC105A7354C2afc1e24F212A962&tokenId=20&data="

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
  url: 'https://dev-api.waas.myabcwallet.com/wapi/v2/nft/transfer-from-data?chainId=137&from=0xcAcCFD4b61823BC105A7354C2afc1e24F212A962&to=0xcAcCFD4b61823BC105A7354C2afc1e24F212A962&tokenId=20&data=',
  headers: { 
    'Authorization': 'Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZyI....'
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
> 성공 시 200 status 반환

```json
{
  "result":"0x42842e0e000000000000000000000000caccfd4b61823bc105a7354c2afc1e24f212a962000000000000000000000000caccfd4b61823bc105a7354c2afc1e24f212a9620000000000000000000000000000000000000000000000000000000000000014"
}
```

### HTTP Request

`GET https://dev-api.waas.myabcwallet.com/wapi/v2/nft/transfer-from-data`

### Request Header

Name | Require | Description
--------- | ------- | -----------
Authorization | true | 인증 JWT

### Query Parameters

Parameter | Require | Description
--------- | ------- | -----------
chainId | true | 10진수 Chain ID
from | true | 토큰 소유자 주소
to | true | 수신자 주소
tokenId | true | 전달하고자 하는 token id
data | false |