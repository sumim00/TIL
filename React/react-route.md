<<<<<<< HEAD
# 리액트 라우팅

>  버전 : react-router-dom v4
>
> 프로젝트 : Moon-note
>
> https://reacttraining.com/react-router/



### v3 / v4

기존에 ```react-route``` 만 단독으로 존재했던 v3과는 달리, v4부터는 ```react-router-dom``` 과 ```react-router-native``` 로 각각 분리되었다. 이름에서도 알 수 있듯이 dom은 웹용, native는 앱용으로 내 작업에서는  ```react-router-dom``` 를 설치했다. 

```powershell
npm install --save react-router-dom
```



## 적용방법

### App.js

```react
import { BrowserRouter as Router, Route, Switch } from 'react-router-dom'

...

return (
      <Router>
        <div>
          <Header />
          <div class="container">
            <Switch>
              <Route exact path="/" component={Home}/>
              <Route path="/about" component={About}/>
              <Route path="/posts" component={Posts}/>
              <Route path="/write" component={Write}/>
            </Switch>
          </div>
        </div>
      </Router>
    )
```

import로 ```react-router-dom``` 을 불러오고, ```Router``` 로 라우팅 할 컴포넌트들을 묶어준 뒤 ```Router``` 로 컴포넌트를 연결시켜준다.  ```exact``` 는 /about과 같이 ```/``` 값이 포함된 라우트에 ```/``` 컴포넌트가 함께 불려오지 않도록, 해당 ```path``` 와 정확히 일치하는 경우에만 컴포넌트를 보여주는 역할을 한다.

```switch``` 는 ```Route``` 되는 컴포넌트만 보여줄 수 있도록 하는 역할이다.



### Posts.js

```react
import { Route, Link } from "react-router-dom";

...

<Link to="/posts/react">React</Link>
<Route path="/posts/:title" component={Post}/>
```

Link : 리액트에서는 a태그를 사용할 경우 새로고침이 발생하기 때문에, ```Link``` 를 사용함으로써 새로고침 없이 뷰를 렌더할 수 있다.

Params:  ```:name``` 형식으로 추가한다.



### Home.js

```react
<button onClick={() => {history.push('/posts')}}>
    버튼
</button>
```

history : push, replace를 함께 사용함으로써 다른 경로로 이동하거나 앞뒤 페이지로 전환할 수 있다.



### 

## Reference

https://medium.com/@han7096/react-router-v4-%EC%A0%95%EB%A6%AC-e9931b63dcae

https://velopert.com/3417

https://blueshw.github.io/2017/06/22/static-routing-vs-dynamic-routing/?no-cache=1

=======
# 리액트 라우팅

>  버전 : react-router-dom v4
>
> 프로젝트 : Moon-note
>
> https://reacttraining.com/react-router/



### v3 / v4

기존에 ```react-route``` 만 단독으로 존재했던 v3과는 달리, v4부터는 ```react-router-dom``` 과 ```react-router-native``` 로 각각 분리되었다. 이름에서도 알 수 있듯이 dom은 웹용, native는 앱용으로 내 작업에서는  ```react-router-dom``` 를 설치했다. 

```powershell
npm install --save react-router-dom
```



## 적용방법

### App.js

```react
import { BrowserRouter as Router, Route, Switch } from 'react-router-dom'

...

return (
      <Router>
        <div>
          <Header />
          <div class="container">
            <Switch>
              <Route exact path="/" component={Home}/>
              <Route path="/about" component={About}/>
              <Route path="/posts" component={Posts}/>
              <Route path="/write" component={Write}/>
            </Switch>
          </div>
        </div>
      </Router>
    )
```

import로 ```react-router-dom``` 을 불러오고, ```Router``` 로 라우팅 할 컴포넌트들을 묶어준 뒤 ```Router``` 로 컴포넌트를 연결시켜준다.  ```exact``` 는 /about과 같이 ```/``` 값이 포함된 라우트에 ```/``` 컴포넌트가 함께 불려오지 않도록, 해당 ```path``` 와 정확히 일치하는 경우에만 컴포넌트를 보여주는 역할을 한다.

```switch``` 는 ```Route``` 되는 컴포넌트만 보여줄 수 있도록 하는 역할이다.



### Posts.js

```react
import { Route, Link } from "react-router-dom";

...

<Link to="/posts/react">React</Link>
<Route path="/posts/:title" component={Post}/>
```

Link : 리액트에서는 a태그를 사용할 경우 새로고침이 발생하기 때문에, ```Link``` 를 사용함으로써 새로고침 없이 뷰를 렌더할 수 있다.

Params:  ```:name``` 형식으로 추가한다.



### Home.js

```react
<button onClick={() => {history.push('/posts')}}>
    버튼
</button>
```

history : push, replace를 함께 사용함으로써 다른 경로로 이동하거나 앞뒤 페이지로 전환할 수 있다.



### 

## Reference

https://medium.com/@han7096/react-router-v4-%EC%A0%95%EB%A6%AC-e9931b63dcae

https://velopert.com/3417

https://blueshw.github.io/2017/06/22/static-routing-vs-dynamic-routing/?no-cache=1

>>>>>>> 21e0b58a136e62bcc7940176e74c474fbf3cc239
https://reacttraining.com/react-router/