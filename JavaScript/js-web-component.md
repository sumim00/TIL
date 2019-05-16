## 웹 컴포넌트

컴포넌트란 프로그래밍에 있어 재사용이 가능한 각각의 독립된 모듈을 뜻한다. 

웹 컴포넌트는 컴포넌트 기술을 웹에서도 적용할 수 있도록 W3C에서 새로이 정한 규격이다. 웹 표준을 기반으로 구축되었으며, 최신 브라우저 및 모든 JavaScript 라이브러리, 프레임워크에서도 사용할 수 있는 위젯이다. 따라서 웹 컴포넌트를 이용하여 코드를 작성하면 Vue나 React와 같은 라이브러리, 프레임워크에 의존하지 않고 상호 운용이 가능하게끔 작성할 수 있다.



### 웹 컴포넌트의 규격

- **Shadow DOM** : DOM과 스타일을 캡슐화하여 처리할 수 있도록 함.
- **Custom Elements** : HTML에 새로운 HTML/DOM 요소를 정의함.
- **HTML Templates** : 컴포넌트의 골격이 사용되기 전까지 비활성화된 상태로 관리.  
- **ES Modules** : 이전 규격이었던 HTML Import를 대체하여 나온 규격이며, 자바스크립트로 구현하는 모듈 시스템.

위의 4가지 규격을 함께 사용하는 것이 가장 이상적이지만, 사용하고 싶은 부분만 선택적으로 사용하는 것도 가능하다. 



### 폴리머


구글이 웹 컴포넌트의 규격에 따라 구현한 UI 라이브러리가 폴리머다.
폴리머는 DOM을 템플릿화 하는 것을 목적으로 하며, Material Design을 기반으로 한다. 또한 JavaScript로 만들어졌다.


https://www.polymer-project.org/



### Refer

<https://github.com/w3c/webcomponents> 

<https://d2.naver.com/helloworld/188655> 

<https://developer.mozilla.org/ko/docs/Web/Web_Components> 
