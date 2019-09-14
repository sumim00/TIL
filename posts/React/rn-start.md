## 리액트 네이티브

### 1. 개발 환경 세팅

네이티브 개발 환경에 익숙한 경우, 기존에 사용하던 Xcode나 Android Studio를 이용하면 된다. 

리액트 네이티브를 통해 처음 앱 제작을 시작하는 경우 공식 홈페이지에서는  [Expo](<https://expo.io/>)를 이용하여 개발환경을 만드는 것을 추천한다. 



### Expo란?

- 리액트 네이티브를 이용한 프로젝트의 진행을 돕는 서드파티 툴.
- 처음 패키지 세팅부터 디바이스에서의 확인, 배포를 위한 빌드까지 개발에 필요한 다양한 기능을 지원한다.
- 네이티브에 비해 간단하고 빠르게 앱을 제작할 수 있다.

##### 단점

- 앱의 용량이 커진다.
- java, swift, cotlin과 같은 다른 라이브러리를 조합하여 사용하기 힘들다.



### Expo 설치 CLI

```powershell
npm install -g expo-cli

expo init 프로젝트명

cd 프로젝트명
npm start or expo start
```





##### Choose a template

1. blank : 별도의 루트 컴포넌트가 없으며 단일페이지를 생성할 때.
2. tabs : react-navigation 을 이용하여 여러 개의 탭과 화면을 생성할 때.



### 시뮬레이션 방법

1. Xcode, Android Studio가 설치되어 있다면 해당 시뮬레이터로 확인.
2. 없다면 가지고 있는 디바이스에 expo앱을 설치하고 QR코드를 스캔하여 확인.



### Refer

[React Native 공식 홈페이지 - Getting Started](<https://facebook.github.io/react-native/docs/getting-started>)