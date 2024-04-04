# Contract
## eth_call

실제로 트랜잭션을 생성하여 발행하지 않고 컨트랙트의 읽기 method를 실행한 결과를 조회할 수 있습니다. 
주로 특정 스마트 컨트랙트의 현재 상태를 읽기 위해 사용됩니다. 
call로 인한 상태 변경은 일어나지 않습니다.

> 성공시 200 status 반환

```json
{
    "result": "0x"
}
```

### HTTP Request

`POST https://dev-api.waas.myabcwallet.com/wapi/v2/contract/eth-call`

### Request Header

Name | Require | Description
--------- | ------- | -----------
Authorization | true | 인증 JWT

### Request Body

Parameter | Require | Description
--------- | ------- | -----------
chainId | true | 10진수 Chain ID
isEIP1559 | true | EIP1559 여부
from | false | [KRW, USD, ETH]
to | true | 10진수 Chain ID
gasLimit | false | 최대 가스
gasPrice | false | 가스비
value | false |
data | false | call data
nonce | false | 
maxPriorityFeePerGas | false | EIP1559 사용가능
maxFeePerGas | false | EIP1559 사용가능