# [React] Redux란

- 상태관리를 위한 자바스크립트 라이브러리. 
- React를 포함한 Angular와 같은 다른 뷰 라이브러리와도 호환 가능.



## 개념

### 액션 (Action)

앞으로 일어날 상태를 나타내는 객체. `type`속성을 필수로 가진다.

```javascript
{
    type: ADD_TODO,
    text: 'Build my first Redux app'
}
```



### 액션 생성자 (Action Creator)

액션이 단순히 어떤 기능을 할 지를 담은 객체라면, 액션 생성자는 이러한 액션을 만드는 함수이다.

```javascript
function addTodo(text) {
    return {
        type: ADD_TODO,
        text
    }
}
```

실제로 액션을 보내려면 결과값을 `dispatch()`함수에 넘긴다.

```javascript
dispatch(addTodo(text));
```

또한 이 두가지 코드를 하나로 묶어 바인드된 액션 생상자를 만들 수 있다.

```javascript
const boundAddTodo = (text) => dispatch(addTodo(text));
```



### 리듀서 (Reducer)

이전 상태와 액션을 받아서 다음 상태를 반환하는 순수 함수. `state`와 `action`의 두 가지 파라미터를 가지고 있다.

```javascript
function todoApp(state, action) {
    if (typeof state === 'undefined') {
    	return initialState
  	}
    return state
}
```



### 스토어 (Store)

상태를 보관하고 액션을 보낼 때 리듀셔를 호출하는 객체. 하나의 애플리케이션에는 하나의 스토어만 존재한다.

- 애플리케이션의 상태 저장
- `getState()`를 통해 상태에 접근
- `dispatch(action)`를 통해 상태를 수정
- `subscribe(listener)`를 통해 리스너를 등록

```javascript
import { createStore } from 'redux';
import todoApp from './reducers';

let store = createStore(todoApp); // 리듀서 생성

console.log(store.getState()); // 초기 상태 기록

let unsubscribe = store.subscribe(() => 
	console.log(store.getState());
) // 상태가 바뀔 때마다 기록

store.dispatch(addTodo('Learn about store')); // 액션을 보내기

unsubscribe(); // 상태변경을 더 이상 받아보지 않는다.
```









### Refer

[Redux 공식 한글 문서](<https://lunit.gitbook.io/redux-in-korean/>)