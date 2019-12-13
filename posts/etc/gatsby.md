## [etc] Gatsby

[Gatsby](<https://www.gatsbyjs.org/>)는 React 기반 정적 사이트 생성기이다. 



#### Gatsby CLI 설치 및 실행

Gatsby CLI는 Gatsby 프로젝트 개발 환경을 설정해주는 툴이다.

```shell
$ npm install -g gatsby-cli
// gatsby-cli npm을 전역으로 설치

$ gatsby new [프로젝트 폴더명]
// 새 프로젝트 생성

$ cd [프로젝트 폴더명]
// 생성한 프로젝트로 이동

$ gatsby develop 
// 개발 모드로 서버 실행
```



#### starter

starter는 gateby의 템플릿으로, 원하는 목적에 맞게끔 샘플 페이지를 생성한다. 기본 명령어인 `gatsby new [프로젝트 폴더명]` 으로 프로젝트를 생성한다면 자동으로`https://github.com/gatsbyjs/gatsby-starter-default` 의 템플릿을 가져온다.

```shell
$ gatsby new [프로젝트 폴더명] https://github.com/gatsbyjs/gatsby-starter-default
// 기본 템플릿으로 프로젝트 생성

$ gatsby new [프로젝트 폴더명] https://github.com/gatsbyjs/gatsby-starter-blog
// 블로그 템플릿으로 프로젝트 생성
```



#### gatsby-starter-blog 폴더 구조

```
.
├── /.cache					내부 캐시
├── /content				포스트 데이터 보관 파일
├── /node_modules			npm 패키지 보관
├── /public					build 결과 폴더
├── /src					components, pages 등 작업 파일 관리 폴더
│	├── components				컴포넌트
│	├── pages					페이지
│	├── templates				템플릿
│	└── utils					유틸리티
├── /static					build하지 않는 파일 보관 폴더
├── .gitignore				git에 추적 방지 파일
├── .prettierrc				Prettier 관련 파일 
├── gatsby-browser.js		Gatsby 브라우저 API 사용 설정 파일
├── gatsby-config.js		Gatsby 기본 설정 파일
├── gatsby-node.js			Gatsby 노드 API 사용 설정 파일
├── gatsby-ssr.js			Gatsby 서버 사이드 렌더링 API 사용 설정 파일
├── LICENSE					라이센스
├── package-lock.json		package.json 잠금
├── package.json			Node.js 관리 파일
└── README.md				프로젝트 정보
```





#### 빌드하기 (정적 사이트 파일 생성)

```shell
gatsby build
```

`public/` 폴더에서 빌드 결과를 확인할 수 있다.