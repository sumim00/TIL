# [Vue.js] 2. Router 설치 및 디렉토리 톺아보기

### CDN

하단 cdn을 html 안에 추가

```html
<script src="https://unpkg.com/vue-router/dist/vue-router.js"></script>
```



### CLI

cmd에 하단 코드를 입력

```powershell
vue add router
# OR
npm install vue-router
```



라우터 설치 후 변경된 my-project 폴더 디렉토리

```powershell
┌ node_modules
├ public
├ src
	├ assets
	├ components
	├ views //추가
		├ About.vue //추가
		├ Home.vue //추가
	├ App.vue
	├ main.js
	└ router.js //추가
├ .gitignore
├ babel.config.js
├ package-lock.json
├ pakage.json
└ README.md
```



### 문법 살펴보기 (vue-cli 모듈 시스템 기준)

src/App.vue

```vue
<template>
	<div id="app">
        <div id="nav">
            <router-link to="/">Home</router-link><!-- 네비게이션 용도 -->
            <router-link to="/about">About</router-link>
        </div>
        <router-view/><!-- 라우트에 맞는 컴포넌트가 이 곳에 렌더링 -->
    </div>
</template>
```



src/views/Home.vue

```vue
<template>
  <div>
    <h1>This is an Home page</h1>
  </div>
</template>
```



src/views/About.vue

```vue
<template>
  <div>
    <h1>This is an about page</h1>
  </div>
</template>
```


src/router.js

```javascript
import Vue from 'vue' //vue와 vue 라우터 import
import Router from 'vue-router'
import Home from './views/Home.vue' //Home 라우터는 상단에서 import

Vue.use(Router) //라우터를 호출

export default new Router({
    mode: 'history',
    base: process.env.BASE_URL,
    routes: [
        {
            path: '/',
            name: 'home',
            component: Home
        },
        {
            path: '/about',
            name: 'about',
            component: () => import('./views/About.vue') //About 라우터는 내부에서 정의
        }
    ] // 라우트를 정의하고 각 컴포넌트와 매치
})
```



### Refer

[Vue 공식 가이드 - 라우터](<https://router.vuejs.org/kr/guide/> )