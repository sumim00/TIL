# 정규표현식 (RegExp)


## 선언 방법

```javascript
// 리터럴 방식
var option1 = /cat/;
// 정규표현식 생성자 함수 사용
var option2 = new RegExp("cat");
```
차후 정규표현식을 수정하지 않는다면 리터럴 방식을, 수정을 해야 하거나 다른 변수와 함께 사용한다면 생성자 함수를 사용하는 것이 좋다.

## 정규표현식 메서드
``` javascript
console.log(/cat/.test("the cat says meow"));
// true
console.log(/cat/.test("the dog says bark"));
// false
```

## 기본 RegEx


### Symbols

\ 특수문자가 아닌 문자 앞에 올 경우 '해당 문자는 특별하다'는 뜻,

   특수문자 앞에 올 경우 '해당 문자는 특별하지 않다'는 뜻.
   
. 개행문자를 제외한 모든 단일 문자를 의미한다. 

\* 앞의 표현식이 0개 이상이다.

\+ 앞의 표현식이 1개 이상이다.

? 앞의 표현식이 있을 수도 있고, 없을 수도 있다.

^ 입력의 시작 부분과 대응된다.

$ 입력의 끝 부분과 대응된다.


### Charactop groups

\B 문자열의 첫 번째 문자가 단어가 아닌 경우, 해당 문자의 앞부분.

문자열의 마지막 문자가 단어가 아닌 경우, 해당 문자의 뒷부분.

두 단어 사이에 대응.

단어 문자가 아닌 두 문자 사이에 대응.

빈 문자열에 대응.

\d 숫자 문자. [0-9]와 동일

\D 숫자가 아닌 문자. [^0-9]와 동일

\w 영숫자 문자. [A-Za-z0-9_]와 동일

\W 단어 문자가 아닌 문자. [^A-Za-z0-9_]와 동일

[WYZ] 문자셋으로 괄호 안의 어떤 문자와도 대응된다. [A-Z]처럼 범위를 지정해줄 수도 있다.

[WYZ]+ 세트 안에 있는 하나 혹은 그 이상의 어떤 글자와도 대응된다.

[^A-Z] 하나의 문자 세트 안에서 ^의 의미는 부정의 의미이다. 여기서는 어떤 대문자와도 대응되지 않는다.


### Flag

g Global search

i case insensitive search


### Advanced

(x) 포획괄호. x에 대응되고 기억되어 나중에 사용할 수 있다.

(?:x) 비포획 괄호. x에 대응되지만 대응된 것을 기억하지 않는다.

x(?=y) y가 뒤따라오는 x에만 대응한다.



###정규식에서 쓰이는 메서드
exec : 대응되는 문자열을 찾는 메서드. 정보를 갖고 있는 배열을 반환하고 없으면 null을 반환.
text : 대응되는 문자열을 찾는 메서드. true 또는 false를 반환.
match : 대응되는 문자열을 찾는 메서드. exec와 기능 동일.
search : 대응된 일부의 인덱스를 반환. 없으면 -1 반환.
replace : 대응되는 문자열을 찾아 다른 문자열로 치환.
split : 정규식 혹은 문자열로 대상 문자열을 나누어 배열로 반환. 



## Refer

[MDN 정규 표현식](https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/%EC%A0%95%EA%B7%9C%EC%8B%9D)

[3jun - Javascript: 초보자를 위한 정규식(Regular Expressions) 배우기](https://3jun.tistory.com/88)
