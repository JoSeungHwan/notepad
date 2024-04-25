# 기본

```html
<div>
  <ul>
    <li>사과</li>
    <li>딸기</li>
    <li>오렌지</li>
  </ul>
  <div>당근</div>
  <p>토마토</p>
  <span>오렌지</span>
</div>
```

# \* : 전체 선택자 (Universal Select) 모든 요소를 선택

```html
* { color: red; } 사과 딸기 오렌지 당근 토마토 오렌지 다 선택
```

# ABC : 태그 선택자 (Type Selector) 태그 이름이 ABC인 요소를 선택

```html
li { color: red; } 사과 딸기 오렌지 선택
```

# .ABC : 클래스 선택자(Class Selector) HTML class 속성의 값이 ABC인 요소 선택

```html
.orange { color: red; }
<li class="“orange”">오렌지</li>
이런식으로 클래스 들어간곳만 선택
```

# #ABC : 아이디 선택자 (ID Selector) HTML id 속성의 값이 ABC인 요소 선택

```html
#orange { color: red; }
<li id="“orange”" class="“orange”">오렌지</li>
이런식으로 아이디들어간곳만 선택
```

# 복합

# ABCXYZ : 일치 선택자 (Basic Combinator) 선택자 ABC와 XYZ를 동시에 만족하는 요소 선택

```html
span.orange { color: red; } <span class="“orange”">오렌지</span> span과 orange
둘다 있는 요소 선택
```

# ABC > XYZ : 자식 선택자 (Child Combinator) 선택자 ABC의 자식 요소 XYZ 선택

```html
ul > .orange { color: red; }
<li class="“orange”">오렌지</li>
li이 부모고 .orange자식일때 선택
```

# ABC XYZ : 하위(자식) 선택자 (Descendant Combinator) 선택자 ABC의 하위 요소 XYZ 선택 ‘띄어쓰기’ 사 선택자의 기호!

```html
div ,orange { color: red; }
<div>
  <ul>
    <li>사과</li>
    <li>딸기</li>
    <li class="“orange”">오렌지</li>
    선택
  </ul>
  <div>당근</div>
  <p>토마토</p>
  <span class="“orange”">오렌지</span> 선택
</div>
<span class="“orange”">오렌지</span> div안에 class=“orange” 만 선택
```

# ABC+XYZ : 인접 형제 선택자 (Adjacent Sibling Combinator) 선택자 ABC의 다음 형제 요소 XYZ하나를 선택

```html
.orange + li { color: red; }
<ul>
  <li>사과</li>
  <li>딸기</li>
  <li class="“orange”">오렌지</li>
  <li>망고</li>
  선택
  <li>사과</li>
</ul>
<li class="“orange”">오렌지</li>
다음 선택자 한개를 선택
```

# ABC~XYZ : 일반 형제 선택자 (General Sibling Conbinator) 선택자 ABC의 다음 형제 요소 XYZ 모두를 선택

```html
.orange~li { color: red; }
<ul>
  <li>사과</li>
  <li>딸기</li>
  <li class="“orange”">오렌지</li>
  <li>망고</li>
  선택
  <li>사과</li>
  선택
</ul>
<li class="“orange”">오렌지</li>
다음 선택자 모두를 선택
```

# 가상 클래스

# ABC:hover : 가상 클래스 선택자 (pseudo-Classes) HOVER 선택자 ABC 요소에 마우스 커서가 올라가 있는 동안 선택

```html
ABC:hover { color: red; }
```

# ABC:active : 가상 클래스 선택자 (Pseudo-Classes) ACTIVE 선택자 ABC 요소에 마우스를 클릭하고 있는 동안 선택

```html
ABC:active { color: red; }
```

# ABC:focus : 가상 클래스 선택자 (Pseudo-Classes) FOCUS 선택자 ABC 요소가 포커스되면 선택

```html
input:focus { background-color: red; }
```

tabindex 속성을 통해 Focus가 될 수 있는 요소를 만들 수 있습니다  이름에서도 알 수 있듯, Tab 키를 사용해 Focus 할 수 있는 순서를 지정하는 속성입니다<br/>
순서(값)로 -1 이 아닌 다른 값을 넣는 것은 논리적 흐름을 방해하기 때문에 권장하지 않습니다.

# ABC:first-child : 가상 클래스 선택자 (Pseudo-Classes) FIRST CHILD 선택자 ABC가 형제 요소 중 첫째라면 선택

```html
.fruits span:first-child { color: red; }
<div class="“fruits”">
  <span>딸기</span> 선택
  <span>수박</span>
  <div>오렌지</div>
  <p>망고</p>
  <h3>사과</h3>
</div>
첫번째 자식이 span 이라서 조건 부합으로 딸기 선택 .fruits div:first-child {
color: red; }
<div class="“fruits”">
  <span>딸기</span>
  <span>수박</span>
  <div>오렌지</div>
  <p>망고</p>
  <h3>사과</h3>
</div>
첫번째 자식이 span 인데 조건 부적합으로 ? 출력
```

# ABC:last-child : 가상 클래스 선택자 (Pseudo-Classes) LAST CHILD 선택자 ABC가 형제 요소 중 막내라면 선택

```html
.fruits h3:lastcgild { color: red; }
<div class="“fruits”">
  <span>딸기</span>
  <span>수박</span>
  <div>오렌지</div>
  <p>망고</p>
  <h3>사과</h3>
  선택
</div>
```

# ABC:nth-child(n) : 가상 클래스 선택자 (Pseudo-Classes) NTH CHILD 선택자 ABC가 형제 요소 중 (n)째라면 선택

```html
.friuts *:nth-child(2) { color: red; }
<div class="“fruits”">
  <span>딸기</span>
  <span>수박</span> 선택
  <div>오렌지</div>
  <p>망고</p>
  <h3>사과</h3>
</div>
두번째 자식 선택 .friuts *:nth-child(2n) { color: red; }
<div class="“fruits”">
  <span>딸기</span>
  <span>수박</span> 선택
  <div>오렌지</div>
  <p>망고</p>
  선택
  <h3>사과</h3>
</div>
2n = 2x 0x2=0 1x2=2 2x2=4 3x2=6 … 두번째 네번째 여섯번째 … 이렇게 선택 가능
.friuts *:nth-child(2n+1) { color: red; }
<div class="“fruits”">
  <span>딸기</span> 선택
  <span>수박</span>
  <div>오렌지</div>
  선택
  <p>망고</p>
  <h3>사과</h3>
  선택
</div>
2n+1 = 0x2+1=1 1x2+1=3 2x2+1=5 … 2곱하고+1을하기떄문에 첫번쨰 세번째 다섯번째 …
홀수 지정선택 .friuts *:nth-child(n+2) { color: red; }
<div class="“fruits”">
  <span>딸기</span>
  <span>수박</span> 선택
  <div>오렌지</div>
  선택
  <p>망고</p>
  선택
  <h3>사과</h3>
  선택
</div>
n+2 = 0+2=2 1+2=3 2+2=4 … 결과론적으로 두번째 부터 선택
```

# ABC:not(XYZ) 부정 선택자 (Negation) NOT 선택자 XYZ가 아닌 ABC 요소 선택

```html
.fruits *:not(span) {  color: red; }
<div class="“fruits”">
  <span>딸기</span>
  <span>수박</span>
  <div>오렌지</div>
  선택
  <p>망고</p>
  선택
  <h3>사과</h3>
  선택
</div>
span제외하고 선택
```

# 가상 요소

# ABC::before : 가상 요소 선택자 (Pseudo-Elements) BEDORE 선택자 ABC 요소의 내부 앞에 내용(Content)을 삽입 (자주쓰인다)

```html
.box::before { contact: “앞!”; }
<div class="“box”">Content!</div>
출력 : 앞! Content
```

# ABC::after : 가상 요소 선택자 (Pseudo-Elements) AFTER 선택자 ABC 요소의 내부 뒤에 내용(Content)을 삽입

```html
.box::after box{ content: “뒤!”; }
<div class="“box”">Content!</div>
출력 : Content! 뒤!
```

```html
.box::after { content: “”; display: block; ———————— 중요 (위아래 값을 주기위해
꼭 넣어야한다) width: 30px; height: 30px; background-color: red; }
```

# 속성

# [ABC] : 속성 선택자 (Attribute) ATTR 속성 ABC을 포함한 요소 선택

```html
[disabled] { color: red; }
<input type="“text" value="“HEROPY”" />
<input type="“password”" value="“1234”" />
<input type="“text”" value="“ABCD”" disabled /> 선택 disabled이 들어간 3번째가
선택
```

# [ABC=“XYZ] : 속성 선택자 (Attribute) ATTR=VALUE 속성 ABC을 포함하고 값이 XYZ인 요소 선택

```html
[type=“password”] { color: red; }
<input type="“text" value="“HEROPY”" />
<input type="“password”" value="“1234”" /> 선택
<input type="“text”" value="“ABCD”" disabled />
타입이 password인 두번째 선택
```
