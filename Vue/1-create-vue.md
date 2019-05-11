## [Vue.js] 1. 설치 및 빌드하기

### CDN

: 해당 코드를 스크립트 라인에 추가하여 jQuery처럼 사용.

```html
<script src="https://unpkg.com/vue@2.6.10/dist/vue.js"></script>
```



### CLI

: cmd창에 직접 입력하여 프로젝트 폴더 패키지를 생성

vue를 전역으로 설치

```powershell
npm install -g @vue/cli
# OR
yarn global add @vue/cli
```



프로젝트 폴더 생성

```powershell
vue create my-project
# OR
vue ui
```



생성된 my-project 폴더 디렉토리

```
┌ node_modules
├ public
├ src
├ .gitignore
├ babel.config.js
├ package-lock.json
├ pakage.json
└ README.md
```



로컬 서버에서 실행하기

```powershell
npm run serve
# OR
yarn serve
```



라우터 설치하기

```powershell
vue add router
# OR
npm install vue-router
```



빌드하기

```powershell
npm run build
```

