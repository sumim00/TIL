# 02 타입 정의하기

#### 기본 타입

1. Number - 숫자 타입
2. String - 텍스트 타입
3. Boolean - `true` 혹은 `false` 값을 반환한다.
4. Any - 모든 타입을 허용한다.
5. Array - 2가지 구문으로 사용 가능하다. `my_arr: number[]` or `my_arr:Array<number>`
6. Void - 어떤 것도 리턴하지 않는 함수의 반환 타입이다.



#### 타입별 정의

```typescript
// Number
let decimal: number = 6;

// String
let color: string = "blue";

// Boolean
let isDone: boolean = false;

// Array
let list: number[] = [1,2,3];
let list: Array<number> = [1,2,3];

// Any
let noSure: any = 4;

// Void
function warnUser(): void {
    alert("This is my warning message")
}
```



[기본 타입 - GitBook]([https://typescript-kr.github.io/pages/Basic%20Types.html](https://typescript-kr.github.io/pages/Basic Types.html))