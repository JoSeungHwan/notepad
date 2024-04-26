# 배열

## ./length

`./length` 배열의 길이(숫자)를 반환합니다.

```javascript
const arr = ['A', 'B', 'C']

console.log(arr.length) 출력 : 3
```

## .at()

`at()` 대상 배열을 인덱싱합니다.<br/>
음수 값을 사용하면 뒤에서 인덱싱합니다.

```javascript
const arr = ['A', 'B', 'C']

console.log(arr[0]) 출력 : A
console.log(arr.at[0])  출력 : A

console.log(arr[arr.length - 1])  출력 : C
console.log(arrat[-1])  출력 : C

```

## .concat()

`concat()` 개상 배열과 주어진 배열을 병합해 새로운 배열을 반환합니다.

```javascript
const arr1 = ['A', 'B', 'C']
const arr2 = ['D', 'E', 'F']
const arr3 = arr1.concat(arr2)
const arr4 = [...arr1, ...arr2]

console.log(arr1) 출력 : A B C
console.log(arr2) 출력 : D E F
console.log(arr3) 출력 : A B C D E F
console.log(arr4) 출력 : A B C D E F
```

## .every()

`evert()` 대상 배열의 모든 요소가 콜백 테스트에서 참(Truthy)을 반환하는지 확인합니다.

```javascript
const arr = [1, 2, 3, 4]
const isValid = arr.every(item => item < 5)

console.log(isValid)  출력: true
```

## .filter()

`filter()` 주어진 콜백 테스트를 통과(참을 반환)하는 모든 요소를 새로운 배열로 반환합니다.<br/>
모든 요소가 테스트를 통과하지 못하면 빈 배열을 반환합니다.

```javascript
const numbers = [1, 20, 7, 9, 104, 0, 58]
const filteredNumbers = numbers.filter(number => number < 30)

console.log(filteredNumbers)  출력 : 1 20 7 9 0
```

```javascript
const users = [
  { name: 'Neo', age: 85 },
  { name: 'Amy', age: 22 },
  { name: 'Lewis', age: 11 },
]
const adults = users.filter(user => {
  return user.age >= 19
})
console.log(adults) 출력 : Neo 85, Amy 22
```

## .find()

`find()` 대상 배열에서 콜백 테스트를 통과하는 첫 번째 요소를 반환합니다.

```javascript
const arr = [5, 8, 130, 12, 44]
const foundItem = arr.find(item => item > 10)

console.log(foundItem)  출력 : 130
```

```javascript
const users = [
  { name: 'Neo', age: 85 },
  { name: 'Amy', age: 22 },
  { name: 'Lewis', age: 11 },
]
const foundIUser = users.find(user => {
  return user.name >= 'Amy'
})
console.log(foundUser) 출력 : Amy 22
```

## .findIndex()

`findIndex()` 대상 배열에서 콜백 테스트를 통과하는 첫 번쨰 요소의 인덱스를 반환합니다.

```javascript
const arr = [5, 8, 130, 12, 44]
             0  1  2    3   4
const index = arr.findIndex(iten => item > 10)
console.log(index)  출력 : 2(숫자)

```

## .flat()

`flat()` 대상 배열의 모든 하위 배열을 지정한 깊이까지 이어붙인 새로운 배열을 생성합니다.<br/>
깉이의 기본값은 '1'입니다.

```javascript
const arr = [1, 2, [3, 4]]

console.log(arr.flat()) 출력 : 1 2 3 4
console.log(arr)  출력 : 1 2 Array(2)
```

```javascript
const arr = [1, 2, [3, 4, [5, 6]]]

console.log(arr.flat()) 출력 : 1 2 3 4 [5, 6]
console.log(arr.flat(2)) 출력 : 1 2 3 4 5 6
console.log(arr.flat(Infinity)) 출력 : 1 2 3 4 5 6
```

## .forEach()

`forEach()` 대상 배열의 길이만큼 주어진 콜백을 실행합니다.

```javascript
const arr = ['A', 'B', 'C']

arr.forEach(utem => console.log(item))  출력 : A B C A B C (줄바꿈)

for (let i = 0; i < arr.length; i += 1) {
  console.log(arr[i])
}
```

## .includes()

`includes()` 대상 배열이 특정 요소를 포함하고 있는지 확인합니다.

```javascript
const arr = [1, 2, 3]

console.log(arr.includes(2))  출력 : true
```

```javascript
const users = [
  { name: 'Neo', age: 85 },
  { name: 'Amy', age: 22 },
  { name: 'Lewis', age: 11 },
]
console.log(users.includes({ name: 'Neo', age: 85 })) 출력 : false

const neo = users[0]
console.log(users.includes(neo))  출력 : true
```

## .join()

`join()` 대상 배열의 모든 요소를 구분자로 연결한 문자를 반환합니다.

```javascript
const arr = ['Apple', 'Banana', 'Cherry']

console.log(arr.join()) 출력 : Apple,Banana,Cherry
console.log(arr.join(', ')) 출력 : Apple, Banana, Cherry
console.log(arr.join('/')) 출력 : Apple/Banana/Cherry
```

## .map()

`map()` 대상 배열의 길이만큼 주어진 콜백을 실행하고, 콜백의 반환 값을 모아 새로운 배열을 반환합니다.

```javascript
const numbers = [1, 2, ,3, 4]
const newNumbers = numbers.mao(item => item * 2)

console.log(newNumbers) 출력 : 2, 4, 6, 8
```

```javascript
const users = [
  { name: 'Neo', age: 85 },
  { name: 'Amy', age: 22 },
  { name: 'Lewis', age: 11 },
]
const newUsers = users.map(user => {
  return {
    ...user,
    isValid: true,
    emaol: null
  }
})

console.log(newUsers) 출력 : {name: 'Neo', age: 85, isValid: true, email: null}, {name: 'Amy', age: 22, isValid: true, email: null}, {name: 'Lewis', age: 11, isValid: true, email: null}
```

## .pop()

`pop()` 대상 배열에서 마지막 요소를 제거하고 그 요소를 반환합니다.<br/>
대상 배열 원본이 변경됩니다.

```javascript
const fruits = ['Apple', 'Banana', 'Cherry']

console.log(fruits.pop()) 출력 : Cherry
console.log(fruits) 출력 : Apple Banana
```

## .push()

`push()` 대상 배열의 마지막에 하나 이상의 요소를 추가하고, 배열의 새로운 길이를 반환합니다.<br/>
대상 배열 원본이 변경됩니다.

```javascript
const fruits = ['Apple', 'Banana', 'Cherry']

const newLength = fruits.push('Orange')
console.log(newLength) 출력 : 4
console.log(fruits) 출력 : Apple Banana Cherry Orange

fruits.push('Mango', 'Strawberry')
console.log(fruits) 출력 : Apple Banana Cherry Orange Mango Strawberry
```

## .reduce()

`reduce()` 대상 배열의 길이만큼 주어진 콜백을 실행하고, 마지막에 호출되는 콜백의 반환 값을 반환합니다.<br/>
각 콜백의 반환 값은 다음 콜백으로 전달됩니다.

```javascript
const numbers = [1, 2, 3]
const sum = numbers.reduce((accumulator, currentValue) => {
  return accumulator + currentValue
}, 0)

console.log(sum)  출력 : 6
```

```javascript
const numbers = [1, 2, 3, 4, 5, 6]
const sum = numbers.reduce((accumulator, currentValue) => {
  return accumulator + currentValue
}, 0)

console.log(sum)  출력 : 21
```

```javascript
const users = [
  { name: 'Neo', age: 85 },
  { name: 'Amy', age: 22 },
  { name: 'Lewis', age: 11 },
]
const totalAge = users.reduce((acc, cur) => {
  return acc + cur.age
}, 0)
console.log(totalAge) 출력 : 118

const namesArray = users,reduce((acc, cur) => {
  acc.push(cur,name)
  return acc
}, [])
const names = namesArray.join(', ')
console.log(names)  출력 : Neo Amy Lewis
```

## .reverse()

`reverse()` 대상 배열의 순서를 반전합니다.<br/>
대상 배열 원본이 변경됩니다.

```javascript
const arr = ['A', 'B', 'C']
const reversed = arr.reverse()

console.log(reversed) 출력 : C B A
console.log(arr)  출력 : C B A
```

## .shift()

`shift()` 대상 배열에서 첫 번쩨 요소를 제거하고, 제거된 요소를 반환합니다.<br/>
대상 배열 원본이 변경됩니다.

```javascript
const arr = ['A', 'B', 'C']

console.log(arr.shift())  출력: A
console.log(arr)  출력 : B C
```

## .slice()

`slice()` 대상 배열의 일부를 추출해 새로운 배열을 반환합니다.<br/>
두 번째 인수 직전까지 추출하고, 두 번쨰 인수를 생략하면 대상 배열의 끝까지 추출합니다.

```javascript
const arr = ['A', 'B', 'C', 'D', 'E', 'F', 'G']

console.log(arr.slice(0, 3))  출력 : A B C
console.log(arr.slice(4, -1)) 출력 : E F
console.log(arr.slice(4)) 출력 : E F G
console.log(arr)  출력 : A B C D E F G
```

## .some()

`some()` 대상 배열의 어떤 요소라도 콜백 테스트를 톨과하는지 확인합니다.

```javascript
const arr = [1, 2, 3, 4]
const isValid = arr.some(item => item > 3)

console.log(isValid)  출력 : true
```

## .sort()

`sort` 대상 배열을 콜백의 반환 값(음수, 양수, 0)에 따라 정렬합니다.<br/>
콜백을 제공하지 않으면 ,요소를 문자열로 변환하고 유니코드 코드 포인트 순서로 정렬합니다.<br/>
대상 배열 원본이 변경됩니다.

```javascript
const numbers = [4, 17, 2, 103, 3, 1, 0]

numbers,sort()
console.log(numbers)   출력 : 0 1 103 17 2 3 4

numbers.sort((a, b) => a - b)
console.log(numbers)  출력 : 0 1 2 3 4 17 103

numbers.sort((a, b) => b - a)
console.log(numbers)  출력 : 103 17 4 3 2 1 0
```

```javascript
const users = [
  { name: 'Neo', age: 85 },
  { name: 'Amy', age: 22 },
  { name: 'Lewis', age: 11 },
]

users.sort((a,b) => a.age - b.age)
console.log(users)  출력 : Lewis, 11 Amy, 22 Neo, 85
```

## .splice()

`splice()` 대산 배열에 요소를 추가하거나 삭제하거나 교체합니다.<bt/>
대상 배열 원본이 변경됩니다.

```javascript
const arr = ['A', 'B', 'C']
arr.splice(2, 0, 'X')

console.log(arr)  출력 : A B X C
```

```javascript
const arr = ['A', 'B', 'C']
arr.splice(1, 1) (두번째 인수는 삭제하는것)

console.log(arr)  출력 : A C
```

## .unshift()

`unshift()` 새로운 요소를 대상 배열의 맨 앞에 추가하고 새로운 배열의 길이를 반환합니다.<br/>
대상 배열 원본이 변경됩니다.

```javascript
const arr = ['A', 'B', 'C']

console.log(arr.unshift('X')) 출력 : 4
console.log(arr)  출력 : X A B C
```

## .Array.from()

`Array.from()` 유사 배열(array-like)을 실제 배열로 반환합니다.

```javascript
const arraylike = {
  0: 'A'
  1: 'B'
  2: 'C'
  length: 3
}

console.log(arraylike.constructor === Array)  출력 : false
console.log(arraylike.constructor === Object) 출력 : true

Array.from(arraylike).forEach(itm => console.log(item)) 출력 : A B C (줄바꿈)
```

## .Array.isArray()

`Array.isArray()` 배열 데이터인지 확인합니다.

```javascript
const array = ['A', 'B', 'C']
const arraylike = {
  0: 'A'
  1: 'B'
  2: 'C'
  length: 3
}

console.log(Array.isArray(array)) 출력 : true
console.log(Array.isArray(arraylike)) 출력 : false
```
