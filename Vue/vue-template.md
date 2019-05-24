# [Vue.js] 템플릿 문법

### 템플릿 문법이란

Vue.JS는 렌더링 된 DOM과 Vue 인스턴스의 데이터에 바인딩 할 수 있는 **HTML 기반의 문법**을 제공.

Vue.JS는 내부적으로 템플릿 문법을 가상 DOM으로 리턴하는 render 함수로 컴파일 함.

가상 DOM을 이용하여 최소한의 DOM을 조작하고 성능 부하를 최소화한다.



------



### 템플릿 문법1. 보간법 (Interpolation, 값 대입)

Vue 인스턴스에 있는 데이터를 HTML 템플릿에 표현하기 위해 사용한다.

콧수염을 닮은 Mustache {{ }} 구문을 사용하며, 가장 기본적인 데이터 바인딩 체계.

| Name                   | Code                                                         |
| ---------------------- | ------------------------------------------------------------ |
| Text                   | <p> 메시지 : {{ msg }} </p><p *v-once*> 메시지 한 번만 : {{ msgOnce }} </p> |
| Raw HTML               | <p> Mustache: {{ blueMsg }} </p><p> v-html directive: <span *v-html*="blueMsg"> {{ blueMsg }} </span></p> |
| Attribute              | <p *v-bind*:*id* = "id"> ... </p>                            |
| JavaScript 표현식 사용 | <p> {{ number }} + 1 = {{ number + 1 }} </p><img *v-bind*:*src* = "feel?smile:bad"/><p> Reverse : {{ *reverse**.**split*('')*.**reverse*()*.**join*('') }} </p> |



### Text

{{  }} 사이에 변수 이름을 입력하면 해당 변수에 해당하는 데이터를 불러와 [HTML 이스케이프][1]로 출력된다. HTML 이스케이프 되지 않는 문자열을 출력하고 싶다면 {{{ }}} 문법을 사용하면 된다.

```vue
<template>
    <div id="app">
        Hello {{ msg }}
    </div>
</template>

<script>
export default {
    data() {
        return {
            msg: 'Vue.js'
        }
    }
}
</script>

```

데이터를 변경할 때 내용이 업데이트 되는 것을 막고 싶다면 `v-once` 디렉티브를 사용한다.

```vue
<span v-once>변경되지 않는 내용 : {{ message }}</span>
```



#### Raw HTML (원시 HTML)

Mustache 구문은 HTML이 아닌 일반 텍스트로 데이터를 해석하기 때문에 HTML 태그나 엔티티 기호 등이 데이터가 되면 그대로 출력된다. HTML 이스케이프로 출력해야할 경우엔 `v-html` 디렉티브를 사용한다.

```vue
<p>Using mustaches : {{ rawHTML }}</p>
<p>Using v-html directive <span v-html="rawHTML"></span></p>
```



------



### 디렉티브

Vue에서 제공하는 특별한 속성.   `v- `접두어를 갖는다.

디렉티브의 속성 값이 변경될 때, DOM과 바인딩하여 DOM을 변경하는 역할.

| Name   | Code                                                         |
| ------ | ------------------------------------------------------------ |
| v-if   | <p *v-if* = "seen"> 이제 나를 볼 수 있어요 </p>              |
| v-bind | <a *v-bind*:*href* = "url">...</a><a :*href* = "url">...</a> |
| v-on   | <button *v-on*:*click* = "helloEvent"> … </button><button @*click* = "helloEvent"> ... </button> |
| 수식어 | <form *v-on*:*submit*.*prevent* = "onSubmit"> ... </form>    |



#### v-if

`v-if`는 조건부의 내용에 따라 제거되었다가 새로 생성되고,

`v-show` 우선 렌더링이 되고 `display:block;` `display:none;` CSS 속성을 이용해 감추고 보여진다.

따라서 `v-if`는 토글할 때의 비용이 높고, `v-show` 는 초기 렌더링 비용이 높으므로

자주 바뀐다면 `v-show`, 바뀌지 않는다면 `v-if` 를 권장한다.



#### 전달인자

일부 디렉티브는 콜론으로 표시되는 `전달인자`를 사용할 수 있다. `v-bind`의 경우 엘리먼트의 상태값을 바꿔줄 때 사용하는 디렉티브인데, 제이쿼리의 `attr`와 비슷한 역할이다. `v-on`은 이벤트를 핸들링하는 디렉티브이다. 

```vue
<a v-bind:href="url"...></a>
<a v-on:click="doSomething"> ... </a>
```





#### 수식어

점으로 표시되는 특수 접미사.

가령 `<a>` 요소에는 개발자가 이벤트를 연결하지 않았음에도 특정 경로로 이동시키는 기능을 수행하는데 이를 `기본 이벤트`라고 한다. 이러한 기본 이벤트의 실행을 중지하기 위해 자바스크립트에서는 `preventDefault()` 이벤트 객체를 호출하는데, Vue 이벤트 수식어를 사용하여 이를 대신 호출할 수 있다.

```vue
<form v-on:submit.prevent="onSubmit">...</form>
```





#### 약어

`v-` 접두사는 Vue 특정 속성을 구분하기 위한 시각적인 신호 역할이다. 그러므로 `v-` 접두어의 필요성이 떨어지거나 장황하다고 느낄 때, 약어를 사용한다.

```vue
<!-- 전체 -->
<button v-on:click="doSomething">...</button>
<!-- 약어 -->
<button @click="doSomething">...</button>

<!-- 전체 -->
<a v-bind:href="url">...</a>
<!-- 약어 -->
<a :href="url">...</a>
```





### Refer

[Vue.JS 공식 가이드](<https://kr.vuejs.org/v2/guide/syntax.html> )

[자바스크립트 프레임워크 소개 3 - Vue.js : TOAST Meetup]( <https://meetup.toast.com/posts/99>  )

[Vue.js 입문서 - 프론트엔드 개발자를 위한 : Captain Pangyo](<https://joshua1988.github.io/web-development/vuejs/vuejs-tutorial-for-beginner/>)

[리액트에 대해서 그 누구도 제대로 설명하기 어려운 것 – 왜 Virtual DOM 인가? : Velopert]( <https://velopert.com/3236> )

<http://cigiko.cafe24.com/vue-js-%EB%B7%B0-%ED%85%9C%ED%94%8C%EB%A6%BF/> 

https://takeuu.tistory.com/33



[1]: 특정 문자를 HTML로 변환하는 행위. `&lt;` 를 입력하면 `<`특수기호가 나오는 현상을 예로 들 수 있다.
