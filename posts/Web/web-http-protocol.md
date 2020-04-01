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

![](https://mdn.mozillademos.org/files/13687/HTTP_Request.png)

- 클라이언트가 서버에게 요청하는 정보가 담겨 있다.
- 메서드 (Method) : 클라이언트가 수행하고자 하는 동작을 나타낸다. 클라이언트가 리소스를 가져오려는 경우는 GET, HTML폼을 이용하여 데이터를 전송하려는 경우에는 POST등이 표시.
- 경로 (Path) : 가져오려는 리소스의 경로. 만약 가고 싶은 url 경로가 https://swimjiy.github.io/2019-11-03-How-Web-Works 이라면 도메인인 https://swimjiy.github.io/를 제외한 리소스의 경로 `/2019-11-03-How-Web-Works` 가 표시된다. 
- 프로토콜 버전 (Version of the protocol) : HTTP 프로토콜의 버전
- 헤더 (Headers) : 서버에 대한 추가 정보를 전달한다.





### HTTP Response

![](https://mdn.mozillademos.org/files/13691/HTTP_Response.png)

- 클라이언트의 요청에 대한 서버의 답변이 담겨 있다.
- 상태줄-헤더-본문
- 프로토콜 버전 (Version of the protocol) : HTTP 프로토콜의 버전
- 상태 코드 (Status code) : 클라이언트 요청의 성공 여부를 숫자로 나타낸다.
- 상태 메시지 (Status message) : 상태 코드를 이해하기 쉽게 영어로 풀어 쓴 메시지
- 헤더 (Headers) : 요청 헤더와 유사한 형식으로 추가 정보를 전달한다.
- 이후에는 가져온 리소스가 포함된 본문이 표시된다.



### Reference

[WEB2 - HTTP - 생활코딩](https://opentutorials.org/course/3385)

[HTTP 개요 - HTTP | MDN](https://developer.mozilla.org/ko/docs/Web/HTTP/Overview)

[[프로토콜] HTTP 프로토콜 이란? - DalkomIT - 티스토리](https://dalkomit.tistory.com/134)

[프런트엔드 개발자가 알아야하는 HTTP 프로토콜 Part 1 ...](https://joshua1988.github.io/web-development/http-part1/)


