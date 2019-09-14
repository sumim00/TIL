# Nuxt.js

### [Nuxt.js](<https://ko.nuxtjs.org/>)란?

Vue.js의 SSR 프레임워크.

Vue.js는 기본적으로 SPA 방식을 사용하는데, Vue.js를 사용하면서 동시에 SSR가 필요한 경우 Nuxt.js 프레임워크를 사용할 수 있다.



### SSR(Server Side Rendering) 이란?

모든 템플릿이 서버 연산을 통해 렌더링되는 과정을 일컫는다. 필요한 리소스만 갱신하는 SPA(Single Page Application)과는 달리 서버로부터 완성된 형태의 템플릿만을 전달받기 때문에 검색엔진 최적화(SEO)가 가능하다는 장점이 있다.



### 장점

- Vue.js 애플리케이션을 서버사이드 렌더링 방식으로 만들 수 있다.
- 필요한 디렉토리 구조를 미리 설정하여 쉽고 편리한 개발이 가능하다.
- `nuxt generate` 를 통해 Vue.js 어플리케이션을 정적으로 생성할 수 있다.



### 시작하기

공식 문서에서는 두 가지 방법이 나와있다.

##### 1. Nuxt.js Starter 템플릿 사용

```powershell
$ vue init nuxt-community/starter-template <project-name>

or

$ npm install -g @vue/cli @vue/cli-init
```

```powershell
$ cd <project-name>
$ npm install
```

```powershell
$ npm run dev
```



##### 2. Nuxt.js만 단독 설치

```powershell
$ mkdir <project-name>
$ cd <project-name>
```

package.json

```json
{
  "name": "my-app",
  "scripts": {
    "dev": "nuxt"
  }
}
```

```powershell
$ npm install --save nuxt
```

```powershell
$ mkdir pages
```

pages/index.vue
```powershell
<template>
  <h1>Hello world!</h1>
</template>
```

```powershell
$ npm run dev
```





### 디렉토리 구조

`Vue.js CLI`를 이용하여 Vue.js 환경을 세팅하게 되면 사용 목적에 맞게 디렉토리 구조가 미리 짜여진 것을 볼 수 있는데, `Nuxt.js` 또한 마찬가지로 설치하게 되면 정해진 디렉토리 구조로 스캐폴딩이 되어있다.

```javascript
┌ Assets/			// css, image 등 webpack으로 처리할 에셋들을 포함
├ Components/		// Vue.js 컴포넌트를 포함
├ Layouts/			// 애플리케이션의 레이아웃 포함
├ Middleware/		// 미들웨어를 포함
├ Pages/			// 뷰가 포함되며, 구조에 따라 router가 자동으로 생성
├ Plugins/			// javaScript 플러그인을 포함
├ Static/			// 변환되지 않을 정적 파일들을 포함
├ Store/			// Vuex Store 파일을 포함
├ nuxt.config.js	// Nuxt.js의 사용자 설정을 포함
└ pakage.json
```





### 명령어

| 명령어        | 설명                                                         |
| ------------- | ------------------------------------------------------------ |
| nuxt          | 개발서버를 핫 리로딩 상태로 [localhost:3000](http://localhost:3000/)에 시작한다. |
| nuxt build    | Webpack을 통해 어플리케이션을 빌드한다.                      |
| nuxt start    | 프로덕션(배포) 모드로 서버를 시작한다.                       |
| nuxt generate | 정적 호스팅에 사용. 어플리케이션을 `build`폴더에 HTML 파일의 형태로 빌드한다. |

`package.json`에 다음과 같이 명령문들을 추가하면 `npm run <command>` 명령어를 통해 서버를 시작할 수 있다.

```json
"scripts": {
  "dev": "nuxt",
  "build": "nuxt build",
  "start": "nuxt start",
  "generate": "nuxt generate"
}
```



## Refer

[Nuxt.js 공식 문서](<https://ko.nuxtjs.org/>)

[아하 프론트 개발기(1) — SPA와 SSR의 장단점 그리고 Nuxt.js - aha.official - Medium]([https://medium.com/aha-official/%EC%95%84%ED%95%98-%ED%94%84%EB%A1%A0%ED%8A%B8-%EA%B0%9C%EB%B0%9C%EA%B8%B0-1-spa%EC%99%80-ssr%EC%9D%98-%EC%9E%A5%EB%8B%A8%EC%A0%90-%EA%B7%B8%EB%A6%AC%EA%B3%A0-nuxt-js-cafdc3ac2053](https://medium.com/aha-official/아하-프론트-개발기-1-spa와-ssr의-장단점-그리고-nuxt-js-cafdc3ac2053))

[Nuxt.js 개념부터 설치까지 빠르게 배우기 - Dev. DY](<https://kdydesign.github.io/2019/04/10/nuxtjs-tutorial/>)