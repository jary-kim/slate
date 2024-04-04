# MPC/Wallet
## 지갑 생성/복구 (Deprecated)

사용자 MPC 지갑을 생성합니다.</br>
이미 생성된 지갑이 존재하는 경우, 기존 지갑을 복구합니다.</br>

```python
import requests

url = "https://dev-api.waas.myabcwallet.com/wapi/v2/mpc/wallets"

payload = 'email=test_0%40myabcwallet.com&devicePassword=WeZFHUUwcU0LxTVCEJ5Suw%3D%3D'
headers = {
  'Secure-Channel': '037e76bb09e6499f9931ccdda349c95d',
  'Content-Type': 'application/x-www-form-urlencoded',
  'Authorization': 'Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2In0.eyJzdWIiOiJiMjRjODM3YTZlOWU0M2M4YWVlNGM0MjM4....'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

```shell
curl --location 'https://dev-api.waas.myabcwallet.com/wapi/v2/mpc/wallets' \
--header 'Secure-Channel: 037e76bb09e6499f9931ccdda349c95d' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--header 'Authorization: Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2In0.eyJzdWIiOiJiMjRjODM3YTZlOWU0M2M4YWVlNGM0MjM4YmNjMzY2MCIsImF1ZCI6Imh0dHBzOi8vbXcubXl....' \
--data-urlencode 'email=test@myabcwallet.com' \
--data-urlencode 'devicePassword=WeZFHUUwcU0LxTVCEJ5Suw=='
```

```javascript
const axios = require('axios');
const qs = require('qs');
let data = qs.stringify({
  'email': 'test_0@myabcwallet.com',
  'devicePassword': 'WeZFHUUwcU0LxTVCEJ5Suw==' 
});

let config = {
  method: 'post',
  maxBodyLength: Infinity,
  url: 'https://dev-api.waas.myabcwallet.com/wapi/v2/mpc/wallets',
  headers: { 
    'Secure-Channel': '037e76bb09e6499f9931ccdda349c95d', 
    'Content-Type': 'application/x-www-form-urlencoded', 
    'Authorization': 'Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2In0.eyJzdWIiOiJiMjRjODM3YTZlOWU0M2M4YWVlNGM0MjM4YmNjMzY2MCIsImF1ZCI6Imh0dHBzOi8vbXcubXl....'
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

> The above command returns JSON structured like this:

```json
{
    "uid": "d5b440b8-469b-4e16-8978-d78b73a09c4e",
    "wid": 6,
    "sid": "0xbE616d5b24903efc58149f3c7511FeC2085c176e",
    "pvencstr": "Uz/jFCF4xa9i6wyH0Z6xZ2cr....",
    "encryptDevicePassword": "g35AfeNKZvSdAy4Dbal+5...."
}
```

### HTTP Request

`POST https://dev-api.waas.myabcwallet.com/wapi/v2/mpc/wallets`

### Request Header

Name | Require | Description
--------- | ------- | -----------
Authorization | true | 인증 JWT
Content-Type | true | application/x-www-form-urlencoded
Secure-Channel | true | 보안 채널 ID

### Request Body

Parameter | Description
--------- | -----------
email | 사용자 이메일 주소
devicePassword | 암호화 대상

### Response Body

Field | Type | Description
--------- | ------- | -----------
uid | String | 사용자 uid
wid | Integer | 지갑 id
sid | String | 지갑 주소
pvencstr | String | Key Share
encryptDevicePassword | String | 암호화된 패스워드

<aside class="notice">
암호화 대상 필드는 필수로 보안 채널을 사용해 암호화되어야 합니다.</br>
암호화 방법은 <a href="/?#b7c2a75aca">보안 채널 생성</a>을 참조합니다.
</aside>

<aside class="warning">
지갑 생성 후 응답으로 반환된 pvenc와 devicepassword는 안전하게 관리되어야 하며, 이는 트랜잭션 서명에 사용됩니다.
</aside>

## 사용자 지갑 정보 조회

```python
import requests

url = "https://dev-api.waas.myabcwallet.com/wapi/v2/mpc/wallets/info"

payload = {}
headers = {
  'Authorization': 'Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2In0.eyJzdWIiOiJiMjRjODM3YTZlOWU0M2M4YWVlNGM0MjM4YmNjMzY2MCIsImF1ZCI6Im....'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)

```

```shell
curl --location 'https://dev-api.waas.myabcwallet.com/wapi/v2/mpc/wallets/info' \
--header 'Authorization: Bearer Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2In0.eyJzdWIiOiJiMjRjODM3YTZlOWU0M2M4YWVlNGM0MjM4YmNjMzY2MCIsImF1ZCI6Im....'
```

```javascript
const axios = require('axios');

let config = {
  method: 'get',
  maxBodyLength: Infinity,
  url: 'https://dev-api.waas.myabcwallet.com/wapi/v2/mpc/wallets/info',
  headers: { 
    'Authorization': 'Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2In0.eyJzdWIiOiJiMjRjODM3YTZlOWU0M2M4YWVlNGM0MjM4YmNjMzY2MCIsImF1ZCI6Im....'
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

> The above command returns JSON structured like this:

```json
{
    "_id": "657bdc790b67b600128a865f",
    "uid": "d5b440b8-469b-4e16-8978-d78b73a09c4e",
    "wid": 1,
    "email": "test_0@myabcwallet.com",
    "accounts": [
        {
            "id": "0",
            "sid": "0xbE616d5b24903efc58149f3c7511FeC2085c176e",
            "ethAddress": "0xbE616d5b24903efc58149f3c7511FeC2085c176e",
            "icon": "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAEAAAABACAMAAACdt4Hs....",
            "name": "Account 1",
            "signer": "mpc"
        }
    ],
    "favorites": [],
    "autoconfirms": [],
    "twoFactorEnabled": false,
    "hashToSign": "f631cdd5eebfbe4b8f07798f5b3445d0477dcbe5c1db326b9ec2770bab35a7ad",
    "twoFactorResetRetryCount": 0,
    "twoFactorRetryFreezeEndTime": 0,
    "twoFactorFreezeEndTime": 0
}
```

### HTTP Request

`GET dev-api.waas.myabcwallet.com/wapi/v2/mpc/wallets/info`

### Request Header
Name | Require | Description
--------- | ------- | -----------
Authorization | true | 인증 JWT

## 사용자 패스워드 검증 (Deprecated)

devicePassword와 암호문이 동일한 원문인지 검증합니다.

```python
import requests

url = "https://dev-api.waas.myabcwallet.com/wapi/v2/mpc/wallets/check/device-password"

payload = 'devicePassword=WeZFHUUwcU0LxTVCEJ5Suw%3D%3D&encryptDevicePassword=ukf9SrDdv4AgpSzU8SO2C7gC1f4v5%2Fpa%2FZuow1VLQaK3raQEbul3C5LHBpaum%2BOg'
headers = {
  'Secure-Channel': '037e76bb09e6499f9931ccdda349c95d',
  'Content-Type': 'application/x-www-form-urlencoded',
  'Authorization': 'Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2In0.eyJzdWIiOiJiMjRjODM3YTZlOWU0M2M4YWVlNG....'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

```shell
curl --location 'https://dev-api.waas.myabcwallet.com/wapi/v2/mpc/wallets/check/device-password' \
--header 'Secure-Channel: 037e76bb09e6499f9931ccdda349c95d' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--header 'Authorization: Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2In0.eyJzdWIiOiJiMjRjODM3YTZlOWU0M2M4YWVlNG....' \
--data-urlencode 'devicePassword=WeZFHUUwcU0LxTVCEJ5Suw==' \
--data-urlencode 'encryptDevicePassword=ukf9SrDdv4AgpSzU8SO2C7gC1f4v5/pa/Zuow1VLQaK3raQEbul3C5LHBpaum+Og'
```

```javascript
const axios = require('axios');
const qs = require('qs');
let data = qs.stringify({
  'devicePassword': 'WeZFHUUwcU0LxTVCEJ5Suw==',
  'encryptDevicePassword': 'ukf9SrDdv4AgpSzU8SO2C7gC1f4v5/pa/Zuow1VLQaK3raQEbul3C5LHBpaum+Og' 
});

let config = {
  method: 'post',
  maxBodyLength: Infinity,
  url: 'https://dev-api.waas.myabcwallet.com/wapi/v2/mpc/wallets/check/device-password',
  headers: { 
    'Secure-Channel': '037e76bb09e6499f9931ccdda349c95d', 
    'Content-Type': 'application/x-www-form-urlencoded', 
    'Authorization': 'Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2In0.eyJzdWIiOiJiMjRjODM3YTZlOWU0M2M4YWVlNG....'
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

> 성공시 200 status

```json
{
  "result": true
}
```

### HTTP Request

`POST dev-api.waas.myabcwallet.com/wapi/v2/mpc/check/device-password`

### Request Header
Name | Require | Description
--------- | ------- | -----------
Authorization | true | 인증 JWT
Content-Type | true | application/x-www-form-urlencoded
Secure-Channel | true | 보안 채널 ID

### Request Body

Parameter | Description
--------- | -----------
encryptDevicePassword | 지갑 생성/복구 시 응답으로 받은 encryptDevicePassword(암호화 대상)
devicePassword | 비밀번호 원문(암호화 대상)

## KeyShare 패스워드 검증 (Deprecated)

입력된 devicePassword가 지갑 생성/복구에서 사용된 devicePassword와 동일한지 검증합니다.

```python
import requests

url = "https://dev-api.waas.myabcwallet.com/wapi/v2/mpc/wallets/check/device-password/share"

payload = 'devicePassword=WeZFHUUwcU0LxTVCEJ5Suw%3D%3D&pvencstr=wl5WmBJdq9NppL66wcSVVo4gjkv%2FJ0Gx%2BlYt9Pu64Z....'
headers = {
  'Secure-Channel': '037e76bb09e6499f9931ccdda349c95d',
  'Content-Type': 'application/x-www-form-urlencoded',
  'Authorization': 'Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2In0.eyJzdWIiOiJiMjRjODM3YTZlOWU0M2M4YWVlNGM0MjM4....'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)

```

```shell
curl --location 'https://dev-api.waas.myabcwallet.com/wapi/v2/mpc/wallets/check/device-password/share' \
--header 'Secure-Channel: 037e76bb09e6499f9931ccdda349c95d' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--header 'Authorization: Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2In0.eyJzdWIiOiJiMjRjODM3YTZlOWU0M2M4YWVlNGM0MjM4YmNjMzY2MCIsImF1ZCI6Imh0dHBzOi8vbXcubXl....' \
--data-urlencode 'devicePassword=WeZFHUUwcU0LxTVCEJ5Suw==' \
--data-urlencode 'pvencstr=wl5WmBJdq9NppL66wcSVVo4gjkv/J0Gx+lYt9Pu64ZHLuEE+CurnRGqmVZvFcvzZs9....'
```

```javascript
const axios = require('axios');
const qs = require('qs');
let data = qs.stringify({
  'devicePassword': 'WeZFHUUwcU0LxTVCEJ5Suw==',
  'pvencstr': 'wl5WmBJdq9NppL66wcSVVo4gjkv/J0Gx+lYt9Pu64ZHLuEE+Curn....' 
});

let config = {
  method: 'post',
  maxBodyLength: Infinity,
  url: 'https://dev-api.waas.myabcwallet.com/wapi/v2/mpc/wallets/check/device-password/share',
  headers: { 
    'Secure-Channel': '037e76bb09e6499f9931ccdda349c95d', 
    'Content-Type': 'application/x-www-form-urlencoded', 
    'Authorization': 'Bearer eyJraWQiOiIyNCIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2In0.eyJzdWIiOiJiMjRjODM3YTZlOWU0M2M4YWVlNGM0MjM4YmNjMzY2MCIsImF1ZCI6Imh0dHBzOi8vbXcubXl....'
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

> 성공시 200 status

```json
{
  "result": true
}
```

### HTTP Request

`POST dev-api.waas.myabcwallet.com/wapi/v2/mpc/wallets/check/device-password/share`

### Request Header
Name | Require | Description
--------- | ------- | -----------
Authorization | true | 인증 JWT
Content-Type | true | application/x-www-form-urlencoded
Secure-Channel | true | 보안 채널 ID

### Request Body

Parameter | Description
--------- | -----------
devicePassword | 지갑 생성/복구 시 응답으로 받은 encryptDevicePassword(암호화 대상)
pvencstr | 지갑 생성/복구 시 응답으로 받은 pvenc(암호화 대상)


## KeyShare 생성 후 호출

SDK에서 제공되는 KeyShare 생성 이후 1회 필수 호출합니다.
(외부 공개가 필요한지 검토 필요.)

```python
TBD

```

```shell
TBD
```

```javascript
TBD
```

> 성공시 200 status

```json
{
    "_id": "657bdc790b67b600128a865f",
    "uid": "d5b440b8-469b-4e16-8978-d78b73a09c4e",
    "wid": 1,
    "email": "test_0@myabcwallet.com",
    "accounts": [
        {
            "id": "0",
            "sid": "0xbE616d5b24903efc58149f3c7511FeC2085c176e",
            "ethAddress": "0xbE616d5b24903efc58149f3c7511FeC2085c176e",
            "icon": "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAEAAAABACAMAAACdt4Hs....",
            "name": "Account 1",
            "signer": "mpc"
        }
    ],
    "favorites": [],
    "autoconfirms": [],
    "twoFactorEnabled": false,
    "hashToSign": "f631cdd5eebfbe4b8f07798f5b3445d0477dcbe5c1db326b9ec2770bab35a7ad",
    "twoFactorResetRetryCount": 0,
    "twoFactorRetryFreezeEndTime": 0,
    "twoFactorFreezeEndTime": 0
}
```

### HTTP Request

`POST dev-api.waas.myabcwallet.com/wapi/v2/mpc/wallets/post`

### Request Header
Name | Require | Description
--------- | ------- | -----------
Authorization | true | 인증 JWT
Content-Type | true | application/x-www-form-urlencoded

### Request Body

Parameter | Description
--------- | -----------
email| 사용자 이메일
address | 지갑 생성 응답으로 반환된 sid
ourpubkey | 지갑 생성 응답으로 반환된 ourpubkey
ucpubkey | 지갑 생성 응답으로 반환된 ucpubkey
uid | 지갑 생성 응답으로 반환된 uid
wid | 지갑 생성 응답으로 반환된 wid

## KeyShare 복구 전 호출

SDK에서 제공되는 KeyShare 복구 이전에 호출하여 복구에 필요한 데이터를 얻습니다.
(외부 공개가 필요한지 검토 필요.)

```python
TBD

```

```shell
TBD
```

```javascript
TBD
```

> 성공시 200 status

```json
{
  "uid":"",
  "wid":0,
  "sid":""
}
```

### HTTP Request

`GET dev-api.waas.myabcwallet.com/wapi/v2/mpc/wallets/recover`

### Request Header
Name | Require | Description
--------- | ------- | -----------
Authorization | true | 인증 JWT
Content-Type | true | application/x-www-form-urlencoded

## KeyShare 복구 후 호출

SDK에서 제공되는 KeyShare 복구 이후 1회 필수 호출합니다.
(외부 공개가 필요한지 검토 필요.)

```python
TBD

```

```shell
TBD
```

```javascript
TBD
```

> 성공시 200 status

```json
{
    "_id": "657bdc790b67b600128a865f",
    "uid": "d5b440b8-469b-4e16-8978-d78b73a09c4e",
    "wid": 1,
    "email": "test_0@myabcwallet.com",
    "accounts": [
        {
            "id": "0",
            "sid": "0xbE616d5b24903efc58149f3c7511FeC2085c176e",
            "ethAddress": "0xbE616d5b24903efc58149f3c7511FeC2085c176e",
            "icon": "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAEAAAABACAMAAACdt4Hs....",
            "name": "Account 1",
            "signer": "mpc"
        }
    ],
    "favorites": [],
    "autoconfirms": [],
    "twoFactorEnabled": false,
    "hashToSign": "f631cdd5eebfbe4b8f07798f5b3445d0477dcbe5c1db326b9ec2770bab35a7ad",
    "twoFactorResetRetryCount": 0,
    "twoFactorRetryFreezeEndTime": 0,
    "twoFactorFreezeEndTime": 0
}
```

### HTTP Request

`POST dev-api.waas.myabcwallet.com/wapi/v2/mpc/wallets/recover`

### Request Header
Name | Require | Description
--------- | ------- | -----------
Authorization | true | 인증 JWT
Content-Type | true | application/x-www-form-urlencoded

### Request Body

Parameter | Description
--------- | -----------
ucpubkey | 지갑 생성 응답으로 반환된 ucpubkey
uid | 지갑 생성 응답으로 반환된 uid
wid | 지갑 생성 응답으로 반환된 wid