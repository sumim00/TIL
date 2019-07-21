## 리액트 네이티브 2. 컴포넌트



#### 사용 방법

```javascript
import { 컴포넌트1, 컴포넌트2... } from "react-native"
```



#### 기본 컴포넌트

| 컴포넌트명 | 설명                                                  |
| ---------- | ----------------------------------------------------- |
| View       | UI 생성에서 가장 기본적인 컴포넌트                    |
| Text       | 텍스트 컴포넌트                                       |
| Image      | 이미지 컴포넌트                                       |
| TextInput  | input 타입을 위한 컴포넌트                            |
| ScrollView | 여러 컴포넌트와 뷰를 호스팅할 수 있는 스크롤 컨테이너 |
| StyleSheet | CSS 스타일 설정을 위한 컴포넌트                       |



#### UI 컨트롤러

| 컴포넌트명 | 설명                                 |
| ---------- | ------------------------------------ |
| Button     | 기본 버튼 컴포넌트                   |
| Picker     | iOS와 Android 네이티브 피커 컴포넌트 |
| Slider     | 범위를 선택할 때 사용한다.           |
| Switch     | boolean속성 input을 사용할 수 있다.  |



#### 리스트 뷰

`ScrollView`와 달리 스크린에서만 보여지는 요소들만 렌더링한다. 

| 컴포넌트명  | 설명                                                |
| ----------- | --------------------------------------------------- |
| FlatList    | 스크롤이 가능한 리스트들을 렌더링하기 위한 컴포넌트 |
| SectionList | `FlatList`와 비슷하나, 분리된 리스트들에 사용한다.  |



#### iOS 컴포넌트 및 API

| 컴포넌트명          | 설명                                                         |
| ------------------- | ------------------------------------------------------------ |
| ActionSheetIOS      | 공유 시트 및 iOS 액션 시트를 표시하는 API                    |
| AlertIOS            | iOS 대화 상자를 만들거나 사용자 입력을 위한 prompt를 생성한다. |
| DatePickerIOS       | 날짜 선택창을 렌더링한다.                                    |
| ImagePickerIOS      | iOS에서 이미지 선택창을 렌더링한다.                          |
| NavigatorIOS        | 네비게이션 기능을 구현할 수 있다.                            |
| ProgressViewIOS     | iOS에서 `UIProgressView`를 구현할 수 있다.                   |
| PushNotificationIOS | 앱에 푸시기능을 사용할 수 있다.                              |
| SegmentedControlIOS | iOS에서`UISegmentedControl`를 구현할 수 있다.                |
| TabBarIOS           | iOS에서`UITabViewController`를 구현할 수 있다.               |



#### 안드로이드 컴포넌트 및 API

| 컴포넌트명          | 설명                                                    |
| ------------------- | ------------------------------------------------------- |
| BackHandler         | 뒤로가기 버튼이 눌려지는 것을 감지한다.                 |
| DatePickerAndroid   | 안드로이드 날짜선택창을 구현한다.                       |
| DrawerLayoutAndroid | 안드로이드에서 `DrawerLayout`를 렌더링한다.             |
| PermissionsAndroid  | 안드로이드 M에 도입된 권한 모델에 대한 접근을 제공한다. |
| ProgressBarAndroid  | 안드로이드에서 `ProgressBar`를 렌더링한다.              |
| TimePickerAndroid   | 안드로이드 시간선택창을 구현한다.                       |
| ToastAndroid        | 안드로이드 Toast 알림을 생성한다.                       |
| ToolbarAndroid      | 안드로이드에서 `Toolbar`를 렌더링한다.                  |
| ViewPagerAndroid    | 뷰의 좌우를 바꿀 수 있다.                               |



#### 기타

| 컴포넌트명           | 설명                                                         |
| -------------------- | ------------------------------------------------------------ |
| ActivityIndicator    | 로딩 서큘레이터를 표시한다.                                  |
| Alert                | 알림 기능을 사용할 수 있다.                                  |
| Animated             | 보다 편리한 애니메이션 기능 사용을 위한 라이브러리다.        |
| Clipboard            | iOS와 안드로이드에서 클립보드의 콘텐츠를 설정하고 가져올 수 있다. |
| Dimensions           | 디바이스의 크기 정보를 제공한다.                             |
| KeyboardAvoidingView | 키보드의 위치에 따라 바닥 패딩을 자동으로 조절할 수 있다.    |
| Linking              | 앱 링크와 관련된 UI를 제공한다.                              |
| Modal                | 모달창을 렌더링한다.                                         |
| PixelRatio           | 픽셀 밀도에 대한 접근을 제공한다.                            |
| RefreshControl       | `ScrollView` 내부에서 사용되며 끌어서 새로 고침 기능을 추가한다. |
| StatusBar            | 앱 상태표시줄을 컨트롤할 수 있다.                            |
| WebView              | 네이티브 뷰에서 웹 컨텐츠를 렌더링한다.                      |





### Refer

[React Native 공식 홈페이지 - Components and APIs](<https://facebook.github.io/react-native/docs/components-and-apis>)