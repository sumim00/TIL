## GitBook

[GitBook](<https://www.gitbook.com/>)은 API와 같이 공유가 필요한 자료들을 쉽게 문서화할 수 있도록 돕는 최신 문서 플랫폼이다. 

사용방법은  1.GitBook 페이지에서 workspace를 만들어 공유할 수 있고, 2.`gitbook-cli`npm을 이용하여 로컬 혹은 githuub레포지토리에서도 사용할 수 있다.



[gitbook-cli](<https://www.npmjs.com/package/gitbook-cli>) 사용 방법

```powershell
$ npm install -g gitbook-cli
```



cli를 설치한 뒤, 프로젝트 디렉토리를 생성한다.

```powershell
$ mkdir [프로젝트명] && cd [프로젝트명]
```



사용을 원하는 폴더에 다음과 같은 코멘드를 입력한다.

```powershell
$ gitbook init
```



gitbook이 성공적으로 설치되면 `serve`를 통해 localhost에서 실행한다.

```
$ gitbook serve
```

