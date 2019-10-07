# [TypeScript] 04.인터페이스

#### 인터페이스란?

타입 체크를 위해 사용되며 변수, 함수, 클래스에 사용할 수 있다. 



#### 변수 타입 인터페이스

```typescript
// 인터페이스 정의
interface Todo {
    id: number;
    content: string;
    completed: boolean;
}

// 변수 todo의 타입으로 Todo 인터페이스를 선언한다.
let todo: Todo;

// Todo 인터페이스를 준수하는 todo 변수의 인수를 입력한다.
todo = { id: 1, content: 'typescript'; completed: false };
```



#### 함수 타입 인터페이스

```typescript
// 함수 타입 입터페이스 정의
interface SquareFunc {
    (num: number): number;
}

// SquareFunc 인터페이스를 준수하는 squareFunc 함수를 선언한다.
const squareFunc: SquareFunc = function (num: number) {
    return num * num;
}

console.log(squareFunc(10)); // 100
```



#### 클래스 타입 인터페이스

```typescript
// 클래스 타입 입터페이스 정의
interface ITodo {
    id: number;
    content: string;
    completed: boolean;
}

// ITodo 인터페이스를 준수하는 Todo 클래스를 선언한다.
class Todo implements ITodo {
  constructor (
    public id: number,
    public content: string,
    public completed: boolean
  ) { }
}

const todo = new Todo(1, 'Typescript', false);

console.log(todo);
```



#### interface optional

```typescript
interface Todo {
    id: number;
    content?: string; // content의 타입 정의를 강제하지 않는다.
    completed: boolean;
}
```





[](<https://typescript-kr.github.io/pages/Interfaces.html>)

[](<https://poiemaweb.com/typescript-interface>)