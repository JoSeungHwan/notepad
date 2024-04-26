# 날짜

```javascript
const date = new Date()

console.log(date) 출력 : Wed Sep 28 2022 15:09:22 GMT+0900 ( 한국 표준시 )
```

```javascript
const d1 = new Date(2022, 11, 16, 12, 57, 30)

console.log(d1) 출력 : Fri Dec 16 2022 12:57:30 GMT+0900 ( 한국 표준시 )
```

```javascript
const d1 = new Date(2022, 11, 16, 12, 57, 30)

console.log(d1) 출력 : Fri Dec 16 2022 12:57:30 GMT+0900 ( 한국 표준시 )
```

```javascript
const d2 = new Date('Fri Dec 16 2022 12:57:30 GMT+0900 ( 한국 표준시 )')

console.log(d2) 출력 : Fri Dec 16 2022 12:57:30 GMT+0900 ( 한국 표준시 )
console.log(d2.getFullYear()) 출력 : 2022(숫자)
```

## .getFullYear()와 , .setFullYear()

`getFullYear()와 , .setFullYear()` 날짜 인스턴스의 '연도'를 반환하거나 지정합니다.

```javascript
const date = new Date()

console.log(date.getfullYear()) 출력 : 2022(숫자)

date.setFullYeat(2023)
console.log(date.getFullYear) 출력 : 2023
console.log(date) 출력 : Thu Sep 28 2023 15:20:23 GMT+0900 ( 한국 표준시 )
```

## .getMonth()와 .setMonth()

`getMonth()와 .setMonth()` 날짜 인스턴스의 '월'을 반환하거나 지정합니다.<br/>
0부터 시작(Zero-based numbering)힙니다.

```javascript
const date = new Date()

console.log(date.getMonth())  출력 : 8(숫자)
console.log(date) 출력 : Wed Sep 28 2022 15:27:35 GMT+0900 ( 한국 표준시 )

date.setMonth(0)
console.log(date.getMonth())  출력 : 0
console.log(date) 출력 : Fri Jan 28 2022 15:27:35 GMT+0900 ( 한국 표준시 )
```

## .getDate()와 .setDate()

`getDate()와 .setDate()` 날짜 인스턴스의 '일'을 반환하거나 지정합니다.

```javascript
const date = new Date()

console.log(date.getDate())  출력 : 28(숫자)
console.log(date) 출력 : Wed Sep 28 2022 15:27:35 GMT+0900 ( 한국 표준시 )

date.setDate(11)
console.log(date.getDate())  출력 : 11
console.log(date) 출력 : Fri Jan 11 2022 15:27:35 GMT+0900 ( 한국 표준시 )
```

## .getHours()와 .setHours()

`getHours()와 .setHours()` 날짜 인스턴스의 '시간'을 반환하거나 지정합니다.

```javascript
const date = new Date()

console.log(date.getHours())  출력 : 15(숫자)
console.log(date) 출력 : Wed Sep 28 2022 15:27:35 GMT+0900 ( 한국 표준시 )

date.setHours(7)
console.log(date.getHours())  출력 : 7
console.log(date) 출력 : Fri Jan 28 2022 7:27:35 GMT+0900 ( 한국 표준시 )
```

## .getMinutes()와 .setMinutes()

`getMinutes()와 .setMinutes()` 날짜 인스턴스의 '분'을 반환하거나 지정합니다.

```javascript
const date = new Date()

console.log(date.getMinutes())  출력 : 48(숫자)
console.log(date) 출력 : Wed Sep 28 2022 15:48:35 GMT+0900 ( 한국 표준시 )

date.setMinutes(2)
console.log(date.getMinutes())  출력 : 2
console.log(date) 출력 : Fri Jan 28 2022 7:02:35 GMT+0900 ( 한국 표준시 )
```

## .getSeconds()와 .setSeconds()

`getSeconds()와 .setSeconds()` 날짜 인스턴스의 '초'을 반환하거나 지정합니다.

```javascript
const date = new Date()

console.log(date.getSeconds())  출력 : 38(숫자)
console.log(date) 출력 : Wed Sep 28 2022 15:48:38 GMT+0900 ( 한국 표준시 )

date.setSeconds(57)
console.log(date.getSeconds())  출력 : 57
console.log(date) 출력 : Fri Jan 28 2022 7:02:57 GMT+0900 ( 한국 표준시 )
```

## .getDay()

`getDay()` 날짜 인스턴스의 '요일'을 반환합니다.

```javascript
const date = new Date()
const day = date.getDay()

console.log(day)  출력 : 3(숫자)
console.log(getDayKo(day))  출력 : 수요일

function getDayKo(day) {
  switch (day) {
    case 0: return '일요일'
    case 1: return '월요일'
    case 2: return '화요일'
    case 3: return '수요일'
    case 4: return '목요일'
    case 5: return '금요일'
    case 6: return '토요일'
  }
}
```

## .getTime()와 .setTime()

`.getTime()와 .setTime()` 날짜 인스턴스의 '밀리초(ms)'로 변환하거나 지정합니다.<br/>
'1970-01-01 00:00:00' (유닉스타입)부터 경과한 날짜

```javascript
const date = new Date()

console.log(date,getTime()) 출력 : 1664348309502(숫자)
console.log(date) 출력 : Wed Sep 28 2022 15:58:29 GMT+0900 ( 한국 표준시 )

date.setTime(1700000000000)
console.log(date.getTime()) 출력 : 1700000000000(숫자)
console.log(date) 출력 : Wed Nov 15 2023 07:13:20 GMT+0900 ( 한국 표준시 )
```

```javascript
Date.prototype.isAfter = functiom (date) {
 const a = this.getTime()
 const b = date.hetTime()
 return a > b
}

const d1 = new Date('Set Jan 01 2022 00:00:00 GMT+0900 ( 한국 표준시 )')
const d2 = new Date('Set Jan 01 2023 00:00:00 GMT+0900 ( 한국 표준시 )')

console.log(d1.isAfter(d2))  출력 : false
console.log(d2.isAfter(d1))  출력 : true
```

## Date.now()

`Date.now()` 메소드가 호출될 때의 '밀리초(ms)'로 반환합니다.

```javascript
const time = new Date().getTime()
console.log(Date.now()) 출력 : 1664349597861(숫자)
console.log(time) 출력 : 1664349597861(숫자)

setTimeout(() => {
  console.log(Date.now()) 출력 : 1664349597861(숫자)
  console.log(time) 출력 : 1664349597861(숫자)
})
```
