## [Vue.js] 템플릿 문법



### **Mustache 템플릿 문법** 

좌우 구분자로 사용하는 이중 중괄호 기호가 콧수염 모양같아서 붙여진 이름이다.

{{  }} 사이에 변수 이름을 입력하면 해당 변수에 해당하는 데이터를 불러와 [HTML 이스케이프][1]로 출력된다. HTML 이스케이프 되지 않는 문자열을 출력하고 싶다면 {{{ }}} 문법을 사용하면 된다.

```vue
<template>
    <div id="app">
        Hello {{ message }}
    </div>
</template>

<script>
export default {
    data() {
        return {
            message: 'Vue.js'
        }
    }
}
</script>

```



### Refer

<https://kr.vuejs.org/v2/guide/syntax.html> 

<http://cigiko.cafe24.com/vue-js-%EB%B7%B0-%ED%85%9C%ED%94%8C%EB%A6%BF/> 



[1]: 특정 문자를 HTML로 변환하는 행위. `&lt;` 를 입력하면 `<`특수기호가 나오는 현상을 예로 들 수 있다.