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





#### position 사용 (ie7+)

1번 방법을 호환성 문제로 사용하지 못할 경우에 쓴다. 하단 footer를 ```position:absolute; bottom:0;```  으로 제어하고 

```css
html,
body {
  margin: 0;
  padding: 0;
  position: relative;
}

.header {
  width: 100%;
  height: 50px;
  background: #ccc;
}

.container {
  height: auto;
  min-height: 100%;
  padding-bottom: 50px;
  background: #999;
}

.footer {
  position: absolute;
  bottom: 0;
  width: 100%;
  height: 50px;
  background: #ddd;
}

```

