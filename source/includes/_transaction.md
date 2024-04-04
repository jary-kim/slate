
# Transaction
## 트랜잭션 전송
```shell
curl --location 'https://dev-api.waas.myabcwallet.com/wapi/v2/transactions/raw-tx/send' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--header 'Authorization: Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2In0.eyJzdWIiOiJiMjRjODM3YTZlOWU0M2M4YWVlNGM0MjM4YmNjMzY2MCI....' \
--data-urlencode 'signedSerializeTx=0xad6911cd120e5a2f2cd3529d0293d444bd7db09917df2821ba8fc31e079260245b69f89bf381989bdb1e520002fc5b94a24d969b74a08ce9ea860f46939daa011b' \
--data-urlencode 'chainId=8217'
```
```python
import requests

url = "https://dev-api.waas.myabcwallet.com/wapi/v2/transactions/raw-tx/send"

payload = 'signedSerializeTx=0x6a627842000000000000000000000000c18541c89f542e401ad0cc5c1e81fca220f3c537&chainId=8217'
headers = {
  'Content-Type': 'application/x-www-form-urlencoded',
  'Authorization': 'Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2In0.eyJzdWIiOiJiMjRjODM3Y....'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```
```javascript
const axios = require('axios');
const qs = require('qs');
let data = qs.stringify({
  'signedSerializeTx': '0xad6911cd120e5a2f2cd3529d0293d444bd7db09917df2821ba8fc31e079260245b69f89bf381989bdb1e520002fc5b94a24d969b74a08ce9ea860f46939daa011b',
  'chainId': '8217'
});

let config = {
  method: 'post',
  maxBodyLength: Infinity,
  url: 'https://dev-api.waas.myabcwallet.com/wapi/v2/transactions/raw-tx/send',
  headers: { 
    'Content-Type': 'application/x-www-form-urlencoded', 
    'Authorization': 'Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2In0.eyJzdWIiOiJiMjRjODM3YTZlOWU0M2M4YWVlNGM....'
  },
  data : data
};

axios.request(config)
.then((response) => {
  console.log(JSON.stringify(response.data));
})
.catch((error) => {
  console.log(error);
});
```
> 성공 시 응답메시지에 receipt hash를 반환

```json
{
  "result":"0x02f86f8301388180847735940084773594008401312d0094caccfd4b61823bc105a7354c2afc1e24f212a9628080c080a08b0418e20359c5f3d5fbfdc0f8c71bf01d9a24ff84b58a86f0a06fc641490496a0607bd39f35bb48964fbe401fce252b8b9aa3d69c9f02db3b79889d591a5ac3b2"
}
```

### HTTP Request

`POST https://dev-api.waas.myabcwallet.com/wapi/v2/transactions/raw-tx/send`

### Request Header

Name | Require | Description
--------- | ------- | -----------
Authorization | true | 인증 JWT
Content-Type | true | application/x-www-form-urlencoded

### Request Body

Parameter | Require | Description
--------- | ------- | -----------
chainId | true | 10진수 Chain ID
signedSerializeTx| true | 직렬화된 Sign 트랜잭션 문자열


## 트랜잭션 목록 조회 (Deprecated)

```shell
curl --location 'https://dev-api.waas.myabcwallet.com/wapi/v2/transactions?chainId=8217&address=0xcAcCFD4b61823BC105A7354C2afc1e24F212A962&cursor=&size=5&fromBlock=&toBlock=&toDate=&fromDate=' \
--header 'Authorization: Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCI....'
```
```python
import requests

url = "https://dev-api.waas.myabcwallet.com/wapi/v2/transactions?chainId=8217&address=0xcAcCFD4b61823BC105A7354C2afc1e24F212A962&cursor=&size=5&fromBlock=&toBlock=&toDate=&fromDate="

payload = {}
headers = {
  'Authorization': 'Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCI....'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```
```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://dev-api.waas.myabcwallet.com/wapi/v2/transactions?chainId=8217&address=0xcAcCFD4b61823BC105A7354C2afc1e24F212A962&cursor=&size=5&fromBlock=&toBlock=&toDate=&fromDate=',
  headers: { 
    'Authorization': 'Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFs....'
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
    "cursor": "0J4G9pd0W6zQkvGl5gOJBA8XwxY13NaxWPq9vK7r8pVzg0EDm2ln6POqLKOupdd7tPkrAkXhLNQER1eYoQMJZkwOG3Ab56LdBX4Kb9NeLP4r72EVoDqmZaMpd386YArW",
    "list": [
        {
            "from": "0xcaccfd4b61823bc105a7354c2afc1e24f212a962",
            "to": "0xd0b04a7573eebafd4c10c9fa7693cae6d1a7e445",
            "value": "0x4563918244f40000",
            "blockNumber": "142819204",
            "status": "1",
            "timestamp": "1704798245",
            "transactionIndex": "25",
            "transactionHash": "0x605019573c3cf27e5071df99c93f70a1e25734cba87869ba0dc7aa2e8451ad85",
            "contractAddress": null,
            "klaytnTransferType": "klay",
            "feePayer": "",
            "feeRatio": "0",
            "fee": "0x1dd7c1681d000",
            "gas": null,
            "gasPrice": null,
            "receipt_cumulative_gas_used": null,
            "receipt_gas_used": null,
            "nonce": null,
            "internal_transactions": null
        },
        {
            "from": "0xcaccfd4b61823bc105a7354c2afc1e24f212a962",
            "to": "0xace7d5bc035e13c8059e8993fde6f3d6caddfba8",
            "value": "0x4563918244f40000",
            "blockNumber": "142819175",
            "status": "1",
            "timestamp": "1704798216",
            "transactionIndex": "2",
            "transactionHash": "0x2dfc63e3b3551d9273ce0821e5900972d647779b57bef2734ee2e1e110cce804",
            "contractAddress": null,
            "klaytnTransferType": "klay",
            "feePayer": "",
            "feeRatio": "0",
            "fee": "0x1dd7c1681d000",
            "gas": null,
            "gasPrice": null,
            "receipt_cumulative_gas_used": null,
            "receipt_gas_used": null,
            "nonce": null,
            "internal_transactions": null
        },
        {
            "from": "0x6947a8844fcd4af6003b4549f2dd0bfa0b9f36d3",
            "to": "0xcaccfd4b61823bc105a7354c2afc1e24f212a962",
            "value": "0x1",
            "blockNumber": "140981007",
            "status": "1",
            "timestamp": "1702958975",
            "transactionIndex": "182",
            "transactionHash": "0xca32f7b07950cbbd06aca6413087aad002da9a31b59881c5be233e217f7ad63c",
            "contractAddress": null,
            "klaytnTransferType": "klay",
            "feePayer": "",
            "feeRatio": "0",
            "fee": "0x1dd7c1681d000",
            "gas": null,
            "gasPrice": null,
            "receipt_cumulative_gas_used": null,
            "receipt_gas_used": null,
            "nonce": null,
            "internal_transactions": null
        },
        {
            "from": "0xcaccfd4b61823bc105a7354c2afc1e24f212a962",
            "to": "0x6947a8844fcd4af6003b4549f2dd0bfa0b9f36d3",
            "value": "0x16345785d8a0000",
            "blockNumber": "140980992",
            "status": "1",
            "timestamp": "1702958960",
            "transactionIndex": "21",
            "transactionHash": "0xd30e603b377984a4211c9c4cbadb905d53c024f5f9c9223826d9da90430bc5ba",
            "contractAddress": null,
            "klaytnTransferType": "klay",
            "feePayer": "",
            "feeRatio": "0",
            "fee": "0x1dd7c1681d000",
            "gas": null,
            "gasPrice": null,
            "receipt_cumulative_gas_used": null,
            "receipt_gas_used": null,
            "nonce": null,
            "internal_transactions": null
        },
        {
            "from": "0x0000000000000000000000000000000000000000",
            "to": "0xcaccfd4b61823bc105a7354c2afc1e24f212a962",
            "value": "0x0",
            "blockNumber": "139779292",
            "status": null,
            "timestamp": "1701755350",
            "transactionIndex": null,
            "transactionHash": "0xe5d6985ee8e7812a7d0536d3a5a6ba88f7e6369367ce575dc9685d7625494e3f",
            "contractAddress": "0x19e8ed97647cb1c626068da6506dd642966243df",
            "klaytnTransferType": "nft",
            "feePayer": "",
            "feeRatio": "0",
            "fee": "0x1199d193257000",
            "gas": null,
            "gasPrice": null,
            "receipt_cumulative_gas_used": null,
            "receipt_gas_used": null,
            "nonce": null,
            "internal_transactions": null
        }
    ]
}
```

### HTTP Request

`GET https://dev-api.waas.myabcwallet.com/wapi/v2/transactions`

### Request Header

Name | Require | Value
--------- | ------- | -----------
Authorization | true | 인증 JWT

### Query Parameters

Parameter | Require | Description
--------- | ------- | -----------
chainId | true | 10진수 Chain ID
address | true | 검색 대상 주소
cursor | false | 필터 offset
size | false | Default: 100, Max: 1000
fromBlock | false |
toBlock | false |
fromDate | false | yyyy-MM-dd kk:mm:ss
toDate | false | yyyy-MM-dd kk:mm:ss

### Response Body

Field | Type | Description
--------- | ------- | -----------
from | String | 
to | String | 
value | String | 
blockNumber | String | 
status | String | 
timestamp | String | 
transactionIndex | String | 
transactionHash | String | 
contractAddress | String | 
klaytnTransferType | ["klay", "ft", "nft","mt"] | (Klaytn 한정)
feePayer | String | 수수료 대납 주소(Klaytn 한정)
feeRatio | String | 수수료 대납 비율(Klaytn 한정)
fee | String | 수수료(Klaytn 한정)
gas | String | Klaytn 제외
gasPrice | String | Klaytn 제외
receipt_cumlative_gas_used | String | Klaytn 제외
receipt_gas_used | String | Klaytn 제외
nonce | String | Klaytn 제외
internal_transactions | InternalTransaction | Klaytn 제외

#### Schema
InternalTransaction
Field | Type | Description
--------- | ------- | -----------
transaction_hash | String | 
block_hash | String | 
block_number | String | 
type | String | 
from | String | 
to | String | 
value | String | 
gas | String | 
gas_used | String | 
input | String | 
output | String | 

<aside class="notice">
Block 범위 필터와 Date 범위 필터는 함께 사용할 수 없습니다.
</aside>

## Block 조회
```shell
curl --location 'https://dev-api.waas.myabcwallet.com/wapi/v2/transactions/v2/transactions/block?blockNumber=1453784&chainId=1' \
--header 'Authorization: Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCI....'
```
```python
import requests

url = "https://dev-api.waas.myabcwallet.com/wapi/v2/transactions/block?blockNumber=1453784&chainId=1"

payload = {}
headers = {
  'Authorization': 'Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCI....'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```
```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://dev-api.waas.myabcwallet.com/wapi/v2/transactions/block?blockNumber=1453784&chainId=1',
  headers: { 
    'Authorization': 'Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFs....'
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
    "hash": "0x025a2d9392fe302e28cb47ebf955461d143f8715341b1018ec56da99cc9467d7",
    "parentHash": "0x3625e27e3ec985058c3e3a0bc2861c24264bbedba8c20ed444204aa1d678ec01",
    "sha3Uncles": "0x1dcc4de8dec75d7aab85b567b6ccd41ad312451b948a7413f0a142fd40d49347",
    "miner": "0x31d7dccbe7b48bacbd4f99bfffa00fcd27c1434e",
    "stateRoot": "0x55784b01d947b729650561e5d48506aa21df2d015e8ac548e772a7a881a9f832",
    "transactionsRoot": "0x8301724965952fa9abff1d84cecaf3a8cc08afcaa8577036c51e0e87df9e6648",
    "receiptsRoot": "0x16546198762ad6ad22fdf6f7f7fd222376eb0cfdf410881807af4cd2b6106d4f",
    "number": "0x162ed8",
    "gasUsed": "0x33450",
    "gasLimit": "0x47e7c4",
    "extraData": "0xd783010305844765746887676f312e352e31856c696e7578",
    "logsBloom": "0x00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",
    "timestamp": "0x5729881b",
    "difficulty": "0x1ecf996105e1",
    "totalDifficulty": "0xefe898da29de6f85",
    "sealFields": [],
    "uncles": [],
    "transactions": [
        "0xa9a55b90e44fa15feec0e5ba3d0dcec882ed22f0dc935c68345f0200e95b3dc3",
        "0x3af0810463ba8ed79c5dde4e20b4fc82af9c78a6dfdb1c7871b6123edf9f252b",
        "0xbc5f4077bc9e3548d256cb8c2cc7482095e05857e6330917ffdba054a05c3265",
        "0xcdd01f244595cfb6ff092e85f1a6bb0afb327a018c57453258a28edaecbcd060",
        "0x3b2616e381230676dd21cbe9316cfc40ef7045b2b766253624cfaf2c73aaa030",
        "0xd4da5a4a92e11bede7e2438c20bba498d1a3f5d0492ba812a3f747cc477997c6",
        "0x9087011789ed7eff26200fabb00ead5370f03ec45233bbd29b15183d69be132e",
        "0xd6d6b9638e207aca18ef5150f4efc75b509e2fbffe1be6bc862ce32f9ae78d47",
        "0x9ae11cc1fb54df84761aa3684ed6fcb486aaa289067d3b302e0f479aad49fec5",
        "0xeee1c00b5835cf0719bc91bebc3a63e8bf50695b1dbbd0a9ac405eafd197ddbe"
    ],
    "size": "0x68d",
    "mixHash": "0x7c921b6399f84c398211d9f87283217918347d2002003961952e67353ca4a8b4",
    "nonce": "0x61a8d77d3e6efa6d",
    "baseFeePerGas": null
}
```

### HTTP Request

`GET https://dev-api.waas.myabcwallet.com/wapi/v2/transactions/block`

### Request Header

Name | Require | Value
--------- | ------- | -----------
Authorization | true | 인증 JWT

### Query Parameters

Parameter | Require | Description
--------- | ------- | -----------
chainId | true | 10진수 Chain ID
blockNumber | true | 조회할 blockNumber

## Receipt 조회
```shell
curl --location 'https://dev-api.waas.myabcwallet.com/wapi/v2/transactions/receipt?hash=0xa9a55b90e44fa15feec0e5ba3d0dcec882ed22f0dc935c68345f0200e95b3dc3&chainId=1' \
--header 'Authorization: Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCI....'
```
```python
import requests

url = "https://dev-api.waas.myabcwallet.com/wapi/v2/transactions/receipt?hash=0xa9a55b90e44fa15feec0e5ba3d0dcec882ed22f0dc935c68345f0200e95b3dc3&chainId=1"

payload = {}
headers = {
  'Authorization': 'Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCI....'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```
```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://dev-api.waas.myabcwallet.com/wapi/v2/transactions/receipt?hash=0xa9a55b90e44fa15feec0e5ba3d0dcec882ed22f0dc935c68345f0200e95b3dc3&chainId=1',
  headers: { 
    'Authorization': 'Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFs....'
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
    "transactionHash": "0xa9a55b90e44fa15feec0e5ba3d0dcec882ed22f0dc935c68345f0200e95b3dc3",
    "transactionIndex": "0x0",
    "blockHash": "0x025a2d9392fe302e28cb47ebf955461d143f8715341b1018ec56da99cc9467d7",
    "blockNumber": "0x162ed8",
    "from": "0x32be343b94f860124dc4fee278fdcbd38c102d88",
    "to": "0x17d294f910c9891ee648575b1caff2d59bcf2c1d",
    "cumulativeGasUsed": "0x5208",
    "gasUsed": "0x5208",
    "contractAddress": null,
    "logs": [],
    "status": null,
    "logsBloom": "0x00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000",
    "type": "0x0",
    "effectiveGasPrice": "0x6fc23ac00"
}
```

### HTTP Request

`GET https://dev-api.waas.myabcwallet.com/wapi/v2/transactions/receipt`

### Request Header

Name | Require | Value
--------- | ------- | -----------
Authorization | true | 인증 JWT

### Query Parameters

Parameter | Require | Description
--------- | ------- | -----------
chainId | true | 10진수 Chain ID
hash | true | 조회할 trasaction hash

## Transaction count
```shell
curl --location 'https://dev-api.waas.myabcwallet.com/wapi/v2/transactions/count?address=0xd4f15e5A668551953b06ee07D663F5FE3338b0ef&chainId=1&block=1435702' \
--header 'Authorization: Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCI....'
```
```python
import requests

url = "https://dev-api.waas.myabcwallet.com/wapi/v2/transactions/count?address=0xd4f15e5A668551953b06ee07D663F5FE3338b0ef&chainId=1&block=1435702"

payload = {}
headers = {
  'Authorization': 'Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCI....'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```
```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://dev-api.waas.myabcwallet.com/wapi/v2/transactions/count?address=0xd4f15e5A668551953b06ee07D663F5FE3338b0ef&chainId=1&block=1435702',
  headers: { 
    'Authorization': 'Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFs....'
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
    "result": "4"
}
```

### HTTP Request

`GET https://dev-api.waas.myabcwallet.com/wapi/v2/transactions/count`

### Request Header

Name | Require | Value
--------- | ------- | -----------
Authorization | true | 인증 JWT

### Query Parameters

Parameter | Require | Description
--------- | ------- | -----------
chainId | true | 10진수 Chain ID
address | true | 조회할 지갑 주소
block | true | 입력한 blockNumber 이전까지 생성한 transaction의 개수

## transaction hash를 통한 트랜잭션 정보 조회
```shell
curl --location 'https://dev-api.waas.myabcwallet.com/wapi/v2/transactions/hash?hash=0x2b28df4fa5ffe35c39c97267282b3a42beaac5feb49e9e92e48fb97e91510ce2&chainId=1' \
--header 'Authorization: Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCI....'
```
```python
import requests

url = "https://dev-api.waas.myabcwallet.com/wapi/v2/transactions/hash?hash=0x2b28df4fa5ffe35c39c97267282b3a42beaac5feb49e9e92e48fb97e91510ce2&chainId=1"

payload = {}
headers = {
  'Authorization': 'Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCI....'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```
```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://dev-api.waas.myabcwallet.com/wapi/v2/transactions/hash?hash=0x2b28df4fa5ffe35c39c97267282b3a42beaac5feb49e9e92e48fb97e91510ce2&chainId=1',
  headers: { 
    'Authorization': 'Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFs....'
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
    "hash": "0x2b28df4fa5ffe35c39c97267282b3a42beaac5feb49e9e92e48fb97e91510ce2",
    "nonce": "0x5",
    "blockHash": "0x6a374a6b49e62c6d95e7aecf6e31bb23aa5c231bda0d63fae72fa7d3ed223626",
    "blockNumber": "0x163fe2",
    "transactionIndex": "0x0",
    "from": "0xd4f15e5a668551953b06ee07d663f5fe3338b0ef",
    "to": "0xbb9bc244d798123fde783fcc1c72d3bb8c189413",
    "value": "0x1b1ae4d6e2ef500000",
    "gasPrice": "0x4a817c800",
    "gas": "0x232db",
    "input": "0x",
    "v": "0x1c",
    "r": "0xac9b2c14fcdd41d7e977424fbc457ffc603792bc2ac4e34d35983a3dc6626f3d",
    "s": "0x17b82069e5be34359881290ce6d339421a3907366596c063996e167ff029c7ae",
    "type": "0x0",
    "chainId": null
}
```

### HTTP Request

`GET https://dev-api.waas.myabcwallet.com/wapi/v2/transactions/hash`

### Request Header

Name | Require | Value
--------- | ------- | -----------
Authorization | true | 인증 JWT

### Query Parameters

Parameter | Require | Description
--------- | ------- | -----------
chainId | true | 10진수 Chain ID
hash | true | 조회할 trasaction hash