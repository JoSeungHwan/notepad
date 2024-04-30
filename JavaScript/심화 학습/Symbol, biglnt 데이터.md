# 심봄(Symbol)

### 변경이 불가한 데이터로, 유일한 식별자를 만들어 데이터를 보호하는 용도로 사용할 수 있습니다.

## Symbol('설명')

### '설명'은 당순 디버깅을 위한 용도일 뿐, 심볼 값과는 관계가 없습니다.

```javascript
const sKey = Symbol('Hello')
const user = {
  key: '일반 정보',
  [sKey]: '민감한 정보'
}

console.log(user.key)                 출력 : 일반 정보
console.log(user.['key'])             출력 : 일반 정보
console.log(user.[sKey])              출력 : 민감한 정보
console.log(user.[Symbol('Hello')])   출력 : undefined
console.log(sKey)                     출력 : Symbol(Hello)
```

#### 예제

`main.js`

```javascript
import Jo from './Jo.js';

console.log(Jo);                출력 : firstName: Jo, lastName: Hwan, age: 29, Symbol(Date od birth): Mon: Jan 16 1994 17:30:00 GMT+0900 (한국 표쥰시), Symbol(Emails)
console.log(Object.keys(Jo));   출력 : firstName, lastName, age
for (const key in Jo) {
  console.log(Jo[key]);         출력 : JO Hwan 29
}

console.log(Jo[birthKey]);      출력 : sun Jan 16 1994 17:30:00 GMT+0900 (한국 표준시)
console.log(Jo[emailsKey]);     출력 : swcc321@naver.com, abc@naver.com
```

`Jo.js`

```javascript
import { birthKey, emailsKey } from './keys.js';

export default {
  firstName: 'Jo',
  lastName: 'Hwan',
  age: 29,
  [birthKey]: new Date(1993, 12, 16, 17, 30),
  [emailsKey]: ['swcc321@naver.com', 'abc@naver.com'],
};
```

`keys.js`

```javascript
export const birthKey = Symbol('Date od birth');
export const emailsKey = Symbol('Emails');
```

# BigInt

### BigInt는 길이 제한이 없는 정수(integer)입니다.

### 숫자(number) 데이터가 안정적으로 표시할 수 있는,

### 최대치(`2^53 - 1`)보다 큰 정수를 표현할 수 있습니다.

### 정수 뒤에 `n`을 붙이거나 `BigInt()`를 호출해 생성합니다.

```javascript
console.log(1234567890123456789012345678901234567890)             출력 : 1.23456789012345678e+39
console.log(1234567890123456789012345678901234567890n)            출력 : 1234567890123456789012345678901234567890n
console.log(BigInt('1234567890123456789012345678901234567890'))   출력 : 출력 : 1234567890123456789012345678901234567890n

const a = 11n
const b = 22

// 숫자 => BigInt
console.log(a + BigInt(b))            출력 : 33n
console.log(typeof (a + BigInt(b)))   출력 : bigint

// Bigint => 숫자
console.log(Numder(a) + b)            출력 : 33
console.log(typeof (Number(a) + (b))) 출력 : number
```
