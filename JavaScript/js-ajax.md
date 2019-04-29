# Ajax

정의 : 비동기적으로 페이지의 일부만 리로드하는 기술. 기존에 페이지 전체를 서버에서 재응답하는 것과는 달리 서버의 과부하를 막고 응답시간을 줄일 수 있다.



#### 코드

```
<body>
    <article></article>
    <input type="button" value="fetch" onclick="
        fetch('css.html').then(function(response){
            response.text().then(function(text){
                // alert(text);
                document.querySelector('article').innerHTML = text;
            })
        })
    ">
</body>
```



fetch('css.html') : 인자로 받은 값을 서버에 요청하는 역할 (css.html 파일을 불러오도록 서버에 요청)

.then() : 서버가 응답이 끝나면 뒤에 나오는 함수를 실행

.then(function(response){} : response는 서버가 응답이 끝난 뒤 가져오는 정보를 담고 있는 객체. 



```
<ol id="nav">
    <li><a href="#!html" onclick="fetchPage('html')">html</a></li>
    <li><a href="#!css" onclick="fetchPage('css')">css</a></li>
    <li><a href="#!javascript" onclick="fetchPage('javascript')">javascript</a></li>
</ol>
<script>
  if(location.hash){
    fetchPage(location.hash.substr(2));
  } else {
    fetchPage('welcome');
  }
</script>
```



window.location.hash : window는 생략 가능, url에서 해시에 해당하는 부분을 불러온다.

location.hash.substr(1) : substr는 string 중 일부만 가져오는 함수, 예시의 경우 1부터 끝까지 가져온다.

#! : 해시뱅, 해시뱅을 이용한 방식은 검색엔진 최적화가 안되기 때문에, 최근에는 pjax 를 이용하고 있음.


```
function fetchPage(name){
    fetch(name).then(function(response){
      response.text().then(function(text){
        document.querySelector('article').innerHTML = text;
      })
    });
  }
  if(location.hash){
    fetchPage(location.hash.substr(2));
  } else {
    fetchPage('welcome');
  }
  fetch('list').then(function(response){
    response.text().then(function(text){
      var items = text.split(',');
      var i = 0;
      var tags = '';
      while(i<items.length){
        var item = items[i];
        item = item.trim();
        var tag = '<li><a href="#!'+item+'" onclick="fetchPage(\''+item+'\')">'+item+'</a></li>';
        tags = tags + tag;
        i = i + 1;
      }
      document.querySelector('#nav').innerHTML = tags;
    })
  });
```


split(',') : 괄호 내 요소, 여기서는 따옴표를 기준으로 문장을 나눠서 배열에 저장한다. 

trim() : 요소의 공백을 제거한다.


#### Polyfill

정의 : 웹 개발에서 기능을 지원하지 않는 웹 브라우저 상의 기능을 구현하는 코드

##### fetch API polyfill cdn 주소

<script src="https://cdn.jsdelivr.net/npm/promise-polyfill@8.1/dist/polyfill.min.js"></script>

<script src="https://cdn.jsdelivr.net/npm/whatwg-fetch@3.0/dist/fetch.umd.min.js"></script>
