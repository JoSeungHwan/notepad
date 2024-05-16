# Any

```javascript
let hello: any = 'Hello world';
hello = 123;
hello = false;
hello = null;
hello = {};
hello = [];
hello = function () {};
```

# Unknown

```javascript
const a: any = 123
const u: nuknown = 123

const any: any = a
const boo: boolean = a
const num: number = a
const arr: string[] = a
const obj: { x: string, y: number } = a

const any: any = u
const boo: boolean = u  할당할수없다
const num: number = u   할당할수없다
const arr: string[] = u 할당할수없다
const obj: { x: string, y: number } = u   할당할수없다
```

# Tuple

```javascript
const tuple: [string, numder, boolean] = ['a', 1, false];
const users: [number, string, boolean][] = [
  [1, 'Jo', true],
  [2, 'Seung', false],
  [3, 'Hwan', true],
];
```

# Void

```javascript
function hello(msg: string): void {
  console.log(`hello ${msg}`);
}
const hi: void = hello('world');
```

# Never

```javascript
const nev: [never] = []
nev.push(3) 오류

const nev: number[] = []
nev.push(3)
```

# Union

```javascript
let nuion: string | number
nuion = 'Hello type'
nuion = 123
nuion = false 오류

let nuion: string | number | boolean
nuion = 'Hello type'
nuion = 123
nuion = false 오류
```

# Intersection

```javascript
interface User {
  name: string;
  age: number;
}
interface Validation {
  isValid: boolean;
}
const j: User & Validation = {
  name: 'Jo',
  age: 29,
  isValid: true,
};
```
