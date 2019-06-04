# [Vue.js] 라이프사이클

## 라이프사이클이란

어떤 Vue 인스턴스가 생성되면, 미리 사전에 정의된 몇 가지 단계를 거치게 되는데 이를 **라이프사이클(Life Cycle)** , 번역하면 **생명주기** 라고 부른다. 다시 말해, Vue 인스턴스가 생성된 후 우리 눈에 보여지고, 갱신되어 사라지는 일련의 단계를 일컫는 말이다.

Vue.js의 라이프사이클은 크게 생성(Create), 부착(Mount), 갱신(Update), 소멸(Destroy)의 4가지 단계를 거친다.

원하는 단계에서 사용자 정의 기능을 수행하기 위해 Vue는 각 단계마다 훅(Hook)을 사용할 수 있도록 제공했다. 가장 많이 사용하는 훅으로는 `beforeCreate`, `Created`, `beforeMount`, `mounted`, `beforeUpdate`, `updated`, `beforeDestroy`, `destroyed` 총 8개가 있다. 



![vue라이프사이클 다이어그램](https://kr.vuejs.org/images/lifecycle.png)



## Creation : 컴포넌트 초기화 단계

라이프사이클 가장 초기에 실행되는 단계. 컴포넌트가 DOM에 추가되기 전의 상태이다. 서버렌더링에서 지원되는 훅

### beforeCreate

### Created



## Mounting : DOM 삽입 단계

서버렌더링에서 지원하지 않는다.

### beforeMount

### Mounted



## Updating : Diff 및 재렌더링 단계

컴포넌트에서 사용되는 반응형 속성들이 변경되거나 재렌더링이 발생하면 실행되는 단계. 서버렌더링에서는 호출되지 않는다.

### beforeUpdate

### Updated



## Destroy : 해체 단계

인스턴스가 제거되는 단계.

### beforeDestroy

### Destroyed



## Refer

[Vue.js 2.0 라이프사이클 이해하기 – Witinweb – Medium]([https://medium.com/witinweb/vue-js-%EB%9D%BC%EC%9D%B4%ED%94%84%EC%82%AC%EC%9D%B4%ED%81%B4-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0-7780cdd97dd4](https://medium.com/witinweb/vue-js-라이프사이클-이해하기-7780cdd97dd4))

[Vue 라이프사이클 이해하기 - Developer:wormwlrm](<https://wormwlrm.github.io/2018/12/29/Understanding-Vue-Lifecycle-hooks.html>)

[Vue 인스턴스 — Vue.js]([https://kr.vuejs.org/v2/guide/instance.html#%EC%9D%B8%EC%8A%A4%ED%84%B4%EC%8A%A4-%EB%9D%BC%EC%9D%B4%ED%94%84%EC%82%AC%EC%9D%B4%ED%81%B4-%ED%9B%85](https://kr.vuejs.org/v2/guide/instance.html#인스턴스-라이프사이클-훅))