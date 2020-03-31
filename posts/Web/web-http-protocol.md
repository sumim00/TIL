# [Web] HTTP 프로토콜

### 웹을 구성하는 4가지 요소

- HTML 언어

- URL 주소체계

- Web browser, Web server 소프트웨어

- HTTP 프로토콜

### HTTP란

- 웹 브라우저와 웹 서버 간에 데이터를 주고받기 위해 사용하는 인터넷 프로토콜.

- 프로토콜이란 상호 간에 정의한 규칙을 의미하며 특정 기기 간에 데이터를 주고받기 위해 정의됨.

### HTTP의 특징

- 클라이언트/서버 모델을 따름.
- TCP/IP 통신 위에서 동작한다.
- connecionless : 연결을 하고 Request를 하고 Response를 보내준 뒤에 접속을 끊는다. 페이지를 이동할 때마다 연결을 반복한다. 서버와 계속해서 통신이 필요한 경우 Ajax나 socket.io등을 사용한다.
- stateless : 통신을 하면 현재 상태가 저장되지 않는다. 쿠키나 세션의 방식이 없다면 로그인 정보가 사라진다.

### HTTP Request

- 클라이언트가 서버에게 요청하는 정보가 담겨 있다.
- 시작줄-헤더-본문



### HTTP Response

- 클라이언트의 요청에 대한 서버의 답변이 담겨 있다.
- 상태줄-헤더-본문



### Reference

[WEB2 - HTTP - 생활코딩](https://opentutorials.org/course/3385)

[HTTP 개요 - HTTP | MDN](https://developer.mozilla.org/ko/docs/Web/HTTP/Overview)

[[프로토콜] HTTP 프로토콜 이란? - DalkomIT - 티스토리](https://dalkomit.tistory.com/134)

[프런트엔드 개발자가 알아야하는 HTTP 프로토콜 Part 1 ...](https://joshua1988.github.io/web-development/http-part1/)


