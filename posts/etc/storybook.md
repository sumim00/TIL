# [etc] Storybook

[Storybook](<https://storybook.js.org/>)은 개발자가 독립적인 컴포넌트를 만들 수 있도록 지원하는 UI 개발 환경이다. 



#### 특징

- 컴포넌트를 스토리에 올려 고립된 환경에서 테스트가 가능하기 때문에,

  개발자는 페이지 단위의 의존성에서 벗어나 독립된 컴포넌트를 만드는 데 집중할 수 있다.

- React, React Native, Vue, Angular, HTML 환경에서 사용 가능

- Airbnb, Slack, Coursear와 같은 많은 오픈소스 프로젝트에서 사용하고 있다.



#### 장점

- 컴포넌트를 독립된 환경에서 개발
- UI를 직접 확인하면서 개발할 수 있다.
- 더욱 유연하고 재사용 가능한 컴포넌트를 만들 수 있다.
- UI 개발에 있어 생기는 디자인, 기획 오류를 빠르게 수정할 수 있다.



#### Setup

```powershell
# 프로젝트 폴더로 경로 이동
cd my-project
```

```powershell
# npm으로 cli설치
npm install -g @storybook/cli 
```

```powershell
# 프로젝트 내 storybook 설치
getstorybook
```

```powershell
# storybook 실행 
npm run storybook
```

