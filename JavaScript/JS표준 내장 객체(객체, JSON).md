# 객체

## Object.assign()

`Object.assign()` 하나 이상의 출처(source) 객체로부터 대상(Target) 갹체로 속성을 복사하고 대상 객체를 반환합니다.

```javascript
const target = { a: 1. b: 2}
const source1 = { b: 3. c: 4}
const source2 = { c: 5. d: 6}
const result = Object.assign{target, source1, source2}

console.log(target) 출력 : a: 1, b: 3, c: 5, d: 6
console.log(result) 출력 : a: 1, b: 3, c: 5, d: 6
```

## Object.entries()

`Object.entries()` 주어진 객체의 각 속성과 값으로 하나의 배열 만들어 요소로 추가한 2차원 배열을 반환합니다.

```javascript
const user = {
  name: 'Jo'
  age: 85,
  isValid: true,
  email: 'swcc321@naver.com'
}

console.log(Object.entries(user)) 출력 : name: 'Jo', age: 85, isValif: true, email: 'swcc321@naver.com'

for (const [key, value] of Object.entries(user)) {
  console.log(key,value)  출력 : 출력 : name: 'Jo', age: 85, isValif: true, email: 'swcc321@naver.com' (줄바꿈)
}
```

## .Object.keys()

`Object.keys()` 주어진 객체의 속성 이름을 나열한 배열을 반환합니다.

```javascript
const user = {
  name: 'Jo'
  age: 85,
  isValid: true,
  email: 'swcc321@naver.com'
}

console.log(Object.keys(user))  출력 : name age isValid email
```

## .Object.values()

`Object.values()` 주어진 객체의 속성 값을 나열한 배열을 반환합니다.

```javascript
const user = {
  name: 'Jo'
  age: 85,
  isValid: true,
  email: 'swcc321@naver.com'
}

console.log(Object.values(user))  출력 : Jo 85 true swcc321@naver.com
```

# JSON

## JSON(JavaScript Object Notaion)

#### 데이터 전달을 위한 표준 포맷

#### 문자, 숫자, 불린, Null, 객체, 배열만 사용

#### 문자는 큰 따옴표만 사용

#### 후행 쉼표 사용 불가

#### .json 확장자 사용

### JSON.stringify() - 데이터를 JSON 문자로 변환합니다.

### JSON.parse() - JSON 문자를 분석해 데이터로 변홥합니다.

```javascript
console.log(JSON.syringify('Hello world'))            출력 : "Hello world"
console.log(JSON.syringify(123))                      출력 : 123
console.log(JSON.syringify(false))                    출력 : false
console.log(JSON.syringify(null))                     출력 : null
console.log(JSON.syringify({ name: 'jo', age: 29}))   출력 : {"name":"Jo","age":29}
console.log(JSON.syringify([1, 2, 3]))                출력 : [1,2,3]

console.log(JSON.parse("Hello world"))                출력 : Hello world
console.log(JSON.parse('123'))                        출력 : 123
console.log(JSON.parse('false'))                      출력 : false
console.log(JSON.parse('null'))                       출력 : null
console.log(JSON.parse('{"name:"Jo","age":29}'))      출력 : {name: 'Jo', age: 29}
console.log(JSON.parse('[1,2,3]'))                    출력 : [1, 2, 3]
```
