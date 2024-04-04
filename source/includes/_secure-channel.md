
# Secure-Channel
## 보안 채널 생성

성공 시 응답메시지에 요청에 사용된 평문의 암호문과 생성된 Secure-Channel ID를 반환합니다.

WaaS 서버 측 ECPublicKey (비 압축) 와 클라이언트의 ECPrivateKey 를 ECDH (secp256r1) 연산을 통해 32바이트의 shared secret 을 생성할 수 있다.</br>
secret 32바이트 중 앞의 16바이트는 key, 뒤의 16바이트는 iv 로 AES 복호화를 수행합니다.</br>(AES/CBC/PKCS7Padding 사용)

복호화 결과가 요청 시 보낸 평문과 일치하다면 채널이 정상적으로 생성된 것 입니다.

```shell
curl --location 'https://dev-api.id.myabcwallet.com/secure/channel/create' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--data-urlencode 'pubkey=0488864e149733b5887193fc207b8a4a3d519fd4b9d83f596e6b226095478fecfdc330dbbb73656d82885ac0f1ee944767023eb698f1d7789a56dae66d0946c309' \
--data-urlencode 'plain=test'
```
```python
import requests

url = "https://dev-api.id.myabcwallet.com/secure/channel/create"

payload = 'pubkey=0488864e149733b5887193fc207b8a4a3d519fd4b9d83f596e6b226095478fecfdc330dbbb73656d82885ac0f1ee944767023eb698f1d7789a56dae66d0946c309&plain=test'
headers = {
  'Content-Type': 'application/x-www-form-urlencoded'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```
```javascript
const axios = require('axios');
const qs = require('qs');
let data = qs.stringify({
  'pubkey': '0488864e149733b5887193fc207b8a4a3d519fd4b9d83f596e6b226095478fecfdc330dbbb73656d82885ac0f1ee944767023eb698f1d7789a56dae66d0946c309',
  'plain': 'test' 
});

let config = {
  method: 'post',
  maxBodyLength: Infinity,
  url: 'https://dev-api.id.myabcwallet.com/secure/channel/create',
  headers: { 
    'Content-Type': 'application/x-www-form-urlencoded'
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
  "channelid":"2e05fdf0b2e240aba81ec46f494e792f",
  "publickey":"04f2c7f6b36e7165c26aa6ee0eb3dd4f136c6ddb9a7c14fb83f66da07353ff2625dd0414bcc253f491eb8b5dc21beb630fe1853874f2e4463d5a8ca9762d71af5b",
  "encrypted":"dg1LZUUwWbu2Lw7i6db4Cw=="
}
```

### HTTP Request

`GET https://dev-api.id.myabcwallet.com/secure/channel/create`

### Request Header

Name | Require | Value
--------- | ------- | -----------
Content-Type | true | application/x-www-form-urlencoded

### Request Body

Parameter | Require | Description
--------- | ------- | -----------
pubkey | true | 요청자의 공개키 (ECPublicKey : secp256r1) 04(prefix) + x + y 비 압축 형태
plain | true | 복호화 검증을 위한 임시 문자열

### Response Body

Field | Type | Description
--------- | ------- | -----------
channelid | String | 보안 채널 ID
publickey | Integer | Server public key
encrypted | String | 요청에 사용된 plain 암호문(복호화 검증에 사용)

<aside class="notice">
생성된 보안 채널의 유효 시간은 1시간 입니다.
</aside>

<aside class="notice">
일부 API에서 암호화 대상이 존재하는 경우, 보안 채널 생성 후 shared secret 으로 암호화 대상 원문을 암호화해야 합니다.</br>
암호화 대상을 포함한 API를 호출할 시 보안 채널 생성 후 응답으로 반환된 channelid를 HTTP 요청 헤더 <code>Secure-Channel</code>에 추가해야 합니다.
</aside>

<aside class="notice">
ABC 측에서 클라이언트 개발 편의를 위해 Javascript 용 Util 라이브러리를 제공하고 있습니다. 
라이브러리 제공을 위해서는 ABC 측에 문의를 통하여 Key 발급과 가이드를 받을 수 있습니다.
</aside>

<aside class="warning">
요청에 사용되는 plain은 채널 생성 확인 여부를 위한 임시 문자열을 사용합니다.
암호화 대상 원문을 사용해서는 안 됩니다.
</aside>