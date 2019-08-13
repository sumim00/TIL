## Redux-Saga

data를 fetching하는 비동기 액션과 같이 단순하지 않은 작업들은 saga에서 작업하고, 액션에는 순수한 객체만 반환하게끔  돕는 리덕스 미들웨어.

Generators라는 ES6 기능을 활용.



#### 설치

```pow
$ npm install --save redux-saga

#or

$ yarn add redux-saga
```





### actions/index.js

```js
export const FETCH_GUEST_REQUESTED = 'FETCH_GUEST_REQUESTED'

export const fetchGuest = () => ({
    type: FETCH_GUEST_REQUESTED
})
```



### reducers/index.js

```js
const INITIAL_STATE = {
    guests: []
}

const reducer = (state = {}, action) => { 
  switch (action.type) { 
     case 'GET_NEWS': 
        return {... state, loading : true}; 
     기본값 : 
        반환 상태; 
   } 
}; 
```



### sagas/index.js

```js
function* fetchGuest() {
    const list = yield call(Api.fetchList, action.payload.guestList)
    try {
        yield put({type: "FETCH_GUEST_SUCCEEDED", guest: guest})
    } catch (error) {
        yield put({type: "FETCH_GUEST_FAILED", message: error.message});
    }
}

function* watchGuestSaga() {
    yield takeEvery("FETCH_GUEST_REQUESTED", fetchGuest)
}
/* takeLatest를 사용하면 가장 마지막 호출만 실행된다. */
function* watchGuestSaga() {
    yield takeLatest("FETCH_GUEST_REQUESTED", fetchGuest)
}
```

