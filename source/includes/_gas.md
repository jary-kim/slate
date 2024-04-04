# Gas
## 가스비 조회

```json
{
    "result": "0x5208"
}
```
### HTTP Request

`GET https://dev-api.waas.myabcwallet.com/wapi/v2/gas/price`


### Request Header

Name | Require | Description
--------- | ------- | -----------
Authorization | true | 인증 JWT

### Query Parameters

Parameter | Require | Description
--------- | ------- | -----------
chainId | true | 10진수 Chain ID
isEIP1559 | true | EIP1559 여부

## 가스비 제안

EIP 1559를 지원하는 chain에 대해서만 지원한다.

> 성공시 200 status 반환

```json
{
    "low": {
        "suggestedMaxPriorityFeePerGas": "0.02073725822",
        "suggestedMaxFeePerGas": "15.970339979",
        "minWaitTimeEstimate": 15000,
        "maxWaitTimeEstimate": 30000
    },
    "medium": {
        "suggestedMaxPriorityFeePerGas": "0.02139908561",
        "suggestedMaxFeePerGas": "21.553362758",
        "minWaitTimeEstimate": 15000,
        "maxWaitTimeEstimate": 45000
    },
    "high": {
        "suggestedMaxPriorityFeePerGas": "0.0882",
        "suggestedMaxFeePerGas": "27.202524624",
        "minWaitTimeEstimate": 15000,
        "maxWaitTimeEstimate": 60000
    },
    "estimatedBaseFee": "15.94960272",
    "networkCongestion": 0,
    "latestPriorityFeeRange": [
        "0.022060912",
        "6"
    ],
    "historicalPriorityFeeRange": [
        "0.00001",
        "273.17093238"
    ],
    "historicalBaseFeeRange": [
        "14.897614381",
        "23.052346282"
    ],
    "priorityFeeTrend": "down",
    "baseFeeTrend": "down"
}
```
### HTTP Request

`GET https://dev-api.waas.myabcwallet.com/wapi/v2/gas/suggestedGasFees`


### Request Header

Name | Require | Description
--------- | ------- | -----------
Authorization | true | 인증 JWT

### Query Parameters

Parameter | Require | Description
--------- | ------- | -----------
chainId | true | 10진수 Chain ID



## (Deprecated) 가스비 예측


> 성공시 200 status 반환

```json
{
    "result": "0x5208"
}
```
### HTTP Request

`POST https://dev-api.waas.myabcwallet.com/wapi/v2/gas/estimate`


### Request Header

Name | Require | Description
--------- | ------- | -----------
Authorization | true | 인증 JWT

### Request Body

Parameter | Require | Description
--------- | ------- | -----------
chainId | true | 10진수 Chain ID
isEIP1559 | true | EIP1559 여부
from | false | 
to | true | target address
gasLimit | false | 최대 가스
gasPrice | false | 가스비
value | false | 
data | false | call data
nonce | false | 
maxPriorityFeePerGas | false | EIP1559
maxFeeperGas | false | EIP1559

## EIP 1559 가스비 예측

> 성공시 200 status 반환

```json
{
    "result": "0x5208"
}
```
### HTTP Request

`POST https://dev-api.waas.myabcwallet.com/wapi/v2/gas/estimate/eip1559`


### Request Header

Name | Require | Description
--------- | ------- | -----------
Authorization | true | 인증 JWT

### Request Body

Parameter | Require | Description
--------- | ------- | -----------
chainId | true | 10진수 Chain ID
from | false | 
to | true | target address
gasLimit | false | 최대 가스
value | false | 
data | false | call data
nonce | false | 
maxPriorityFeePerGas | false | 
maxFeeperGas | false | 

## Legacy 가스비 예측


> 성공시 200 status 반환

```json
{
    "result": "0x5208"
}
```
### HTTP Request

`POST https://dev-api.waas.myabcwallet.com/wapi/v2/gas/estimate/legacy`


### Request Header

Name | Require | Description
--------- | ------- | -----------
Authorization | true | 인증 JWT

### Request Body

Parameter | Require | Description
--------- | ------- | -----------
chainId | true | 10진수 Chain ID
from | false | 
to | true | target address
gasLimit | false | 최대 가스
gasPrice | false | 가스비
value | false | 
data | false | call data
nonce | false | 