# 씹어먹는 C언어 필기 (5~7강)

>  Psi님의 [씹어먹는 C언어](<https://modoocode.com/231>) 강좌를 수강하며 기록한 노트입니다.



### 5. 문자 입력 받기



##### 문자를 저장하는 변수 : `char`

- 1바이트 정수를 저장하는 문자 타입

```c
/* 문자를 저장하는 변수 */
#include <stdio.h>
int main() {
	char a;
	a = 'a';
	printf("a 의 값과 들어있는 문자는? 값: %d , 문자: %c \n", a, a);

	return 0;
}

// answer
a 의 값과 들어있는 문자는 ? 값 : 97, 문자 : a
```



##### `scanf`의 사용

- `scanf` : 화면(키보드)로부터 결과를 받아들이는 입력 함수
- 엔터를 눌러야만 입력으로 처리

```c
/* scanf 총정리 */
#include <stdio.h>
int main() {
	char ch;	// 문자

	short sh;	// 정수
	int i;
	long lo;

	float fl;	// 실수
	double du;

	printf("char 형 변수 입력 : ");
	scanf("%c", &ch);

	printf("short 형 변수 입력 : ");
	scanf("%hd", &sh);
	printf("int 형 변수 입력 : ");
	scanf("%d", &i);
	printf("long 형 변수 입력 : ");
	scanf("%ld", &lo);

	printf("float 형 변수 입력 : ");
	scanf("%f", &fl);
	printf("double 형 변수 입력 : ");
	scanf("%lf", &du);

	printf("char : %c , short : %d , int : %d ", ch, sh, i);
	printf("long : %d , float : %f , double : %f \n", lo, fl, du);

	return 0;
}
```





##### 섭씨 -> 화씨 환산 프로그램

```c
/* 섭씨 온도를 화씨로 바꾸기 */
#include <stdio.h>
int main() {
	double celsius;

	printf("섭씨 온도를 화씨 온도로 바꿔주는 프로그램입니다. \n");
	printf("섭씨 온도를 입력해주세요. : ");
	scanf("%lf", &celsius);

	printf("섭씨 %f 도는 화씨 %f 도 입니다. \n", celsius, 9 * celsius / 5 + 32);

	return 0;
}
```



### 6. 만약에...if문

`if`문에 대한 이해

```c
/* if문이란? */
#include <stdio.h>
int main() {
	int i;
	printf("입력하고 싶은 숫자를 입력하세요. : ");
	scanf("%d", &i);

	if (i == 7) {
		printf("당신은 행운의 숫자 7을 입력했습니다.");
	}
	return 0;
}
```

- `==` : 두 값 사이의 관계를 나타내는 관계 연산자
- `if`문 속의 조건이 0인가 (거짓) 0이 아닌가 (참)에 따라 실행의 유무를 판별 
- `if(1)`이면 괄호 속 내용이 실행된다.



```c
/* 나눗셈 예제 */
#include <stdio.h>
int main() {
	double i, j;
	printf("나누고 싶은 두 정수를 입력하세요. : ");
	scanf("%lf %lf", &i, &j);

	if (j == 0) {
		printf("0으로 나눌 수 없습니다. \n");
		return 0;
	}

	printf("%f 를 %f 로 나눈 결과는 : %f \n", i, j, i / j);

	return 0;
}
```

- `j`가 0일 경우 `if`문 속 메시지가 출력되고 프로그램이 종료(`return 0`) 된다.



`if- else`문

```c
/* if else문 */
#include <stdio.h>
int main() {
	int num;

	printf("아무 숫자나 입력하세요. : ");
	scanf("%d", &num);

	if (num == 7) {
		printf("행운의 숫자 7이군요! \n");
	}
	else {
		printf("그냥 보통 숫자인 %d 를 입력했군요! \n", num);
	}

	return 0;
}
```



##### 논리 연산자

```c
/* 논리 연산자 */
#include <stdio.h>
int main() {
	int height, weight;

	printf("당신의 키와 몸무게를 각각 입력해주세요. : ");
	scanf("%d %d", &height, &weight);

	if (height >= 190 || weight >= 100) {
		printf("당신은 '거구' 입니다. \n");
	}
	if (!(height >= 190 || weight >= 100)) {
		printf("당신은 거구가 아닙니다. \n");
	}

	return 0;
}
```

- `&&` : 논리곱. 두 개의 조건식이 모두 참이 되어야 실행.
- `||` : 조건식에서 어느 하나가 참이라면 실행.



### 7. 뱅글 뱅글 for, while

##### `for`문 

- 특정한 연산을 제어변수가 조건에 맞을 때만 반복해주는 문.

```c
for (초기식; 조건식; 증감식) {
    명령1;
    명령2;
    ...
}
```



##### `break`문

- 실행되면 `for`문을 탈출한다.

```c
/* break문 */
#include <stdio.h>
int main() {
	int useranswer;

	printf("컴퓨터가 생각한 숫자를 맞춰보세요! \n");

	for (;;) {
		scanf("%d", &useranswer);
		if (useranswer == 3) {
			printf("맞추셨군요! \n");
			break;
		}
		else {
			printf("틀렸어요! \n");
		}
	}

	return 0;
}
```



##### `continue`문

- `break`와 달리 ` for`문을 빠져나가지 않고 조건 점검부로 점프한다.

```c
/* continue문 */
#include <stdio.h>
int main() {
	int i;

	for (i = 0; i < 100; i++) {
		if (i % 5 == 0) continue;

		printf("%d ", i);
	}

	return 0;
}
```



##### `while`문

- 명령을 실행하기 전에 조건식이 참인지 먼저 검사한다. (최소 0번 명령 실행, for문 또한 동일)

```c
while (조건식) {
    명령1;
    명령2;
    ...
}
```

```c
/* while문 */
#include <stdio.h>
int main() {
	int i = 1, sum = 0;

	while (i <= 100) {
		sum += i;
		i++;
	}

	printf("1부터 100까지의 합 : %d \n", sum);

	return 0;
}
```





##### `do - while`문

- 먼저 명령을 실행한 뒤에 조건식을 검사한다. (최소 1번 명령 실행)

```c
do {
    명령1;
    명령2;
    ...
} while (조건식);
```

```c
/* do-while문 */
#include <stdio.h>
int main() {
	int i = 1, sum = 0;

	do {
		sum += i;

		i++;
	} while (i < 1);

	printf("sum : %d \n", sum);

	return 0;
}

// answer
sum : 1
```

