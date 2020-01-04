# 씹어먹는 C언어 필기 (8~10강)

>  Psi님의 [씹어먹는 C언어](<https://modoocode.com/231>) 강좌를 수강하며 기록한 노트입니다.



### 8. 우분투 리눅스에서 C 프로그래밍 하기



우분투에서 `GCC` 설치

기초적인 `VIM` 사용법

`GCC` 로 컴파일한 후 실행하기



### 9. 만약에...2탄 (switch문)

```c
switch(/* 변수 */) {
    case /* 값1 */:
        // 명령들;
        break;
   	case /* 값2 */:
        // 명령들;
        break;
    default :
        // 명령들;
        break;
}
```

- 동일한 변수에 대해 비교문이 반복되는 경우 사용한다. 
- `switch` 문에 사용되는 변수는 반드시 정수 데이터를 보관하는 변수여야 한다. (`char`, `int`, `short`, `long`)
- 값에 위치한 것들은 무조건 상수여야 한다.

```c
/* switch문 */
#include <stdio.h>
int main() {
	int input;

	printf("마이펫 업그레이드! \n");
	printf("무엇을 하실 것인지 입력해주세요. \n");
	printf("1. 밥주기 \n");
	printf("2. 씻기기 \n");
	printf("3. 재우기 \n");

	scanf("%d", &input);

	switch (input) {
		case 1 : 
			printf("아이 맛있어! \n");
			break;
		case 2:
			printf("아이 시원해! \n");
			break;
		case 3:
			printf("zzz \n");
			break;
		default:
			printf("무슨 명령인지 못 알아 듣겠어. 왈왈! \n");
			break;
	}

	return 0;
}
```

```c
/* switch문 문자 */
#include <stdio.h>
int main() {
	char input;

	printf("소문자 알파벳 읽기 \n");
	printf("알파벳 :  \n");

	scanf("%c", &input);

	switch (input) {
		case 'a' : 
			printf("에이 \n");
			break;
		case 'b':
			printf("비 \n");
			break;
		case 'c':
			printf("씨 \n");
			break;
		default:
			printf("죄송해요.. 머리가 나빠서 못 읽어요. \n");
			break;
	}

	return 0;
}
```





### 10. 연예인 캐스팅(?) (C언어에서의 형 반환)

변수의 형을 바꾸는 방법

```c
(바꾸려는 형) 변수 이름 
```

```c
/* 두 수의 비율 */
#include <stdio.h>
int main() {
	int a, b;
	float c, d;

	printf("두 숫자 입력 : ");
	scanf("%d %d", &a, &b);

	c = a / b;
	d = (float)a / b;

	printf("두 수의 비율 : %f %f", c, d);

	return 0;
}
```

```c
/* 생각해보기 문제 */
#include <stdio.h>
int main() {
	float f;
	int i;

	printf("실수를 입력하시오 : ");
	scanf("%f", &f);

	i = (f - (int)f) * 100;

	if (f < 0) {
		i *= -1;
	};
	

	printf("i = %d \n", i);

	return 0;
}
```





