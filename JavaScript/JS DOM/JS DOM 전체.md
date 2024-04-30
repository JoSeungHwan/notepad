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

# 검색과 탐색

```HTML
<body>
  <div class="parent">
    <!-- 주석 -->
    <div class="child">1</div>
    텍스트1
    <div id="child2" class="child">2</div>
    텍스트2
  </div>
</body>
```

## document.getElementById()

### HTML 'id' 속성 값으로 검색한 요소를 반환합니다.

### 여러 요소가 검색되면, 가장 먼저 찾은 요소만 반환합니다.

### 검색 결과가 없으면, 'null'을 반환합니다.

```javascript
const el = document.getElementById('child2')
console.log(el)   출력 : <div id="child2" class="child">2</div>
```

## document.querySelector()

### 'CSS 선택자'로 검색한 요소를 하나 반환합니다.

### 여러 요소가 검색되면, 가장 먼저 찾은 요소만 반환합니다.

### 검색 셜과가 없으면, 'null'을 반환합니다.

```javascript
const el = document.quertSelector('.child:first-child')
console.log(el)   출력 : <div class="child">1</div>
```

## document.quertSelectorAll()

### 'CSS 선택자'로 검색한 모든 요소를 'NodeList'로 반환합니다.

### 'NodeList' 객체는 `.firEach()`를 사용할 수 있습니다.

```javascript
const nodeList = ## document.quertSelector('.child')
console.log(nodeList)   출력 : div.child, div.child2
noseList.forEach(el => console.log(el.textContent))   출력 : 1, 2 (줄바꿈)

console.log(Array.from(nodeList))   출력 : div.child, div.child2 (배열로 출력)
```

## N.parentElement

### 모드의 부모 요소를 반환합니다.

```javascript
const el = document.querySelector('.child')
console.log(el.parentElement)   출력 : <div class="parent"></div>
```

## E.closest()

### 자신을 포함한 조상 요소 중 'CSS 선택자'와 일치하는

### 가장 가까운 요소를 반환합니다.

### 요소를 찾지 못하면, 'null'을 반환합니다.

```javascript
const el = document.querySelector('.child')

console.log(el.closest('div'))      출력 : <div class="child">1</div>
console.log(el.closest('body'))     출력 : <body cz-shortcut-listen="true"></body>
console.log(el.closest('.hello'))   출력 : null
```

## N.previousSibling / N.nextSibling

### 노드의 이전 형제 혹은 다음 형제 노드를 반환합니다.

```javascript
const el = document.querySelector('.child')
console.log(el.previousSibling)   출력 : #text
console.log(el.nextSibling)       출력 : " 텍스트1 "
```

## E.previousElementSibling / E.nextElementSibling

### 요소의 이전 형제 혹은 다음 현제 요소를 반환합니다.

```javascript
const el = document.querySelector('.child')
console.log(el.previousElementSibling)    출력 : null
console.log(el.nextElementSibling)        출력 : <div id="child2" class="child">2</div>
```

## E.children

### 요소의 모든 자식 요소를 반환합니다.

```javascript
const el = document.querySelector('.parent')
console.log(el.children)    출력 : div.child, div.child2

console.log(Array.from(el.children)) 배열로 출력할수잇다
```

## E.firstElementChild / E.lastElementChild

### 요소의 첫 번째 자식 혹은 마지막 자식 요소를 반환합니다.

```javascript
const el = document.querySelector('.parent')
console.log(el.firstElementChild)   출력 : <div class="child">1</div>
console.log(el.lastElementChild)    출력 : <div id="child2" class="child">2</div>
```

# 생성, 조회, 수정

```HTML
<body>
  <div class="parent">
    <div class="child">1</div>
    <div class="child">2</div>
  </div>
</body>
```

## document.createElement()

### 메모리에만 존재하는 새로운 HTML 요소를 생성해 반환합니다.

```javascript
const divEl = document.createElement('div')
console.log(divEl)     출력 : <div></div>

const inputEL = document.createElement('input')
console.log(inputEl)    출력 : <input>
```

## E.prepend() / E.append()

### 노드를 요소의 첫 번째 혹은 마지막 자식으로 삽입합니다.

```javascript
const parentEl = document.querySelector('.parent')

const el = document.createElement('div')
el.textContent = 'Hello'

parentEl.prepend(new Comment(' 주석 '))   HTML 첫번쨰에 주석을 추가
parentEl.append(el)       HTML 마지막에 <div>Hello</div> 추가
parentEl.append('Text')   HTML 마지막에 "Text" 추가
```

## E.remove()

### 요소를 제거합니다.

```javascript
const el = document.querySelector('.child')
el.remove()   HTML 맨먼저 찾아진 child클래스를 제거
```

## E.insertAdjacentElement()

### '대상 요소'의 지정한 위치에 '새로운 요소'를 삽입합니다.

### 대상*요소.insertAdjacentElement(위치, 새로운*요소)

```HTML
<!-- ;beforebegin' -->
<div class="target">
  <!-- 'afterbegin' -->
  Content
  <!-- 'beforeend' -->
</div>
<!-- 'afterend' -->
```

```javascript
const childEl = document.querySelector('.child')
const new = document.createElement('span')
newEl.textContent = 'Hello'

childEl.insertAdjacentElement('beforebegin', newEl)
```

하면 이렇게 된다

```HTML
<div class="parent">
  <span>Hello</span>
  <div class="child">1</div>
  <div class="child">2</div>
</div>
```

## N.insertBefore()

### '부모 노드'의 자신인 '참조 노드'의 이전 현제로 '노드'를 삽입합니다.

### 부모*노드.insertBefore(노드, 참조*노드)

```javascript
const parentEl = document.querySelector('.parent');
const childEl = document.querySelector('.child');
const newEl = document.querySelector('span');
newEl.textContent = 'Hello';

parentEl.insertBefore(newEl, childEl);
```

```HTML
<div class="parent">
  <span>Hello</span>
  <div class="child">1</div>
  <div class="child">2</div>
</div>
```

## N.contains()

### '주어진 노드'가 '노드'의 자신을 포함한 후손인지 확인합니다.

### 노드.contains(주어진\_노드)

```javascript
const parentEl = document.querySelector('.parent');
const childEl = document.querySelector('.child');

console.log(parentEl.contains(childEl)); // true
console.log(document.body.contains(parentEl)); // true
console.log(document.body.contains(childEl)); // true
console.log(document.body.contains(document.body)); // true
console.log(parentEl.contains(parentEl)); // true
console.log(parentEl.contains(document.body)); // false
console.log(childEl.contains(document.body)); // false
```

## N.textContext

### 노드의 모든 텍스트를 얻거나 변경합니다.

```javascript
const el = document.querySelector('.child')
console.log(el.textContent)   출력 : 1
```

## E.innerHTML

### 요소의 모든 HTML 내용을 하나의 문자로 얻거나

### 새로운 HTML을 지정합니다.

```javascript
const el = document.querySelector('.parent')
console.log(el.innerHTML)   출력 : <div class="child">1</div>, <div class="child">2</div>

el.innerHTML = '<span style="color: red;">Hello</span>'
```

```HTML
<body>
  <div class="parent">
    <span style="color: red;">Hello</span>
  </div>
</body>
```

```javascript
el.innerHTML = /* html */ `
<div style="border: 4px solid;">
  <span style="color: red;">Hello</span>
  <span style="color: red;">Hello</span>
</div>`;
```

```HTML
<body>
  <div class="parent">
    <div style="border: 4px solid;">
     <span style="color: red;">Hello</span>
     <span style="color: red;">Hello</span>
    </div>
  </div>
</body>
```

## E.dataset

### 요소의 각 'data-' 속성 값을 얻거나 지정합니다.

```javascript
const el = document.querySelector('.child')
const str = 'Hello world'
const odj = { a:1. b: 2}

el.dataset.helloWorld = str
el.dataset.object = JSON.stringify(obj)

console.log(el.dataset.helloWorld)            출력 : Hello World
console.log(el.dataset.object)                출력 : {"a":1,"b":2}
console.log(JSON.parse(el.dataset.object))    출력 : {a: 1, b: 2}
```

```HTML
<body>
  <div class="parent">
    <div class="child" data-hello-world="Hello world" data-object="{a: 1, b: 2}">1</div>
      <div class="child">2</div>
  </div>
</body>
```

## E.tagName

### 요소의 태그 이름을 반환합니다.

```javascript
const parentEl = document.querySelector('.parent')
const childEl = document.querySelector('.child')
const el = document.querySelector('span')

console.log(parentEl.tagName)       출력 : DIV
console.log(childEL.tagName)        출력 : DIV
console.log(el.tagName)             출력 : SPAN
console.log(document.body.tagName)  출력 : BODY
```

## E.id

### 요소의 'id' 속성 값을 얻거나 지정합니다.

```javascript
const el = document.querySelector('.child')
console.log(el.id)

el.id = 'child1'
console.log(el.id)      출력 : child1
console.log(el)         출력 : <div class="child" id="child1">1</div>
```

## E.className

### 요소의 'class' 속성 값을 얻거나 지정합니다.

```javascript
const el = document.querySelector(".child")
console.log(el.className)         출력 : child

el.className += ' child1 active'
console.log(el.className)         출력 : child child1 active
console.log(el)                   출력 : <div class="child child1 active">1</div>
```
