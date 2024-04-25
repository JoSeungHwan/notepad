# 산술 연산자

```javascript
console.log(1 +2) 출력 3
console.log(5 - 7) 출력 -2
console.log(3 * 4) 출력 12
console.log(10 / 2) 출력 5
console.log(7 % 5) 출력 2

function isEven(num) {
	return num % 2 === 0
}
console.log(isEven(3)) 출력 false 홀수
console.log(isEven(12)) 출력 true 짝수
```

# 할당 연산자

```javascript
const a = 3 재 할당 불가
let a = 3 제 할당 가능

a = a + 2
a += 2 -*/% 다 가능
```

# 증감 연산자

```javascript
let a = 3

console.log(a++) 출력 3
console.log(++a) 출력 4
console.log(a) 출력 4

console.log(a—) 출력 3
console.log(—a) 출력 2
console.log(a) 출력 2

a += 1
a -= 1 로 쓰는거 추천
```

# 부정 연산자

```javascript
console.log(!true) 출력 false
console.log(!!0) 출력 false
```

# 비교 연산자

```javascript
const a = 1
const b = 3

동등(형 변환)
console.loog(a == b) 출력 false

부등(현 변환)
console.log( a != b) true

일치
console.log( a === b ) 출력 false

불일치
console.log( a !== b) true

큼
console.log(a > b) false

크거나 같음
console.log( a>= b) true

작음
console.log( a < b) true

작거나 같은
console.log( a <= b) true

```

# 논리 연사자

### AND연산자

```javascript
const a = true
const b = false
if (a &&b) {
	console.log(‘모두가 참’)
}
if (a || b) {
 	console.log(‘하나 이상이 참’)
}
```

# Nullish 병합

```javascript
const n = 0
OR 연산자
const num1 = n || 7
console.log(num1) 7
Nullish 병합 연산자
const num2 = n ?? 7
console.log(num2) 0

console.log(null ?? 1) 1
console.log(nudefined ?? 2) 2
console.log(null ?? nudefined) nudrfined
console.log(null ?? 1 ?? 2) 1
console.log(false ?? 1 ??2) false
console.log(0 ?? 1 ?? 2) 0
null 이나 nudefined빼고는 뒤에 무시
```

# 삼항 연산자

```javascript
const a = 1
if (a < 2) {
	console.log(‘참’) 출력
} else {
	console.log(‘거짓’)
}

조건 ? 참 : 거짓
console.log(a <2 ? ‘참’ : ‘거짓’)

function getAlert(message) {
	return message ? message “ : ‘메세지가 없음’
}
```

# 전개 연산자 …

```javascript
const a = [1, 2, 3]
const b [4, 5, 6]

console.log(a) [1, 2, 3]
console.log(…a) 1 2,3

const c = a.concat(b)
console.log(c) [1, 2, 3, 4, 5, 6]

const d = […a, …b]
console.log(d) [1, 2, 3, 4, 5, 6]

const a = { x:1, y:2 }
const b = { y:3, z:4 }

const c = Object.assign({}, a, b)
console.log(c) x:1, y:3, z:4

const d = {a, b}
console..log(d) a: {x: 1, y: 2}, b: {y:3, z:4}

const d = {…a, …b}
console..log(d) x:1, y:3, z:4

function fn(x, y, z) {
	console.log(x, y, z)
}
fn(q, 2, 3)
const a [1, 2, 3]
fn(a[0], a[1], a[2])
fn([1, 2, 3])
fn(a)
```

# 구조 분해 할당

```javascript
const arr = [1, 2, 3]
const a = arr[0]
const b = arr[1]
const c = arr[2]
console.log(a, b, c) 1 2 3

const [a, b, c] = arr

let a = 0
let b = 0
let c = 0
[a, b, c] = arr

const arr = [1, 2, 3]
const [a, …rest] = arr
console.log(a, rest) 1 [2, 3]

const obj = {
	a: 1,
	b: 2,
	c: 3
	x: 7
}
const a = obj.a
const b = obj.b
const c = obj.c
const {a, b, c} = obj
const {a} = obj
const {x = 4} = obj
const {x = 4, a: Jo, y: ten = 10} = obj

console.log(a, b, c) 1 2 3
console.log(x, Jo, ten) 7 1 10
```

# 선택적 체이닝

```javascript
const user = null

console.log(user?.name) nudrfined

const userA = {
	name: ‘Jo’,
	age: 85,
	addredd: {
		country: ‘Korea’,
		city: ‘Seoul’
	}
}
const userB = {
	name: ‘Neo’
	age: 22
}
function gerCity(user) {
	return user.address?.city || ‘주소 없음’
}
console.log(getCity(userA))
console.log(getCity(userB)) B에는 address가 없어서 ? 을 붙여서 없으면 nudefined 가 출력하게 만든다 주소없음 출력
```

# if, Switch 조건문

```javascript
if (조건) {
}
if (조건) {
} else {
}
if (조건1) {
} else if (조건2) {
} else if (조건3) {
} else {
}

function isPositive(number) {
	if (number > 0) {
		return ‘양수’
	} else if (number < 0) {
		return ‘음수’
	} else {
		return ‘0’
	}
}
console.log(isPositive(1)) 양수
console.log(isPositive(10)) 양수
console.log(isPositive(-2)) 음수
console.log(isPositive(0)) 0

switch (조건) {
	case 값1:
		조건이 값1일 때 실행
		break
	case 값2:
		조건이 값2일 때 실행
		break
	default:
		조건이 값1도 값2도 아닐 때 실행
}
function price(fruit) {
	switch (fruit) {
		case ‘Apple’:
			return 1000
		case ‘Banana’:
			return 1500
		case “cherry’:
			return 2000
		default:
			return 0
	}
}
function price(fruit) {
	if (fruit === ‘Apple’) {
		return 1000
	} else if (fruit === ‘Banana’) {
		return 1500
	} else if (fruit === ‘Chrry’) {
		return 2000
	} else {
		return 0
	}
}
console.log(price(‘Apple’)) 1000
console.log(price(‘Banana’)) 1500
console.log(price(‘Cherry’)) 2000
console.log(price(‘Hello’)) 0
```

# For, For of, For in 반복문

```javascript
for (초기화; 조건; 증감) {
	반복 실행할 코드
}
for (let i = 0; i < 10; i += 1) {
}
for (let i = 9; i > -1; i -= 1) {
}
for (let i = 9; i > -1; i -= 1) {
	if (i < 4) {
		break
	}
}
for (let i = 9; i > -1; i -= 1) {
	if (ii % 2 === 0) {
		continue
	}
} 짝수 빼고 출력

For of 반복문
const fruits = [‘Apple’, ‘Banana’, ‘Chrry’]
for (let i = 0; i < fruits.lenth; i += 1) {
	console.log(fruits[1])
}
for (const a of fruits) {
 	console.log(a)
}

const users = [
	{
		name: ‘Jo’,
		age: 29
	},
	{
		name: ‘ss’,
		age: 20
	},
	{
		name: ‘hh’,
		age: 31
	}
]
for (let i = 0; i < users.length; i += 1) {
	console.log(users[i])
}
for (const user of users) {
	console.log(user)
}

For in 반복문
const user = {
	name: ‘jo’,
	age: 29,
	isValid: true,
	email: ‘swcc321@naver.com’
}
for (const key in user) {
	console.log(key)
	console.log(user[key])
}
```

# While, Do while 반복문

### While 반복문

```javascript
let n = 0;
while (n < 4) {
  console.log(n);
  n += 1;
}
```

### Do While 반복문

```javascript
let n = 0;
while (n) {
  console.log(n);
  n += 1;
}
do {
  console.log(n);
  n += 1;
} while (n);
```
