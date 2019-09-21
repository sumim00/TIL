## split(), splice(), slice() 정리

공통점 : JavaScript Array에서 문자열을 분할하는 메서드



#### split(기준 문자열)

문자열을 인자로 주어진 파라미터를 기준으로 쪼개서 배열에 담는다.

```javascript
var str = 'html,css,javascript,jquery,apache,php';
str.split(',') // [html,css,javascript,jquery,apache,php]

var str = 'javascript';
var newStr = str.split('') //	[ 'j', 'a', 'v', 'a', 's', 'c', 'r', 'i', 'p', 't' ]
```



#### splice(시작점, 제거할 요소 수, 추가할 요소)

배열의 기존 요소를 삭제 또는 교체하거나, 새 요소를 추가하여 배열의 내용을 변경한다.

```javascript
var months = ['Jan', 'March', 'April', 'June'];

months.splice(1, 0, 'Feb');
// ['Jan', 'Feb', 'March', 'April', 'June']

months.splice(4, 1, 'May');
// ['Jan', 'Feb', 'March', 'April', 'May']

months.splice(2, 2);
// ['Jan', 'Feb', 'May']
```



#### slice(시작점, 마지막점)

어떤 배열의 시작점부터 마지막 바로 전까지에 대한 복사본을 만들어 새로운 배열로 반환한다.

원본 배열은 수정되지 않는다.

```javascript
var animals = ['ant', 'bison', 'camel', 'duck', 'elephant'];

animals.slice(2) // ["camel", "duck", "elephant"]

animals.slice(2, 4) // ["camel", "duck"]
```





### Refer

[Array.prototype.splice() - JavaScript | MDN - Mozilla](<https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/splice>)

[split - 생활코딩](<https://opentutorials.org/course/50/96>)