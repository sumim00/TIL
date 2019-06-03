# [Vue.js] 라이프사이클

## 라이프사이클이란

JavaScript의 모든 객체는 생성, 갱신, 소멸 등의 일련의 과정을 거친다. Vue.js 또한 객체 중 하나이기에 이와 다르지 않다. `new Vue()`를 통해 생성된 뷰 인스턴스는 여러 가지 상태를 거치는데 이 때 인스턴스의 상태에 따라 호출할 수 있는 속성들을 **라이프사이클(Life Cycle)** , 번역하면 **생명주기** 라고 부른다. 

Vue.js의 라이프사이클은 크게 Creation, Mounting, Updating, Destruction 으로 나눌 수 있고, 이를 전후 2개씩 분류하여 총 8개로 이루어져있다.



![vue라이프사이클 다이어그램](https://kr.vuejs.org/images/lifecycle.png)



## Creation : 컴포넌트 초기화 단계

라이프사이클 가장 초기에 실행되는 단계. 컴포넌트가 DOM에 추가되기 전의 상태이다. 서버렌더링에서 지원되는 훅



## Mounting : DOM 삽입 단계

서버렌더링에서 지원하지 않는다.



## Updating : Diff 및 재렌더링 단계

컴포넌트에서 사용되는 반응형 속성들이 변경되거나 재렌더링이 발생하면 실행되는 단계. 서버렌더링에서는 호출되지 않는다.



## Distruction : 해체 단계

인스턴스가 제거되는 단계.



## Refer

[Vue.js 2.0 라이프사이클 이해하기 – Witinweb – Medium]([https://medium.com/witinweb/vue-js-%EB%9D%BC%EC%9D%B4%ED%94%84%EC%82%AC%EC%9D%B4%ED%81%B4-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0-7780cdd97dd4](https://medium.com/witinweb/vue-js-라이프사이클-이해하기-7780cdd97dd4))