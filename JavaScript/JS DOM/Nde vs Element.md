# DOM (Document Object Model)

### DOM이란 HTML 문서를 객체로 표현한 것으로,

### JS에서 HTML을 제어할 수 있게 해줍니다.

```javascript
// DOM API
const elsement = document.querySelector('h1');
console.log(element.textContent);
```

## Node vs Element

### 노드(Node): HTML 요소, 텍스트, 주석 등 모든 것을 의미

### 요소(Element): HTML 요소를 의미

```HTML
<body>
  <div class="parent">
    <!-- 주석 -->
    <div class="child">1</div>
    텍스트1
    <div class="child">2</div>
    텍스트2
  </div>
</body>
```

```javascript
const parent = document.querySelector('.parent')

//부모 요소의 모든 자식 노드 확인!
console.log(parent.childNodes)  출력 : text, comment, text, div.child, text, div.child, text

//부모 요소의 모든 자식 요소 확인!
console.log(parent.children)    출력 : div.child, div.child
```

```javascript
class N {}
class E extends N {}

console.dir(E)                  출력 : class E
console.dir(N)                  출력 : class N
console.dir(E.__proto__)        출력 : class N

console.dir(Element)            출력 : Element()
console.dir(Node)               출력 : Node()
console.dir(Element.__proto__)  출력 : Node()
```
