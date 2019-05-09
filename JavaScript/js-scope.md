## 스코프 (Scope)

유효범위라고도 불린다. 변수와 매개변수의 접근성 및 생존기간을 제어하는 범위이다.

크게 전역 스코프 (Global Scope)와 지역 스코프(Local Scope) 로 나뉘며, 지역 스코프는 또다시 함수 스코프 (Function Scope)와 블록 스코프 (Block Scope) 로 분류할 수 있다.
처음에 스코프를 이해하기 어려울 땐 아래의 그림과 같이 변수가 사람의 형태로 있고, 이 변수가 여행할 수 있는 지역 범위를 호스팅이라고 생각했다.

![호스팅 이미지](../img/js-scope.jpg)



#### 전역 스코프 (Global Scope)

변수가 함수 바깥이나 중괄호 `{}` 바깥에 선언되는 경우, 전역 스코프에 정의되었다고 한다. 또한 해당 변수는 전역 변수로서 코드 모든 곳에서 사용이 가능하다.



#### 지역 스코프(Local Scope)

특정 부분에서만 사용이 가능한 경우, 지역 스코프에 있다고 한다. 이러한 변수를 지역 변수라고 부른다. 지역 스코프를 '어느 특정 부분에서' 사용할 수 있는지를 가지고 구분한다면, 함수 스코프 (Function Scope)와 블록 스코프 (Block Scope) 로 나눌 수 있다.



#### 함수 스코프 (Function Scope)

함수 내부에서 변수를 선언한 경우, 그 변수는 함수 스코프에 정의되었다고 한다. 



#### 블록 스코프 (Block Scope)

중괄호`{}` 내부에 `const` 또는 `let` 으로 변수를 선언하면, 해당 함수는 중괄호 내에서만 접근이 가능하다. 블록 스코프는 ES6 부터 지원했기 때문에 var는 함수 스코프 레벨만 지원한다.



## Reference

[자바스크립트의 스코프와 클로저](<https://meetup.toast.com/posts/86> )

[[번역] 자바스크립트 스코프와 클로저(JavaScript Scope and Closures)](<https://medium.com/@khwsc1/%EB%B2%88%EC%97%AD-%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%8A%A4%EC%BD%94%ED%94%84%EC%99%80-%ED%81%B4%EB%A1%9C%EC%A0%80-javascript-scope-and-closures-8d402c976d19> )
