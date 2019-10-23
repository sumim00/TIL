## [JavaScript] 크로스 도메인 이슈와 CORS



#### 동일 출처 정책?

웹 보안 방식 중 동일 출처 정책 (Same-origin policy) 는 어떤 출처에서 불러온 문서나 스크립트는 출처와 프로토콜, 포트, 호스트가 모두 같아야 한다는 보안 방식이다. 

동일 출처 정책으로 인해 브라우저들은 보안 상의 이유로 동일한 도메인으로만 HTTP 요청을 보낼 수 있고, 때문에 외부 서버에서 요청한 데이터를 정상적으로 받을 수 없다.



#### 크로스 도메인?

크로스 도메인 (Cross Domain)이란 말 그대로 서로 다른 도메인 간의 호출을 뜻한다.

웹사이트에서는 효율성이나 성능 등으로 각 기능별로 여러 서버를 두는 경우가 있기 때문에, 크로스 도메인 이슈가 생기면 필요한 AJAX 통신을 할 수 없다는 문제점이 생긴다.

따라서, CORS를 사용해서 크로스 도메인의 접근을 허용한다.



#### CORS (Cross Origin Resource Sharing)?

CORS란 JavaScript의 **동일 출처 정책**으로 인해 발생하는 **크로스 도메인**의 이슈를 해결하기 위한 매커니즘이다.

브라우저와 서버가 상호 통신하면서 특정 도메인에서 접근하는 것을 허용하며, 순수한 동일 출처 요청보다 더 다양한 자원을 사용할 수 있다는 장점이 있다. 





## Refer

[Same-origin policy - 웹 보안 | MDN](<https://developer.mozilla.org/ko/docs/Web/Security/Same-origin_policy>)

[HTTP 접근 제어 (CORS) - HTTP | MDN](<https://developer.mozilla.org/ko/docs/Web/HTTP/Access_control_CORS>)

[[JavaScript] 크로스 도메인(Cross Domain) - 제씨스토리](<https://jess2.tistory.com/109>)

