# [TypeScript] 03.컴파일러 사용법 및 옵션

#### npm 설치하기

터미널에서 npm을 사용하여 TypeScript를 전역에 설치한다.

```bash
$ npm install -g typescript
```



#### 테스트 코드 작성 및 실행

테스트를 위해 TypeScript파일을 작성한다.

```typescript
// person.ts
class Person {
    private name: string;

    constructor(name: string) {
        this.name = name;
    }
    sayHello() {
        return "Hello, " + this.name;
    }
}

const person = new Person('Lim');

console.log(person.sayHello());
```



터미널에서 트랜스파일링을 실행한다. tsc 명령어 뒤에 트랜스파일링을 진행할 파일명을 입력한다. 이 때 확장자 `.ts` 는 생략할 수 있다.

```bash
$ tsc person
```



실행 결과 같은 디렉토리에 자바스크립트 파일이 생성된다.

```javascript
// person.js
var Person = /** @class */ (function () {
    function Person(name) {
        this.name = name;
    }
    Person.prototype.sayHello = function () {
        return "Hello, " + this.name;
    };
    return Person;
}());
var person = new Person('Lim');
console.log(person.sayHello());

```



트랜스파일링이 완료된 `person.js`파일을 실행하면 다음과 같은 결과를 볼 수 있다.

```bash
$ node person
Hello, Lim
```



#### 컴파일러 옵션 : 1. 자바스크립트 버전 변경 

트랜스파일링된 js 파일의 기본 버전은 ES3이다. 

버전을 변경하기 위해서는 컴파일 옵션에 `--target` 또는 `-t`를 사용한다.

```bash
tsc person -t es6
```

```javascript
// person.js
class Person {
    constructor(name) {
        this.name = name;
    }
    sayHello() {
        return "Hello, " + this.name;
    }
}
const person = new Person('Lim');
console.log(person.sayHello());
```



#### 컴파일러 옵션 : 2. 다수의 파일 트랜스파일링 

아래와 같은 명령으로 `person.ts`와 `student.ts` 파일을 동시에 트랜스파일링할 수 있다.

```bash
$ tsc person student
```

또는 와일드카드를 사용하여 모든 TypeScript 파일을 한꺼번에 트랜스파일링할 수도 있다.

```bash
$ tsc *.ts
```





### Refer

[5분 안에 보는 TypeScript · GitBook]([https://typescript-kr.github.io/pages/tutorials/TypeScript%20in%205%20minutes.html](https://typescript-kr.github.io/pages/tutorials/TypeScript in 5 minutes.html))

[TypeScript - Intro &amp; Install | PoiemaWeb](<https://poiemaweb.com/typescript-introduction>)