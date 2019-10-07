# [TypeScript] 05.클래스

#### 클래스와 프로퍼티의 접근 제어자

```typescript
class Parent {
    publicProp: string;
    private privateProp: string;
    protected protectedProp: string;

    constructor() {
        this.privateProp = '';
        this.protectedProp = '';
        this.publicProp = '';
    }
}

class Child extends Parent {
    constructor() {
        super();
        this.publicProp = 'public';
        this.protectedProp = 'protected';
    }
}
```

- class 내 프로퍼티의 접근 제어자는 `public`을 기본값으로 갖고 있다.
- `private`로 설정된 프로퍼티는 외부에서 접근할 수 없다.
- `protected`로 설정된 프로퍼티는 외부에서 접근할 수 없으나, 상속받은 자식 클래스에서는 접근할 수 있다.



#### 클래스와 메서드

```typescript
class Person {
    constructor( _name: string, _age: number ) { }

    // 일반 함수 사용
    getName(): void {
        console.log(this._name);
    }
    
    // 화살표 함수 사용
    getAge = ():void => {
        console.log(this._age);
    }
}

const person: Person = new Person('Elsa', 20);
person.getName(); // Elsa
```





[타입스크립트 코리아:  2017.05 기초 세미나]([https://www.inflearn.com/course/%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%BD%94%EB%A6%AC%EC%95%84-1705-%EA%B8%B0%EC%B4%88-%EC%84%B8%EB%AF%B8%EB%82%98/lecture/6809](https://www.inflearn.com/course/타입스크립트-코리아-1705-기초-세미나/lecture/6809))