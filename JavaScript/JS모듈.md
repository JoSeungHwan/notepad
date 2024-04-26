# 모듈(Module)

### 특정 데이터들의 집합(파일)입니다.

## 모듈 가져오기(Improt), 모듈 내보내기(Export)

##### 가져오기

`main.js`

```javascript
import { hello } from './module.js'

console.log(hello)  출력 : Hello World
```

##### 내보내기

`module.js`

```javascript
export const hello = 'Hello World';
```

##### 모듈 가져오기, 내보내기를 사용할려면

`index.html`에서 script 부분에 type="module"을 명시해줘야한다

```html
<script type="module" defer src="./maim.js"></script>
```

## 가져오기와 내보내기 패턴

`main.js`

```javascript
// default로 받아진 모듈을 이름 지정가능(여기선 number로 지정했다 마음대로 변경가능)
import number, { str, arr, hello } from './module.js'

console.log(number) 출력 : 123
console.log(str)    출력 : ABC
console.log(arr)    출력 : {}
console.log(hello)  출력 : hello() {}
```

```javascript
// default로 받아진 모듈을 이름 지정가능(여기선 number로 지정했다 마음대로 변경가능)
// 이름 내보내기도 이름 변경이 가능하다 as
import number, { str as asd, arr as def, hello as ghi } from './module.js'

console.log(number) 출력 : 123
// 바뀐 이름으로 써먹을수 있다
console.log(asd)    출력 : ABC
console.log(def)    출력 : {}
console.log(ghi)  출력 : hello() {}
```

```javascript
// 한번에 가져오기
import * as abc from './module.js'

console.log(abc)  출력 : default: 123, atr: "ABC", arr: Array(0), hello: hello() (배열로 담겨져있다)
```

`module.js`

```javascript
// 기본 내보내기 (default는 한번만 쓸수있다)
export default 123;

// 이름 내보내기
export const str = 'ABC';
export const arr = [];
export function hello() {}
```

## 동적으로 모듈 가져오기

`main.js`

```javascript
// 1초후에 모듈 가져오기
setTimeout(() => {
  import('./module.js').then(abc => {
    console.log(abc)  1초뒤 출력 : default: 123, atr: "ABC", arr: Array(0), hello: hello() (배열로 담겨져있다)
  })
}, 1000)
```

```javascript
// 1초후에 모듈 가져오기
setTimeout(async () => {
  const abc = await import('./module.js')
  console.log(abc)  1초뒤 출력 : default: 123, atr: "ABC", arr: Array(0), hello: hello() (배열로 담겨져있다)
}, 1000)
```

`module.js`

```javascript
// 기본 내보내기 (default는 한번만 쓸수있다)
export default 123;

// 이름 내보내기
export const str = 'ABC';
export const arr = [];
export function hello() {}
```

## 가져온 모듈 바로 내보내기

`maon.js`

```javascript
impport { a, b } from './utils.js'
```

`utils.js`

```javascript
export { a } from './a.js';
export { b } from './b.js';
```

`a.js`

```javascript
export const a = () => 123;
```

`b.js`

```javascript
export const b = () => 456;
```
