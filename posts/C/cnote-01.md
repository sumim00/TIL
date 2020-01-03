# 씹어먹는 C언어 필기 (1~4강)

>  Psi님의 [씹어먹는 C언어](<https://modoocode.com/231>) 강좌를 수강하며 기록한 노트입니다.



### 2-1. C언어 본격 맛보기



##### 시작

```c
#include <stdio.h>
int main() { 					// 프로그램이 시작되는 함수 
    printf("Hello, World! \n");	// 화면에 내용을 출력하는 함수
    return 0;
}
```



##### #include <stdio.h>

- `stdio.h`  파일을 포함하라는 뜻.
- `stdio`란 *STandard Input Output header* 의 약자로, 화면에 출력하고 키보드로부터 입력을 받아들일 수 있게 돕는 여러 함수들이 포함되어 있다.



##### return 0

- 0을 반환한다는 의미.
- 컴퓨터에게 프로그램이 무사히 종료되었음을 알린다.



##### 주의점

- 모든 문장이 끝나는 부분에 세미콜론(;)을 찍어준다. 



------



### 2-3. 수를 표현하는 방법(기수법)

워드 (컴퓨터 상에서 연산이 실행되는 최소 단위, 64bit 컴퓨터는 1워드가 8byte)



------



### 3. 변수가 뭐지?



##### 변수

- 바뀔 수 있는 어떤 값을 보관하는 곳 (Variable)



```c
/* 변수 알아보기 */
#include <stdio.h>
int main() {
	int a;
	a = 10;
	printf("a의 값은 : %d \n", a);
	return 0;
}
```



##### int a

- `int`형의 데이터를 보관한다.
- 이 때 `int`는 -2147483648 부터 2147483647 까지의 정수를 보관.



##### %d

- 처음 "" 다음에 오는 변수를 출력



##### 변수 데이터 형식

![](https://modoocode.com/img/1165C91B49EF36C6B66009.webp)

`signed`  : 음수와 양수 모두 표시 가능

`unsigned`  : 양수만 표시



```c
/* 변수 알아보기 2 */
#include <stdio.h>
int main() {
	int a;
	a = 127;
	printf("a 의 값은 %d 진수로 %o 입니다. \n", 8, a);
	printf("a 의 값은 %d 진수로 %d 입니다. \n", 10, a);
	printf("a 의 값은 %d 진수로 %x 입니다. \n", 16, a);
	return 0;
}
```



`%d ` : "" 다음에 오는 변수를 순차적으로 출력

`%o` : `a`의 값을 8진수로 출력

`%x` : `a`의 값을 16진수로 출력



```c
/* 변수 알아보기 3 */
#include <stdio.h>
int main() {
	float a = 3.141592f;
	double b = 3.141592;
	printf("a : %f \n", a);
	printf("b : %f \n", b);
	return 0;
}
```



`%f` : `a`의 값을 실수로 출력

##### 주의할 점

`printf`에서 `%f`를 이용하여 소수를 출력할 때, `printf("%f", 1.0)` 처럼 언제나 소수점을 뒤에 붙여 주어야 한다. 



```c
/* printf 형식 */
#include <stdio.h>
int main() {
	float a = 3.141592f;
	double b = 3.141592;
	int c = 123456;
	printf("a : %.2f \n", a);	// 소수점 2자리까지 출력
	printf("c : %5d \n", c);	// 자리수를 되도록 5로 맞추어 출력
	printf("b : %6.3f \n", b);	// 자리수는 6 소수점은 3자리까지 출력
	return 0;
}

// output
a : 3.14
c : 123456
b :  3.142
```



##### 주의할 점

`%d`는 `%f`와 달리 무조건 자리수를 맞추지 않으므로 123456을 전부 표시한다.



##### 변수 선언 규칙

- 숫자가 앞에 위치할 수 없다.
- 변수명은 오직 영어, 숫자, `_` 로만 구성되어야 한다.
- 변수의 이름에 띄어쓰기가 있으면 안된다.
- 변수의 이름이 C언어 예약어이면 안된다. (Visual Studio의 경우 예약어는 파란색으로 표시된다.)



------



### 4. 계산하리

##### 산술 연산자

- `+, -, *, /, %`
- 사칙연산 등 계산을 위한 연산자.
- `%`는 정수형 데이터만 연산이 가능하며, `printf`로 표시할 때 `%%` 형태로 입력한다.



```c
/* 산술 연산 */
#include <stdio.h>
int main() {
	int a, b;
	a = 10;
	b = 3;
	printf("a + b 는 : %d \n", a + b);
	printf("a - b 는 : %d \n", a - b);
	printf("a * b 는 : %d \n", a * b);
	printf("a / b 는 : %d \n", a / b);
	printf("a %% b 는 : %d \n", a % b);
	return 0;
}
```



##### 대입 연산자

- `=`
- 우측의 값을 좌측에 대입하는 연산자.
- C언어 컴파일러는 `=` 기호를 뒤에서부터 해석한다.



##### 산술 변환

```c
/* 산술 변환 */
#include <stdio.h>
int main() {
	int a;
	double b;
	a = 10;
	b = 3;
	printf("a / b 는 : %f \n", a / b);
	printf("b / a 는 : %f \n", b / a);
	return 0;
}

// answer
a / b 는 : 3.333333
b / a 는 : 0.300000
```

- 어떠한 자료형이 다른 두 변수를 연산할 때, 숫자의 범위가 큰 자료형으로 바뀌는 과정.
- 위의 경우는 `int`보다 `double` 의 수 범위가 넓기 때문에 `double` 형태로 결과가 출력.



```c
/* 더하기 1을 하는 방법 */
#include <stdio.h>
int main() {
	int a = 1, b = 1, c = 1, d = 1;
	a = a + 1;
	printf("a : %d \n", a);
	b += 1;				// 복합 대입연산
	printf("b : %d \n", b);
	++c;				// 전위형 증감 연산자
	printf("c : %d \n", c);
	d++;				// 후위형 증감 연산자
	printf("d : %d \n", d);
	return 0;
}

// answer
a : 2
b : 2
c : 2
d : 2
```



```c
/* prefix, postfix */
#include <stdio.h>
int main() {
	int a = 1;
	printf("++a : %d \n", ++a);

	a = 1;
	printf("a++ : %d \n", a++);
	printf("a : %d \n", a);
	return 0;
}

// answer
++a : 2
a++ : 1
a : 2
```



##### 비트 연산자

- `&, |, ^, ~, <<, >>`
- `&` (AND 연산) : 두 수 모두 1일 경우만 1 반환
- `|` (OR 연산) : 두 수 중 하나 이상 1일 경우 1 반환
- `^` (XOR 연산) : 두 수 가 다를 경우 1 반환
- `~` (반전 연산) : 0을 1로, 1을 0으로 변환
- `<<` (쉬프트 연산) : 비트를 왼쪽으로 이동
- `>>` (쉬프트 연산) : 비트를 오른쪽으로 이동

 

```c
/* 비트 연산 */
#include <stdio.h>
int main() {
	int a = 0xAF;				// 10101111
	int b = 0xB5;				// 10110101
	printf("%x \n", a & b);		// 10100101
	printf("%x \n", a | b);		// 10111111
	printf("%x \n", a ^ b);		// 00011010
	printf("%x \n", ~a);		// 1....1 01010000
	printf("%x \n", a << 2);	// 1010111100
	printf("%x \n", b >> 3);	// 00010110
	return 0;
}

// answer
a5
bf
1a
ffffff50
2bc
16
```



##### 연산자 우선 순위

![](https://modoocode.com/img/205C9C4F501D010E144AA9.webp)

- 괄호가 1순위