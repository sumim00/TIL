## [Web] HTTP

#### HTTP란?

- HyperText Transfer Protocol의 약자이며, 웹상에서 정보를 주고받을 수 있는 프로토콜
- 클라이언트와 서버 사이에 이루어지는 요청/응답(request/response) 프로토콜이다.



#### HTTP 메시지 포맷

- ASCII 메시지로 이루어져 있다.
- 클라이언트가 서버에게 보내는 **요청메시지**와 서버가 보내는 **응답메시지**가 있다.



#### 요청메시지

- 구성요소 : 요청내용 / 헤더 / 빈줄 / 기타 메시지



#### 응답메시지

- 구성요소 : 상태표시 / 헤더 / 빈줄 / 기타 메시지



#### HTTP/1.1과 HTTP/2의 차이점

- HTTP/1.1의 문제점
  - 무거운 Header 구조
  - 연결당 하나의 요청과 응답을 처리

- HTTP/2에서 개선된 특징
  - HTTP 헤더 필드의 데이터 압축
  - 서버 푸시 기술
  - 요청을 HTTP 파이프라인으로 처리
  - HTTP 1.1의 HOL(Head Of Line) Blocking 문제 해결
  - TCP 연결 하나로 여러 요청을 다중화 처리



### Refer

[HTTP 개요 - HTTP | MDN](https://developer.mozilla.org/ko/docs/Web/HTTP/Overview)

[HTTP - 위키백과, 우리 모두의 백과사전](<https://ko.wikipedia.org/wiki/HTTP>)

[HTTP/2 소개 | Web Fundamentals | Google Developers](https://developers.google.com/web/fundamentals/performance/http2/?hl=ko)