# 타입 가드(Guards)

```javascript
function logText(el: Element) {
  console.log(el.textCOntent);
}
const h1El = document.querySelector('h1');
logText(h1El); // 에러 HTMLHeadingElement | null 형식의 인수는 Element 형식의 매개 변수에 할당 될 수 없습니다. null 형식은 Element 형식에 할당할 수 없습니다
```

```javascript
const h1El = document.querySelector('h1');
if (h1El) {
  logText(h1El);
}

const h1El = document.querySelector('h1');
if (h1El instanceof HTMLHeadingElement) {
  logText(h1El);
}
```

```javascript
function add(val: string | number) {
  let res = 'Result => ';
  if (typeof val === 'number') {
    res += val.toFixed(2);
  } else {
    res += val.toUpperCase();
  }
  console.log(res);
}

add(3.141592);
add('hello world');
```

```javascript
function add(val: string | number | boolean) {
  let res = 'Result => ';
  if (typeof val === 'number') {
    res += val.toFixed(2);
  }
  if (typeof val === 'string') {
    res += val.toUpperCase();
  }
  console.log(res);
}

add(3.141592);
add('hello world');
```
