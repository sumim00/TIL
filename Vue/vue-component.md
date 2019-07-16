# [Vue.js] 컴포넌트

컴포넌트란 : 재사용 가능한 코드를 캡슐화하기 위한 기능.



#### 전역 등록

```html
<div id="example">
  <my-component></my-component>
</div>
```

```javascript
Vue.component ('my-component', {
    template: '<div>사용자 정의 컴포넌트입니다.</div>'
})

new Vue ({
    el: '#example'
})
```



#### 지역 등록

```javascript
var Child = {
    template: '<div>사용자 정의 컴포넌트입니다.</div>'
}

new Vue ({
    components: {
        'my-component' : Child
    }
})
```



#### 데이터 전달 : props를 이용

```javascript
Vue.component('child', {
    props: ['myMessage'],
    template: '<span>{{ myMessage }}</span>'
})
```

```html
<child my-message="안녕하세요!"></child>
```



#### 데이터 전달 : 동적 props 이용

```html
<div>
    <input v-model="parentMsg">
    <child :my-message="parentMsg"></child>
</div>
```







