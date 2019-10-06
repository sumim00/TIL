## var VS let, const

#### var

- ES5 이하 지원
- 변수의 유효 범위 : 함수 스코프
- 호이스팅 (O)
- 재선언 가능



#### let, const

- ES6 이상 지원
- 변수의 유효 범위 : 블록 스코프
- 호이스팅 (X)
- 재선언 불가능
- let은 재할당 가능, const는 재할당 불가능



#### 호이스팅 (Hoisting)

변수를 코드 아래에서 선언했는데 코드 위에서 사용할 수 있는 상황.

```javascript
console.log(hoisted_var);
var hoisted_var = '변수를 아래에서 선언했는데 위에서 사용 가능';
// 경고 없음

console.log(hoisted_let);
let hoisted_let = '변수를 아래에서 선언했는데 위에서 사용 불가능';
// 경고 메시지 발생
// Block-scoped variable 'hoisted_let' used before its declaration.
```



#### 재선언 (Redeclare)

변수를 위에서 선언하고 아래에서 또 다시 선언하는 상황.

```javascript
var redeclare_var = '한 번 선언했는데';
var redeclare_var = '또 선언이 가능';
// 경고 없음

let redeclare_let = '한 번 선언했기 때문에';
let redeclare_let = '또 선언이 불가능';
// 경고 메시지 발생
// Cannot redeclare block-scoped variable 'redeclare_let'
```



#### 재할당 (Reassign)

변수에 할당된 값이 바뀌는 상황.

```javascript
let reassign_let = '처음 할당된 값을';
reassign_let = '재할당할 수 있다';
// 경고 없음

const reassign_const = '처음 할당된 값을';
reassign_const = '재할당할 수 없다';
// 경고 메시지 발생
// Cannot assign to 'reassign_const' because it is a constant.
```





## Refer

[타입스크립트 코리아 : 2017.05 기초 세미나 (6) - var, let, const]([https://www.inflearn.com/course/%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%BD%94%EB%A6%AC%EC%95%84-1705-%EA%B8%B0%EC%B4%88-%EC%84%B8%EB%AF%B8%EB%82%98/lecture/6805](https://www.inflearn.com/course/타입스크립트-코리아-1705-기초-세미나/lecture/6805))

[const - JavaScript | MDN](<https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/const>)