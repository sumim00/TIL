## [etc] 웹 동작방식

![](https://sumim00.github.io/img/in-post/2019/1101_img01.png)



#### 웹 클라이언트 (Web Client)

- 웹 서버에 정보를 요청하는 프로그램
- HTTP를 이용하여 웹 서버에 정보를 요청한다.
- 일반적으로 웹 브라우저를 웹 클라이언트라고 일컫는다.
- 종류: 크롬(Chrome), 파이어폭스(Firefox)



#### 웹 서버 (Web Server)

- 웹 클라이언트에 정보를 응답하는 프로그램
- 클라이언트로부터 HTTP요청을 받는다
- 정적 데이터를 처리 (HTML, CSS, JavaScript, 그림 등)
- 이외에도 인증, 정적 컨텐츠 관리, HTTPS지원, 컨텐츠 압축, 가상 호스팅, 대용량 파일 지원, 대역폭 스로틀링 등의 기능을 지원한다.
- 종류: 아파치 웹 서버(Apache Web Server), GWS, IIS



#### 웹 애플리케이션 서버 (Web Application Server, WAS)

- 사용자 컴퓨터나 장치에 웹 애플리케이션을 수행해주는 미들웨어
- 동적 데이터를 처리 (DB조회, 다양한 로직 처리 등)
- 주로 데이터베이스 서버와 같이 수행된다.
- 이외에도 여러 개의 트랜잭션 관리, 데이터베이스 접속 기능 제공.
- 웹 서버의 할 일을 분배하여 서버의 부담을 줄일 수 있고, 동적 컨텐츠의 처리 속도를 빠르게 한다.
- 종류: 아파치 톰캣(Apache Tomcat), 레진(Resin), 제이런(JRun)



#### DB (Data Base)

- 데이터 저장소
- 웹에서 발생한 데이터를 저장한다.
- 클라이언트의 요청에 맞는 데이터 정보를 보내거나, 반대로 클라이언트에서 보내온 데이터를 입력/수정한다.
- 종류: 오라클(Oracle), MySQL



### Refer

[웹의 동작 방식 - Web 개발 학습하기 | MDN]([https://developer.mozilla.org/ko/docs/Learn/Getting_started_with_the_web/%EC%9B%B9%EC%9D%98_%EB%8F%99%EC%9E%91_%EB%B0%A9%EC%8B%9D](https://developer.mozilla.org/ko/docs/Learn/Getting_started_with_the_web/웹의_동작_방식))

[웹 애플리케이션 서버 - 위키백과, 우리 모두의 백과사전]([https://ko.wikipedia.org/wiki/%EC%9B%B9_%EC%95%A0%ED%94%8C%EB%A6%AC%EC%BC%80%EC%9D%B4%EC%85%98_%EC%84%9C%EB%B2%84](https://ko.wikipedia.org/wiki/웹_애플리케이션_서버))

[웹 애플리케이션 동작 원리 :: 훈마로의 보물창고](<https://hoonmaro.tistory.com/26>)