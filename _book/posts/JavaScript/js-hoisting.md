# [JavaScript] 호이스팅(Hoisting)

사전적 정의는 '끌어올리다'는 뜻이며, 자바스크립트에서 변수 및 함수의 선언이 스코프 내에서 최상위에 위치하는 것을 의미한다.



```javascript
sayHello("Hello!");

function sayHello(text) {
    console.log(text);
}

//Hello!
```



변수의 경우 또한 어느 위치에 선언을 하더라도 자바스크립트 의 스코프 내에서는 최상위로 끌어올려지는 것을 확인할 수 있다.

```javascript
num = 6;
num += 7;
var num; 
console.log(num)
// 13
```



그러나 만약 변수가 값이 선언되지 않은, 즉 초기화된 상태라면 스코프는 `undefined ` 값을 반환한다.

```javascript
var x = 1;
console.log(x + " " + y)
var y = 2;
// 1 undefined
```



아직 완전히 이해하지 못한 단계라 조금 더 공부해야겠다.



## Reference

[MDN Hoisting 용어사전](<https://developer.mozilla.org/ko/docs/Glossary/Hoisting>) 
