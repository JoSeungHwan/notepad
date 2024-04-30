# History

### 브라우저 히스토리(세션 기록) 정보를 반환하거나 제어합니다.

<br/>

### .length : 등록된 히스토리 개수

### .scrollRestoration : 히스토리 탐색시 스크롤 위치 볻원 여부 확인 및 지정

### .state : 현재 히스토리에 등록된 데이터(상태)

<br/>

### .back() : 뒤로가기

### .forward() : 앞으로 가기

### . go(위치) : 현재 페이지 기준 툭정 히스토리 '위치'로 이동

<br/>

### .pushState(상태, 제목, 주소) : 히스토리에 상태 및 주소를 추가

### .replaceState(상태, 제목, 주소) : 현재 히스토리의 상태 및 주소를 교체

### > 모든 브라우저(Safari 제외)는 '제목' 옵션을 무시합니다.

```javascript
console.log(history);
```

#### 예제

```HTML
<body>
  <nav>
    <a href="#/page1">p1</a>
    <a href="#/page1">p2</a>
    <a href="#/page1">p3</a>
    <input type="text" />
  </nav>
  <div id="app">
    <section id="/page1" class="page1">
      <h1>Page 1</h1>
    </section>
    <section id="/page2" class="page2">
      <h1>Page 2</h1>
    </section>
    <section id="/page3" class="page3">
      <h1>Page 3</h1>
    </section>
  </div>
</body>
```

```CSS
body {
  margin: 0;
}
nav {
  background-color: white;
  padding: 10px;
  border: 4px solid;
  position: fixed;
  bottom: 0;
  right: 0;
}
nav input {
  width: 50px;
}
section {
  height: 100vh;
  border: 10px solid;
  box-sizing: border-box;
}
section.page1 { color: red; }
section.page2 { color: orange; }
section.page3 { color: green; }
```

```javascript
const page1 = /* html */ `
  <section class="page1">
    <h1>Page 1</h1>
  </section>`

  const page2 = /* html */ `
  <section class="page2">
    <h1>Page 2</h1>
  </section>`

  const page3 = /* html */ `
  <section class="page3">
    <h1>Page 3</h1>
  </section>`

  const pageNotFound = /* html */ `
  <section>
    <h1>404 Page Not Found</h1>
  </section>`

  const pages = [
    { path: '#/page1', template: page1 },
    { path: '#/page2', template: page2 },
    { path: '#/page3', template: page3 }
  ]
  const appEl = document.querySelector('#app')

  const render = () =. {
    //console.log(history)
    const page = pages.find(page => page.path === localtion.hash)
    appEl.innerHTML = page
      ? page.template
      : pageNorFound
  }

  window.addEventListener('popstate', render)
  render()

  const pafePush = num  => {
    history.pushState(`전달할 데이터 = ${num}`, null, `#/page${num}`)
    render()
  }

  const inputEL = document.querySelectoe('nav input')
  inputEl.addEventListener('keydown', event => {
    if (event.key === 'Enter') {
      pagePush(event.target.value)
    }
  })
```
