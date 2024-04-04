
# Sign
## Sign (Deprecated)

성공 시 응답메시지에 서명된 raw transaction을 반환.

```shell
curl --location 'https://dev-api.waas.myabcwallet.com/wapi/v2/sign' \
--header 'Secure-Channel: 037e76bb09e6499f9931ccdda349c95d' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--header 'Authorization: Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2In0.eyJzdWIiOiJiMjRjODM3YTZlOWU0M2M4YWVlNGM0MjM4YmNjMzY2MCIsImF1Z....' \
--data-urlencode 'from=0xbE616d5b24903efc58149f3c7511FeC2085c176e' \
--data-urlencode 'to=0xbE616d5b24903efc58149f3c7511FeC2085c176e' \
--data-urlencode 'value=0x0' \
--data-urlencode 'nonce=100' \
--data-urlencode 'chainId=1' \
--data-urlencode 'encryptDevicePassword=ukf9SrDdv4AgpSzU8SO2C7gC1f4v5/pa/Zuow1VLQaK3raQEbul3C5LHBpaum+Og' \
--data-urlencode 'pvencstr=wl5WmBJdq9NppL66wcSVVo4gjkv/J0Gx+lYt9....' \
--data-urlencode 'uid=d5b440b8-469b-4e16-8978-d78b73a09c4e' \
--data-urlencode 'wid=wONT9/oYetQAytC/KdF9Jw==' \
--data-urlencode 'sid=0xbE616d5b24903efc58149f3c7511FeC2085c176e' \
--data-urlencode 'type=EIP1559'
```
```python
import requests

url = "https://dev-api.waas.myabcwallet.com/wapi/v2/sign"

payload = 'from=0xbE616d5b24903efc58149f3c7511FeC2085c176e&to=0xbE616d5b24903efc58149f3c7511FeC2085c176e&value=0x0&nonce=100&chainId=1&encryptDevicePassword=ukf9SrDdv4AgpSzU8SO2C7gC1f4v5%2Fpa%2FZuow1VLQaK3raQEbul3C5LHBpaum%2BOg&pvencstr=wl5WmBJdq9NppL66wcSVVo4gjkv%2FJ0Gx%2BlYt9Pu64ZHL....&type=EIP1559'
headers = {
  'Secure-Channel': '037e76bb09e6499f9931ccdda349c95d',
  'Content-Type': 'application/x-www-form-urlencoded',
  'Authorization': 'Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2In0.eyJzdWIiOiJiMjRjODM3YTZlOWU0M2M4YWVlNGM0MjM4YmNjMzY2MCIsImF1ZCI6Imh0dHBzOi8vbXcubXlhYmN3YWxsZXQuY29tIiwiaXNzIjoiaHR0cHM6Ly9kZXYtYXBpLmlkLm15YWJjd2FsbGV0LmNvbS84MmJjNjllOTFiYTIyOWIzNzc5ODdjNTljNDQ1MTgyMiIsImV4cCI6MTczNTYyNjM4MCwiaWF0IjoxNzA0ODY3OTgwLCJqdGkiOiJhMTg2N2E5YTZhYjM0MzY5YTNmY2FkOWFlOTRhYjRhNCJ9.Uva2wVqBiZk1GnrAlqnKfg8_MUdFkk_Quj_5tQqTfi26UDSp83_3n6n16_KQuO4cwF9PYBvtaIsMMcfJeXHRTg'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)

```
```javascript
const axios = require('axios');
const qs = require('qs');
let data = qs.stringify({
  'from': '0xbE616d5b24903efc58149f3c7511FeC2085c176e',
  'to': '0xbE616d5b24903efc58149f3c7511FeC2085c176e',
  'value': '0x0',
  'nonce': '100',
  'chainId': '1',
  'encryptDevicePassword': 'ukf9SrDdv4AgpSzU8SO2C7gC1f4v5/pa/Zuow1VLQaK3raQEbul3C5LHBpaum+Og',
  'pvencstr': 'wl5WmBJdq9NppL66wcSVVo4gjkv/J0Gx+lYt9Pu64ZHLuEE+CurnRG....',
  'uid': 'd5b440b8-469b-4e16-8978-d78b73a09c4e',
  'wid': 'wONT9/oYetQAytC/KdF9Jw==',
  'sid': '0xbE616d5b24903efc58149f3c7511FeC2085c176e',
  'type': 'EIP1559' 
});

let config = {
  method: 'post',
  maxBodyLength: Infinity,
  url: 'https://dev-wapi.service.myabcwallet.com/v2/sign',
  headers: { 
    'Secure-Channel': '037e76bb09e6499f9931ccdda349c95d', 
    'Content-Type': 'application/x-www-form-urlencoded', 
    'Authorization': 'Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2In0.eyJzdWIiOiJiMjRjODM3YTZlOWU0M2M4YWVlNGM0MjM4Y....'
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
> 성공시 200 status 반환

```json
{
  "result": "0x02f86b01648405f5e10085078a0fd18782520894be616d5b24903efc58149f3c7511fec2085c176e8080c080a02a5a2dd122c13f58aa670e229745af21f9f74865d958718a4b72f9a5b649eb64a01f2770da7846b49c0951f1040060fe1896ed7dda049c01fc7ca70a427de04c60"
}
```

### HTTP Request

`POST https://dev-api.waas.myabcwallet.com/wapi/v2/sign`

### Request Header

Name | Require | Value
--------- | ------- | -----------
Authorization | true | 인증 JWT
Content-Type | true | application/x-www-form-urlencoded
Secure-Channel | true | 보안 채널 ID

### Request Body

Parameter | Require | Description
--------- | ------- | -----------
chainId | true | 10진수 Chain ID
encryptDevicePassword| true | MPC 지갑 생성에서 반환된 encryptDevicePassword(암호화 대상)
pvencstr | true | MPC 지갑 생성에서 반환된 pvencstr(암호화 대상)
uid| true | MPC 지갑 생성에서 반환된 uid
wid| true | 암호화 대상
sid| true | 사용자 EOA
to | true | target EOA or CA
from | false | 
value| false | 16진수 wei
data| false | Contract function call data
nonce| true | 10진수 사용자 거래 순번
gasPrice | false | 
gasLimit | false | 
maxPriorityFeePerGas | false | EIP-1559 type만 지원
maxFeePerGas | false | EIP-1559 type만 지원
type| true | [EIP1559, LEGACY, PERSONAL] 중 택 1

<aside class="notice">
암호화 대상은 필수로 보안 채널을 사용해 암호화되어야 합니다.</br>
암호화 방법은 <a href="/?#b7c2a75aca">보안 채널 생성</a>을 참조하여 암호화합니다.
</aside>

## SignTypedData (Deprecated)

성공 시 응답메시지에 서명된 raw transaction을 반환합니다.

```shell
curl --location 'https://dev-api.waas.myabcwallet.com/wapi/v2/sign/typed-data' \
--header 'Secure-Channel: 4c39ecdb9f844440976c97eb9c7c97e2' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--header 'Authorization: Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2In0.eyJzdWIiOiJiMjRjODM3YTZlOWU0M2M4YWVlNGM0MjM4YmNjMzY2MCI....' \
--data-urlencode 'messageJson={"types":{"EIP712Domain":[{"name":"name","type":"string"},{"name":"version","type":"string"},{"name":"chainId","type":"uint256"},{"name":"verifyingContract","type":"address"}],"Person":[{"name":"name","type":"string"},{"name":"wallet","type":"address"}],"Mail":[{"name":"from","type":"Person"},{"name":"to","type":"Person"},{"name":"contents","type":"string"}]},"primaryType":"Mail","domain":{"name":"EtherMail","version":"1","chainId":1,"verifyingContract":"0xCcCCccccCCCCcCCCCCCcCcCccCcCCCcCcccccccC"},"message":{"from":{"name":"Cow","wallet":"0xCD2a3d9F938E13CD947Ec05AbC7FE734Df8DD826"},"to":{"name":"Bob","wallet":"0xbBbBBBBbbBBBbbbBbbBbbbbBBbBbbbbBbBbbBBbB"},"contents":"Hello,Bob!"}}' \
--data-urlencode 'encryptDevicePassword=k2Jqy2fEc9irIcQDh0u5y40+mxl5n+k7AUrrZkcfhHw4+AfTdnj8Gd3i6V53qddH' \
--data-urlencode 'pvencstr=jOEJOknfhyBrC9egVumF7AWPsmZl....' \
--data-urlencode 'uid=d5b440b8-469b-4e16-8978-d78b73a09c4e' \
--data-urlencode 'wid=A7k/lWRrOhqFmBIOgl1X6w==' \
--data-urlencode 'sid=0xbE616d5b24903efc58149f3c7511FeC2085c176e' \
--data-urlencode 'chainId=8217' \
--data-urlencode 'version=v3'
```
```python
import requests

url = "https://dev-api.waas.myabcwallet.com/wapi/v2/sign/typed-data"

payload = 'messageJson=%7B%22types%22%3A%7B%22EIP712Domain%22%3A%5B%7B%22name%22%3A%22name%22%2C%22type%22%3A%22string%22%7D%2C%7B%22name%22%3A%22version%22%2C%22type%22%3A%22string%22%7D%2C%7B%22name%22%3A%22chainId%22%2C%22type%22%3A%22uint256%22%7D%2C%7B%22name%22%3A%22verifyingContract%22%2C%22type%22%3A%22address%22%7D%5D%2C%22Person%22%3A%5B%7B%22name%22%3A%22name%22%2C%22type%22%3A%22string%22%7D%2C%7B%22name%22%3A%22wallet%22%2C%22type%22%3A%22address%22%7D%5D%2C%22Mail%22%3A%5B%7B%22name%22%3A%22from%22%2C%22type%22%3A%22Person%22%7D%2C%7B%22name%22%3A%22to%22%2C%22type%22%3A%22Person%22%7D%2C%7B%22name%22%3A%22contents%22%2C%22type%22%3A%22string%22%7D%5D%7D%2C%22primaryType%22%3A%22Mail%22%2C%22domain%22%3A%7B%22name%22%3A%22EtherMail%22%2C%22version%22%3A%221%22%2C%22chainId%22%3A1%2C%22verifyingContract%22%3A%220xCcCCccccCCCCcCCCCCCcCcCccCcCCCcCcccccccC%22%7D%2C%22message%22%3A%7B%22from%22%3A%7B%22name%22%3A%22Cow%22%2C%22wallet%22%3A%220xCD2a3d9F938E13CD947Ec05AbC7FE734Df8DD826%22%7D%2C%22to%22%3A%7B%22name%22%3A%22Bob%22%2C%22wallet%22%3A%220xbBbBBBBbbBBBbbbBbbBbbbbBBbBbbbbBbBbbBBbB%22%7D%2C%22contents%22%3A%22Hello%2CBob!%22%7D%7D&encryptDevicePassword=k2Jqy2fEc9irIcQDh0u5y40%2Bmxl5n%2Bk7AUrrZkcfhHw4%2BAfTdnj8Gd3i6V53qddH&pvencstr=jOEJOknfhyBrC9egVumF7AWPsmZl%2FvSXvJw%2FtHU....&uid=d5b440b8-469b-4e16-8978-d78b73a09c4e&wid=A7k%2FlWRrOhqFmBIOgl1X6w%3D%3D&sid=0xbE616d5b24903efc58149f3c7511FeC2085c176e&chainId=8217&version=v3'
headers = {
  'Secure-Channel': '4c39ecdb9f844440976c97eb9c7c97e2',
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
  'messageJson': '{"types":{"EIP712Domain":[{"name":"name","type":"string"},{"name":"version","type":"string"},{"name":"chainId","type":"uint256"},{"name":"verifyingContract","type":"address"}],"Person":[{"name":"name","type":"string"},{"name":"wallet","type":"address"}],"Mail":[{"name":"from","type":"Person"},{"name":"to","type":"Person"},{"name":"contents","type":"string"}]},"primaryType":"Mail","domain":{"name":"EtherMail","version":"1","chainId":1,"verifyingContract":"0xCcCCccccCCCCcCCCCCCcCcCccCcCCCcCcccccccC"},"message":{"from":{"name":"Cow","wallet":"0xCD2a3d9F938E13CD947Ec05AbC7FE734Df8DD826"},"to":{"name":"Bob","wallet":"0xbBbBBBBbbBBBbbbBbbBbbbbBBbBbbbbBbBbbBBbB"},"contents":"Hello,Bob!"}}',
  'encryptDevicePassword': 'k2Jqy2fEc9irIcQDh0u5y40+mxl5n+k7AUrrZkcfhHw4+AfTdnj8Gd3i6V53qddH',
  'pvencstr': 'jOEJOknfhyBrC9egVumF7AWPsmZl/vSXvJw/tHUuYq9+IHV/VrNEfIXzcl2H....',
  'uid': 'd5b440b8-469b-4e16-8978-d78b73a09c4e',
  'wid': 'A7k/lWRrOhqFmBIOgl1X6w==',
  'sid': '0xbE616d5b24903efc58149f3c7511FeC2085c176e',
  'chainId': '8217',
  'version': 'v3' 
});

let config = {
  method: 'post',
  maxBodyLength: Infinity,
  url: 'https://dev-api.waas.myabcwallet.com/wapi/v2/sign/typed-data',
  headers: { 
    'Secure-Channel': '4c39ecdb9f844440976c97eb9c7c97e2', 
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
> 성공시 200 status 반환

```json
{
  "result": "0xad6911cd120e5a2f2cd3529d0293d444bd7db09917df2821ba8fc31e079260245b69f89bf381989bdb1e520002fc5b94a24d969b74a08ce9ea860f46939daa011b"
}
```

### HTTP Request

`POST https://dev-api.waas.myabcwallet.com/wapi/v2/sign/typed-data`

### Request Header

Name | Require | Description
--------- | ------- | -----------
Authorization | true | 인증 JWT
Content-Type | true | application/x-www-form-urlencoded
Secure-Channel | true | 보안 채널 ID

### Request Body

Parameter | Require | Description
--------- | ------- | -----------
chainId | true | 10진수 Chain ID
encryptDevicePassword| true | MPC 지갑 생성에서 반환된 encryptDevicePassword(암호화 대상)
pvencstr | true | MPC 지갑 생성에서 반환된 pvencstr(암호화 대상)
uid| true | MPC 지갑 생성에서 반환된 uid
wid| true | 암호화 대상
sid| true | 사용자 EOA
messageJson | true | json 문자열
type| true | [v3, v4] 중 택 1

<aside class="notice">
암호화 대상은 필수로 보안 채널을 사용해 암호화되어야 합니다.</br>
암호화 방법은 <a href="/?#b7c2a75aca">보안 채널 생성</a>을 참조하여 암호화합니다.
</aside>


## PreSign

Sign 호출에 필요한 데이터를 반환합니다.

```shell
TBD
```
```python
TBD
```
```javascript
TBD
```
> 성공시 200 status 반환

```json
{
  "mpcToken":"",
  "hash":"",
  "from":"",
  "to":"",
  "gasLimit":"",
  "value":"",
  "data":"",
  "nonce":"",
  "accessList":[],
  "maxPriorityFeePerGas":"",
  "maxFeePerGas":"",
  "chainId":""
}
```

### HTTP Request

`POST https://dev-api.waas.myabcwallet.com/wapi/v2/sign/pre`

### Request Header

Name | Require | Description
--------- | ------- | -----------
Authorization | true | 인증 JWT
Content-Type | true | application/x-www-form-urlencoded

### Request Body

Parameter | Require | Description
--------- | ------- | -----------
to | false | target EOA or CA
from | false | 
value| false | 16진수 wei
data| false | Contract function call data
nonce| false | 10진수 사용자 거래 순번
gasPrice | false | 
gasLimit | false | 
maxPriorityFeePerGas | false | EIP-1559 type만 지원
maxFeePerGas | false | EIP-1559 type만 지원
message| false | type: PERSONAL인 경우 사용
jsonMessage | false | type: SignTypedDataV3 또는 SignTypedDataV4인 경우 사용
chainId| false | 10진수 Chain ID
uid| true | 지갑 생성 시 반환된 uid
wid| true | 사용자 지갑 id
sid | true | 사용자 지갑 주소
type| true | [LEGACY, EIP1559, PERSONAL, SignTypedDataV3, SignTypedDataV4] 중 택 1

## PostSign

EIP1559, LEGACY Sign 이후 호출합니다.

```shell
TBD
```
```python
TBD
```
```javascript
TBD
```
> 성공시 200 status 반환

```json
{
  "result":""
}
```

### HTTP Request

`POST https://dev-api.waas.myabcwallet.com/wapi/v2/sign/post`

### Request Header

Name | Require | Description
--------- | ------- | -----------
Authorization | true | 인증 JWT
Content-Type | true | application/x-www-form-urlencoded

### Request Body

Parameter | Require | Description
--------- | ------- | -----------
to | true | target EOA or CA
from | true | 
value| false | 16진수 wei
data| false | Contract function call data
nonce| false | 10진수 사용자 거래 순번
gasPrice | false | 
gasLimit | false | 
maxPriorityFeePerGas | false | EIP-1559 type만 지원
maxFeePerGas | false | EIP-1559 type만 지원
message| false |
signatureJson | true |
hashHex | true |
chainId| true | 10진수 Chain ID
uid| true | 지갑 생성 시 반환된 uid
wid| true | 사용자 지갑 id
sid | true | 사용자 지갑 주소
type| true | [LEGACY, EIP1559] 중 택 1