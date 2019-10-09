#### 순환 (Recursion)

##### Recursion의 개념

> 자기 자신을 호출하는 함수. 순환 또는 재귀함수

```java
void func(...)
{
    ...
    func(...);
    ...
}
```



##### 예제1 factorial

```java
public static int factorial (int n)
{
    if (n == 0)
        return 1;
    else
        return n*factorial(n-1);
}
```



##### 예제2 fibonacci 

```java
public int fibonacci (int n) {
    if (n < 2)
        return n;
    else
        return fibonacci(n-1) + fibonacci(n-2)
}
```



##### 예제3 euclid method

```java
public static int gcd(int p, int q) {
    if (q==0)
        return p;
   	else
        return gcd(q, p%q);
}
```

##### 특징

- 모든 순환함수는 반복문으로 변경 가능.

- 복잡한 알고리즘을 단순하고 알기 쉽게 표현할 수 있다.

- 반복문과 비교하여 계속되는 함수 호출에 따른 오버헤드가 있다.

##### 설계조건

- 적어도 하나의 base case, 즉 순환되지 않고 종료되는 case가 있어야 함.

- 모든 case는 결국 base case로 수렴해야 함.

