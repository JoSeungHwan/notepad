# @media

max-width : 최대 넓이<br/>
min-width : 최소 넓이<br/>
opientation: portrait : 가로넓이보다 세로넓이가 더클떄 (스마트폰 사이즈)<br/>
opientation: landscape : 세로넓이보다 가로가 넓을떄 (스마트폰을 눕혔을때)<br/>
<br/>
1000px 이하 : 테블릿 모드<br/>
740px 이하 : 모바일 모드<br/>

# 반응형 코드르 따른 파일로 구분하기

## 파일

main.medium.css<br/>
main.small.css

## HTML

```html
<link rel="stylesheet" href="./css/main.css" />
<link
  rel="stylesheet"
  href="./css/main.medium.css"
  media="“(max-width:1200px)”"
/>
<link
  rel="stylesheet"
  href="./css/main.small.css"
  media="“(max-width:800px)”"
/>
```
