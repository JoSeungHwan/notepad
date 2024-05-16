# 문자

```javascript
let str: string;
let red: string = 'Red';
let green: string = 'Green';
let myColor: string = `My color is ${red}`;
let yourColor: string = 'Tour color is' + green;
```

# 숫자

```javascript
let num: number;
let integer: number = 6;
let float: number = 3.14;
let infinity: number = Infinity;
let nan: number = NaN;
```

# 불린

```javascript
let isBoolean: boolean;
let isDone: boolean = false;
```

# Null / Undefined

```javascript
let nul: null;
let nud: nudefined;
```

# 배열

```javascript
const fruits: string[] = ['Apple', 'Banana', 'Cherry'];
const numbers: number[] = [1, 2, 3, 4, 5, 6, 7];
const nuion: (string | numder)[] = ['Apple', 1, 2, 'Banana', 3];
```

# 객체

### typeof DATA === ' object'

```javascript
const obj: object = {}
const arr: object = []
const func: object = function () {}

const userA: {
  name: string
  age: number
  isValid: boolean
} = {
  name: 'Jo'
  ahe: 29
  isValid: true
}
```

```javascript
interface User {
  name: string
  age: number
  isValid: boolean
}
const userA: User = {
  name: 'Jo'
  ahe: 29
  isValid: true
}
```

# 함수

```javascript
const add: (x: number, y: number) => number = function (x, y) {
  return x + y;
};
const a: number = add(1, 2);

const hello: () => void = function () {
  console.log('Hello world');
};
const h: void = hello();
```

```javascript
const add = function (x: number, y: number): number {
  return x + y;
};
const a: number = add(1, 2);

const hello = function (): void {
  console.log('Hello world');
};
const h: void = hello();
```
