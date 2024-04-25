# 문자

<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String">String mdn</a>

## .length

`length` 속성은 UTF-16 코드 유닛을 기준으로 문자열의 길이를 나타냅니다.

```javascript
const str = 'Hello world!'
             012345678901
console.log(str.length) 출력 : 12
```

## .includes()

`includes()` 메서드는 하나의 문자열이 다른 문자열에 포함되어 있는지를 판별하고, 결과를 true 또는 false 로 반환합니다. 검색 시 대소문자를 구분합니다.

```javascript
const str = 'Hello world!'

console.log(str.includes('Hello'))  출력 : true
```

```javascript
const str = 'Hello world!'

console.log(str.includes('Hello', 1))  출력 : false  기본값이 0이고 1 index 부터 확인하면 Hello가 없다

if (str.includes('jo')) {
  console.log('Jo가 없습니다')
}
```

## .indexOf()

`.indexOf()`메서드는 호출한 String 객체에서 주어진 값과 일치하는 첫 번째 인덱스를 반환합니다. 일치하는 값이 없으면 -1을 반환합니다.

```javascript
const str = 'Hello woeld!'
             012345678901
console.log(str.indexOf('world')) 출력 : 6
console.log(str.indexOf('Jo'))  출력 : -1

if (str.indexOf('jo') === -1) {
  console.log('Jo가 없습니다')
}
```

## .padEnd()

`padEnd()` 대상 문자의 길이(length)가 지정된 길이보다 작으면<br/>
주어진 문자를 지정된 길이까지 끝에 붙여 새로운 문자를 반환합니다.

```javascript
const str = '1234567'

console.log(str.padEnd(10, '0'))  출력 : 1234567000
console.log(str)  출력 : 1234567
```

```javascript
const str = '1234567890123'

console.log(str.padEnd(10, '0'))  출력 : 1234567890123
console.log(str)  출력 : 1234567890123
```

```javascript
const str = '12345'

console.log(str.padEnd(10, '!'))  출력 : 12345!!!!!
console.log(str)  출력 : 12345
```

## .padStart()

`padStart()` 대상 문자의 길이(length)가 지정된 길이보다 작으면<br/>
주어진 문자을 지정된 길이까지 앞에 붙여 새로운 문자를 반환합니다.

```javascript
const str = '1234567'

console.log(str.padStart(10, '0'))  출력 : 0001234567
console.log(str)  출력 : 1234567
```

```javascript
const str = '1234567890123'

console.log(str.padStart(10, '0'))  출력 : 1234567890123
console.log(str)  출력 : 1234567890123
```

## .replace()

`replace()` 대상 문자에서 패턴(문자, 정규식)과 일치하는 부분을 교체한 새로운 문자를 반환합니다.

```javascript
const str = 'Hello, Hello?!'

console.log(str.replace('Hello', 'Hi')) 출력 : Hi, Hello?!
console.log(str.replace(/Hello/g, 'Hi'))  출력 : Hi, Hi?!
console.log(str)  출력 : Hello, Hello?!
```

## .slice()

`slice()` 대상 문자의 일부를 추출해 새로운 문자를 반환합니다.<br/>
주 번째 인수 직전까지 추출하고, 두 번째 인수를 생략하면 대상 문자의 끝까지 추출합니다.

```javascript
const str = 'Hello world!'
             012345678901
            -210987654321
console.log(str.slice(0, 5))  출력 : Hello
console.log(str.slice(6, -1)) 출력 : world
console.log(str.slice(6)) 출력 : world!
console.log(str)  출력 : Hello world!
```

## .split()

`split()` 대상 문자를 주어진 구분자로 나눠 배열로 반환합니다.

```javascript
const str = 'Apple, Banana, Cherry'

console.log(str.split(', '))  출력 : 'Apple', 'Banana', 'Cherry'
console.log(str.split(','))  출력 : 'Apple', ' Banana', ' Cherry'
console.log(str.split(''))  출력 : 'A','p','p','l','e','B','a','n','a','n','a','C','h','e,','r','r,','y'
```

```javascript
const str = 'Apple / Banana / Cherry'

console.log(str.split(' / '))  출력 : 'Apple', 'Banana', 'Cherry'
console.log(str.split('/'))  출력 : 'Apple ', ' Banana ', ' Cherry'
console.log(str.split(''))  출력 : 'A','p','p','l','e','B','a','n','a','n','a','C','h','e,','r','r,','y'
```

## .toLowerCase()

`toLowerCase()` 대상 문자를 영어 소문자로 변환해 새로운 문자로 반환합니다.

```javascript
const str = 'Apple, Banana, Cherry'

console.log(str.toLowerCase())  출력 : apple, banana, cherry
console.log(str)  출력 : Apple, Banana, Cherry
```

## .toUpperCase()

`toUpperCase()` 대상 문자를 영어 대문자로 변환해 새로운 문자로 반환합니다.

```javascript
const str = 'Apple, Banana, Cherry'

console.log(str.toUpperCase())  출력 : APPLE, BANANA, CHERRY
console.log(str)  출력 : Apple, Banana, Cherry
```

## .trim()

`trim()` 대상 문자의 앞뒤 공백 문자(space, tab 등)를 제거한 새로운 문자를 반환합니다.

```javascript
const str = '   JO!   '

console.log(str.trim()) 출력 : JO!
console.log(str)  출력 :    JO!
```

# 숫자

## .toFixed()

`toFixed` 숫자를 지정된 고정 소수점 표기(자릿수)까지 표현하는 문자로 반환합니다.

```javascript
const num = 3.1415926535

console.log(num.tiFixed(2)) 출력 : 3.14(문자)
console.log(parseFloat(num.toFixed(2))) 출력 : 3.14(숫자)
```

## .toLocaleString()

`toLoacleString()` 숫자를 현지 언어 형식의 문자로 반환합니다.

```javascript
const num = 1000000

console.log(num.toLocaleString()) 출력 : 1,000,000
console.log(`${num.toLocaleString()}원`)  출력 : 1,000,000원
```

## Number.isInteger()

`Number.isInteger()` 숫자가 정수(integer)인지 확인합니다.

```javascript
const num = 123
const pi = 3.14

console.log(Number.isInteger(num))  출력 : true
console.log(Number.isInteger(pi)) 출력 : false
```

## Number.isNaN()

`Number.isNaN()` 주어진 값이 'NaN'인지 확인합니다.

```javascript
const num1 = NaN
const num2 = 123
const str = "Hello world"
const nul = null

console.log(Number.isNaN(num1)) 출력 : true
console.log(Number.isNaN(num2)) 출력 : false
console.log(Number.isNaN(str))  출력 : false
console.log(Number.isNaN(nul))  출력 : false
```

## Number.parseInt() 또는 parseInt()

`parseInt()` 주어진 값(숫자, 문자)을 파싱해 특정 진수(radix)의 정수로 반환합니다.

```javascript
const str = '3.1415926535'
cosnt num = 3.1415926535

console.log(Number.parseInt(str, 10)) 출력 : 3(숫자)
console.log(Number.parseInt(num, 10)) 츌력 : 3(숫자)
```

## Number.parseFloat() 또는 parseFloat()

`parseFloat()` 주어진 값(숫자, 문자)을 파싱해 특정 진수(radix)의 정수로 반환합니다.

```javascript
const str = '3.1415926535'
cosnt num = 3.1415926535

console.log(Number.parseFloat(str, 10)) 출력 : 3.1415926535(숫자)
console.log(Number.parseFloat(num, 10)) 츌력 : 3.1415926535(숫자)
```

# 수학

<a href="https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Math">Math mdn</a>

## Math.abs()

`Math.abs()` 주어진 숫자의 절대값을 반환합니다.

```javascript
console.log(Math.abs(2))  출력 : 2(숫자)
console.log(Math.abs(-2)) 출력 : 2(숫자)
```

## Math.ceil()

`Math.ceil()` 주어진 숫자를 올림해 정수를 반환합니다.

```javascript
console.log(Math.ceil(3.1415926535))  출력 : 4(숫자)
```

## Math.floor()

`Math.floor()` 주어진 숫자를 내림해 정수를 반환합니다.

```javascript
console.log(Math.floor(3.1415926535))  출력 : 3(숫자)
```

## Math.max()

`Math.max()` 주어진 숫자 중 가장 큰 숫자를 반환합니다.

```javascript
console.log(Math.max(1, 22, 38, 192)) 출력 : 192(숫자)
```

## Math.min()

`Math.min()` 주어진 숫자 중 가장 작은 숫자를 반환합니다.

```javascript
console.log(Math.max(1, 22, 38, 192)) 출력 : 1(숫자)
```

## Math.pow()

`Math.pow()` 주어진 숫자의 거듭제곱한 값을 반환합니다.

```javascript
console.log(Math.pow(4, 2)) 출력 : 16(숫자)
console.log(Math.pow(7, 2)) 출력 : 49(숫자)
console.log(Math.pow(10, 3)) 출력 : 1000(숫자)
```

## Math.random()

`Math.random()` 숫자 0 이상; 1 미만의 난수를 반환합니다.

```javascript
console.log(Math.random())  출력 : 0.711243871246835(숫자)
```

특정 범위의 랜덤 정수를 앋는 함수

```javascript
function random(min = 0, max = 10) {
  return Math.floor(Math.random() * (max - min)) + min
}
console.log(random()) 출력 : 2(숫자)
console.log(random(11, 20)) 출력: 18(숫자)
console.log(random(101, 999)) 출력 : 333(숫자)
```

## Math.round()

`Math.round()` 주어진 숫자를 반올림해 정수를 반환합니다.

```javascript
const num1 = 3.141
const num2 = 3.768

console.log(Math.round(num1)) 출력 : 3(숫자)
console.log(Math.round(num2)) 출력 : 4(숫자)
```
