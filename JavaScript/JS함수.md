# 함수(function)

## 함수 선언문(Declaration) 호이스팅 가능

```javascript
function hello() {}
```

## 함수 표현식(Expression) 호이스팅 불가능

```javascript
const hello = function () {};
```

## 호이스팅

```javascript
hello() < 먼저 사용할때 호이스팅 발생
function hello() {
  console.log(‘Hello’)}
```

# 반환 및 종료

```javascript
function hello() {
  return ‘Hello’
  return 뒤에 아무것도 안붙이면 undefined
}
console.log(‘hello())

function plus(num) {
  if (typrof num !== ’number’) {
    console.log(‘숫자를 입력하세요’)
    return 0
  }
  return num + 1
}
console.log(plus(2)) 3
console.log(plus(7)) 8
console.log(plus()) 0
```

# 매개변수 패턴

## 기본값

```javascript
function sum(a, b = 1) {
  return a + b
}
console.log(sum(1, 2)) 3
console.log(sum(7)) 8
```

## 구조 분해 할당

```javascript
const user = {
  name: ‘Jo’,
  age: 29,
  email: ‘swcc321@naver.com’
}

function getName(user) {
  return user.name
}
function getName(user) {
  const { name } = user
  return name
}
function getName({ name }) {
  return name
}

function getEmail({ email  = ‘이메일이 없습니다’}) {
  return email
}

console.log(getName(user)) Jo
console.log(getEmail(user)) swcc321@naver.com

const fruits = [‘Apple’, ‘Banana’, ‘Cherry’]
const numbers = [1, 2, 3, 4, 5, 6, 7]

function getSecondItem(array) {
  return array[1]
}
function getSecondItem(a, b, c) {
  return b
}
function getSecondItem(, b) {
  return b
}

console.log(getSecondItem(fruits)) Banana
console.log(getSecondItem(numbers)) 2
```

## 나머지 매개변수

```javascript
function sum(…rest) {
  console.log(rest)
}
console.log(sum(1, 2)) console.log(rest) [1, 2]
console.log(sum(1, 2, 3, 4)) console.log(rest) [1, 2, 3, 4]
console.log(sum(1, 2, 3, 4, 5, 6, 7, 8, 8, 10)) console.log(rest) [1, 2, 3, 4, 5, 6, 7, 8, 8, 10]

function sum(a, b, …rest) {
  console.log(rest)
}
console.log(sum(1, 2)) console.log(rest) []
console.log(sum(1, 2, 3, 4)) console.log(rest) [3, 4]
console.log(sum(1, 2, 3, 4, 5, 6, 7, 8, 8, 10)) console.log(rest) [3, 4, 5, 6, 7, 8, 8, 10]

function sum(…rest) {
  console.log(rest)
  return rest.reduce(function (acc, cur) {
    return acc + cur
  }, 0)
}
console.log(sum(1, 2)) 3 console.log(rest) [1, 2]
console.log(sum(1, 2, 3, 4)) 10 console.log(rest) [1, 2, 3, 4]
console.log(sum(1, 2, 3, 4, 5, 6, 7, 8, 8, 10)) 55 console.log(rest) [1, 2, 3, 4, 5, 6, 7, 8, 8, 10]
```

# 화살표 함수

```javascript
function sum() {}
const sum = function () {}
const sum = () => {}

function sum(a, b) {
  return a + b
}

const sum = (a, b) => {
  return a + b
}
const sum = (a, b) => a + b

console.log(sum(1,2)) 3
console.log(sum(10, 20)) 30

const a = () => {}
const b = x => {}
const c = (x, y) => {}
const d = x => { return x * x }
const e = x => x * x
const g = () => { return { a: 1} }
const h = () => ({ a: 1})
const i = () => { return [1, 2, 3] }
const j = () => [1, 2, 3]
```

# 즉시 실행 함수

```javascript
const a = 7
const double = () => {
  console.log(a * 2)
}
double()

;(() => {
  console.log(a * 2)
})()

;(() => { console.log(a * 2) })()	(F)()
;(function () { console.log(a * 2) })()	(F)()
;(function () { console.log(a * 2) }())	(F())
;!function () { console.log(a * 2) }()	!F()
;+function () { console.log(a * 2) }()	+F()

;((a,b) => {
  console.log(a)
  console.log(b)
})(1, 2)
```

# 콜백

```javascript
const a = callback => {
  console.log(‘A’)
  callback()
}
const b () => {
  console.log(‘B’)
}
a(b) A B

const sum = (a, b) => a + b
console.log(sum(1, 2)) 3
console.log(sum(3, 7)) 10

const sum = (a, b, c) => {
  setTimeout(() => {
    c(a + b)
  }. 1000)
}
sum(1, 2, value => {
  console.log(value)
}) 3
sum(3, 7, value => {
  console.log(value)
}) 10

const loadImage = (url) => {
  const imgEL = document.createElement(‘img’)
  imgEL = url
  imgEL.addEventListener(‘load’, () => {
    setTimeout(() => {
      cd(imgEL)
    }, 1000)
  })
}
const containerEL = document.querySelector(‘.container’)
loadImage(‘https://www.naver.com', imgEL => {
  containerEL.innerHTML = ‘’
  containerEL.append(imgEL)
})
.container 가 기본으로 있고 1초가 지나면 loadIamge가 보여진다
```

# 재귀

## 함수 내부에서 자기자신을 다시 호출한다

```javascript
let i = 0
const a = () => {
  console.log(‘A’)
  i += 1
  if (i < 4) {
    a()
  }
}
a() A A A A

const userA = { name: ‘A’, parent: null }
const userB = { name: ‘B’, parent: userA }
const userC = { name: ‘C’, parent: userB }
const userD = { name: ‘D, parent: userC }

const getRootUser = user => {
  if (user.parent) {
    return getRootUser(user.oarent)
  }
  return user
}
console.log(getRootUser(userD))	name: ‘A’, parent: null
console.log(getRootUser(userC))	name: ‘A’, parent: null
console.log(getRootUser(userB))	name: ‘A’, parent: null
console.log(getRootUser(userA))	name: ‘A’, parent: null
```

# 호출 스케줄링

```javascript
setTimeout() => {
  console.log(‘Hello’)
  }, (200)

const hello = () => {
  console.log(‘Hello’)
}
setTimeout(hello, 2000)

const hello = () => {
  console.log(‘Hello’)
}
const timeout = setTimeout(hello, 2000)
clearTimeout(timeout)

const hello = () => {
  console.log(‘Hello’)
}
const timeout = setTimeout(hello, 2000)
const h1EL = document.querySelector(‘h1’)
h1EL.addEventListener(‘click’, () => {
  console.log(‘Clear’)
  clearTimeout(timeout)
})
setTimeout 2초가 되기전에 h1EL을 누르면 Clear가 로그되고 타이머를 클리어 한다

const hello = () => {
  console.log(‘Hello’)
}
const timeout = setInterval(hello, 2000)
const h1EL = document.querySelector(‘h1’)
h1EL.addEventListener(‘click’, () => {
  console.log(‘Clear’)
  setInterval(timeout)
})
setInterval 2초마다 Hello를 호출하고 h1EL을 누르면 Clear 가 호출 되면서 Hello 호출을 멈춘다
```

# this

### 일반 함수의 this는 호츌 위치에서 정의

### 화살표 함수의 this는 자신이 선언된 함수(렉시컬) 범위에서 정의

```javascript
const user = {
  firstName: “Jo”,
  lastName: ‘hh’,
  age: 29.
  getFullName: function () {
    return `${user.firstName} ${user.lastName}`
    return `${this.firstName} ${this.lastName}`
  }
}
console.log(user.getFullName()) Jo hh

function user() {
  this.firstName = ‘Neo’
  this.lastName - ‘hh’

  return {
    firstName: ‘Jo’,
    lastName: ‘hh’,
    age: 29,
    getFullName: () => {
      return `${this.firstNam} ${this.lastName}`
    }
  }
}

const u = user()
console.log(u.getFullName()) Neo hh

function user() {
  this.firstName = ‘Neo’
  this.lastName - ‘hh’

  return {
    firstName: ‘Jo’,
    lastName: ‘hh’,
    age: 29,
    getFullName: function() {
      return `${this.firstNam} ${this.lastName}`
    }
  }
}
const lewis = {
  firstName: ‘ss’
  lastName: ‘hh’
}

const u = user()
console.log(u.getFullName()) Jo hh
console.log(u.getFullName.call(lewis)) ss hh

const timer = {
  title: ‘TIMER’,
  timeout() {
    console.log(this.title)
  }
}
timer.timeout()	TIMER

const timer = {
  title: ‘TIMER’,
  timeout() {
    console.log(this.title)
    setTimeout(() => {
      console.log(this.title)
    }, 1000)
  }
}
timer.timeout()	TIMER

setTimeout() 안에 title이 정의 되어있으면 일반함수로 가능하지만
없기 때문에 화살표 함수로 밖에 나가서 title을 가져와서 쓴다
```
