## 페이지 최소 높이 100% 맞추는 방법



#### vh 사용 (ie9+)

본문 영역 css에 ```min-height: calc(100vh - 헤더푸터 높이);``` 를 입력하면 본문의 컨텐츠가 적어도 높이 100%를 맞출 수 있다.

```css
html,
body {
  margin: 0;
  padding: 0;
}

.header {
  width: 100%;
  height: 50px;
  background: #ccc;
}

.container {
  height:auto;
  min-height: calc(100vh - 100px);
  background: #999;
}

.footer {
  width: 100%;
  height: 50px;
  background: #ddd;
}

```





#### margin, padding 사용 (ie7+)

1번 방법을 호환성 문제로 사용하지 못할 경우에 쓴다. html, body부터 ```height:100%``` 를 적용하고, 본문(container) 에 ```min-height:100%``` 를 적용한 뒤 header, footer에 맞는 ```margin``` 값을 마이너스로 주고, ```padding``` 값을 추가한다.

```css
* {margin:0; padding:0}
html, body {height:100%}

#wrap {height:100%}
#header {position:relative; height:100px; background:#7bb3c3}
#container {min-height:100%; margin:-100px 0 -70px; background:#fff}
.container_inner {padding:100px 0 70px}
#footer {height:70px; background:#7b8fc3}

```

<script async src="//jsfiddle.net/sumim/n6z3hpd9/1/embed/"></script>
