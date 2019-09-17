# React.js로 CRUD기능을 가진 노트 SPA 만들기

> [React CURD Example](https://appdividend.com/2018/11/11/react-crud-example-mern-stack-tutorial/) 의 글을 일부 번역/응용하였으며 본고에서 생략되거나 짚고 넘어가지 않은 부분은 원문에서 확인하실 수 있습니다. 
>
> 초보자의 포스트로 오타 및 지적은 댓글 및 메일로 언제든 연락 바랍니다.



## 서론

서론에서는 간단히 사용하는 툴 및 설치에 대해 알아보고자 한다.



## 리액트란?

리액트는 Angular처럼 완성된 프레임워크가 아닌 UI라이브러리라는 점이 특징이다. 리액트는 UI구축을 위한 JavsScript 라이브러리이며 Facebook, Instargram 및 개인 개발자와 기업 커뮤니티에서 관리하고 있다. 공식 문서는 [이 곳](https://reactjs.org/)에서 확인할 수 있다.



## 리액트를 사용하는 이유

1. 빠른 러닝 커브
2. 재사용 가능한 컴포넌트
3. Vertual DOM으로 빠른 렌더가 가능함
4. 간결한 추상화
5. Redux: 복잡한 UI를 위한 상태(State) 관리 라이브러리
6. 훌륭한 개발 도구
7. React Native: Android와 iOS를 위한 크로스 플랫폼 모바일 앱을 구축할 수 있다.



## 사용 스택

- Node.js
- NPM
- yarn
- MongoDB shell version
- MongoDB version
- React.js version



## 0. create-react-app 설치

```powershell
npm install --global yarn
yarn global add create-react-app
```

먼저 [node.js](https://nodejs.org/en/)를 설치하고 cmd창에서 다음과 같이 명령한다. 

리액트는 node.js에 기본적으로 깔려있는 npm만 가지고도 실행이 가능하지만 [yarn](https://yarnpkg.com/en/) 이 npm의 단점을 보완한 패키지 매니저로, 더 빠른 설치가 가능하다고 해서 yarn을 통해  ```create-react-app``` 모듈을 세팅했다.



## 1. 프로젝트 생성

```powershell
npx create-react-app moon-note
cd moon-note
npm start
```

```create-react-app``` 은 ```Babel``` ```Webpack``` 과 같은 추가적인 세팅 없이 바로 리액트를 사용할 수 있도록 페이스북에서 만든 리액트 웹 개발용 모듈이다. 첫 줄의 ```npx```은 npm 패키지를 글로벌로 설치하지 않고 일회성으로 실행할 수 있도록 하는 도구다.

설치가 끝나면 다음과 같이 ```localhost:3000``` 주소로 리액트 프로젝트가 생성되었음을 확인할 수 있다.



![리액트 실행 화면](https://sumim00.github.io/img/in-post/2018/1113_img01.jpg)





## Reference

https://velopert.com/457

https://appdividend.com/2018/11/11/react-crud-example-mern-stack-tutorial/#5_Create_a_backend_on_Nodejs