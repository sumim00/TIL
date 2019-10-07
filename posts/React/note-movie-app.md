# [React] 리액트 강의 정리

> 리액트 기초 강의 들으면서 필요한 내용 기록
>
> 강의 : [인프런 노마드코더 React Js로 웹 서비스 만들기](https://www.inflearn.com/course/reactjs-web/)
>
> 깃허브 : https://github.com/nomadcoders/movie_app



### map


```react
{movies.map((movie, index) => {

	return (
    	<Movie movie={movie} key={index}/>
    )

})

}
```

map을 통해 같은 컴포넌트를 여러 번 불러오지 않아도 자동으로 배열을 로딩할 수 있음. 이 때 key값은 필수

**component의 map key값을 index로 하면 로딩이 느리기 때문에 ajax의 id값이 존재한다면 id값을 입력하는 것이 좋다.



### 컴포넌트 라이프사이클

Render: componentWillMount() -> render() -> componentDidMount() 

Update: componentWillReceiveProps() -> shouldComponentUpdate() -> componentWillUpdate() -> render() -> componentDidUpdate() 



### state

state가 업데이트 되면 render 재실행



### state 추가하기

```react
ComponentDidMount(){

	this.setState({

	movies: [

		...this.state.movies,

		{

			title: '~~',

			poster: '~~~'

		}

	]

})

}

```

기존에 있는 state 배열에 새 항목을 추가할 때는 ```...``` 을 이용해서 이런 식으로 추가할 수 있음.



### Loading states

```react
{this.state.movies ? this._renderMovies() : 'Loading'}

_renderMovies = () => {

	const movies = this.state.movies.map((movie, index) => {

		return <Movie title={movie.title} />

	})

	return movies

}

```

state값을 불러오지 못했으면 loading 메세지를 호출



### dumb component & smart component

dumb component = stateless component

state를 가진 smart comtonent는 class from 을 이용해 생성하고,

state가 없이 props로만 작동하는 dumb component는 stateless functional 하게 변경

더 깔끔한 코드를 만들 수 있음.



```react
function MoviePoster({poster, 여러개 가능}) {

	return(

		<img src={poster} />

	)

}

```



state없이 props값을 사용할 경우 이런 식으로 리턴 기능만 수행 가능

클래스는 this라는 값을 갖고 있지만 function 컴포넌트는 this가 없어서 this.props.~~이런 

식으로 사용할 수 없음. 



### 비동기

AJAX는 비동기로 자바스크립트를 XML, JSON 형식으로 불러오는 역할  ,비동기는  ui상으로 로딩이나 다른 표시가 없이 뒤에서 작업이 가능한 장점이 있다.



### protoTypes

prototype를 통해 입력되는 값이 어떤 종류인지, 필수로 받아와야 하는 항목인지 설정할 수 있다. 

[prop-types](https://www.npmjs.com/package/prop-types) npm 설치를 통해 사용 가능

```react
static propTypes = {

	title: PropTypes.string.inRequired,

}

// or

MoviePoster.propTypes = {

	poster: PropTypes.string.isRequired

}
```



### promise 

fetch, promise가 좋은 이유는 시나리오가 생기고 이를 관리할 수 있기 때문

promise는 내가 성공적으로 수행할 수 있고, 그렇지 않을 경우 결과물을 catch, then으로 확인할 수 있다.

But, .then 은 어플리케이션의 규모가 커질 수록 .then 안에 .then이 끊임없이 들어가고

then이 많아져서 Callback Hell에 빠지게 됨.

```react
componentDidMount(){
    fetch('https://yts.~~~') //url을 AJAX로 불러올 수 있음.
    .then(potato => potato.json())
    .then(json => console.log(json))
    .catch(err => console.log(err))
}
```



### Async Await

promise의 단점을 개선하기 위해 사용

```react
async _getMovies = () => {
    const movies = await this._callApi()
    this.setState({
        movies
    })
    // await의 기능이 끝난 후에 아래 setstate기능 실행
}
_callApi = () => {
    return fetch('~~')
    .then(potato => potato.json())
    .then(json => json.data.movies
    .catch(err => console.log(err))
}
```



### state값 없으면 로딩 이미지 불러오기 (in App.js)

```react
render(){
    const { movies } = this.state;
    return(
    	<div className={movies ? "App" : "App--loading"}>
        	{movies ? this._renderMovies() : 'Loading'}
        </div>
    )
}
```





### 참고

react-line-ellipsis 컴포넌트