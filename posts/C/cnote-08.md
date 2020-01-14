# 씹어먹는 C언어 필기 (17~18강)

> Psi님의 [씹어먹는 C언어](<https://modoocode.com/231>) 강좌를 수강하며 기록한 노트입니다.



### 17. 변수의 생존 조건 및 데이터 세그먼트의 구조

##### 지역 변수, 전역 변수, 정적 변수

- 지역 변수 (local variable) : `{}` 내 해당 지역에서만 접근할 수 있는 변수. 지역에 해당하는 함수가 종료될 때 파괴
- 전역 변수 (global variable) : 어떠한 지역에도 속해 있지 않은 변수. 프로그램이 종료될 때 파괴.
- 정적 변수 (static variable) : `staic int a = 2` 의 형태로, 자신이 선언된 범위를 벗어나더라도 파괴되지 않는다.



```c
/* 정적 변수의 활용 */
#include <stdio.h>
int function() {
	static int how_many_called = 0;

	how_many_called++;

	printf("function called : %d \n", how_many_called);

	return 0;
}
int function2() {
	static int how_many_called = 0;

	how_many_called++;

	printf("function2 called : %d \n", how_many_called);

	return 0;
}
int main() {
	function();
	function2();
	function();
	function2();
	function2();
	function2();
	function();
	function2();
	return 0;
}

// answer
function called : 1
function2 called : 1
function called : 2
function2 called : 2
function2 called : 3
function2 called : 4
function called : 3
function2 called : 5
```



##### 데이터 세그먼트의 구조

- RAM에 프로그램의 모든 내용이 적재되는데, 이 때 RAM에 올라오는 프로그램의 코드를 코드 세그먼트, 프로그램의 데이터를 데이터 세그먼트로 분류한다.
- 스택은 메모리 주소가 낮아지는 방향으로 늘어난다.

```c
/* 메모리의 배치 모습 */
#include <stdio.h>
int global = 3;
int main() {
	int i;
	char* str = "Hello, Baby";
	char arr[20] = "WHATTHEHECK";

	printf("global : %p \n", &global);
	printf("i : %p \n", &i);
	printf("str : %p \n", str);
	printf("arr : %p \n", arr);
	return 0;
}

// answer
global: 0035A014
i : 0030FBBC
str : 00357D24
arr : 0030FB94
```

![](https://modoocode.com/img/114F551E4C1E3404A1F0AD.webp)



### 18-1. 파일 뽀개기 (헤더 파일과 #include)

##### 모듈화 프로그래밍 (파일 나누기)

- 모듈화를 통해 장문의 코드를 용도에 맞게 분리할 수 있다.
- 헤더 파일을 이용하여 함수의 원형을 정리한다.

##### `#include` 전처리기에 대한 이해

- `#include` 와 같은 명령들은 전처리기 명령이라고 부른다.
- 컴파일 이전에 실행되며 지칭하는 파일의 내용을 가져온다.
- `<>` 는 컴파일러에서 기본으로 제공하는 헤더 파일, `" "`는 사용자가 제작한 헤더 파일에 감싼다.

```c
// main.c
#include <stdio.h>
#include "str.h" 

int main() {
	char str1[20];
	char str2[20];

	scanf("%s", str1);
	scanf("%s", str2);

	if (compare(str1, str2)) {
		printf("%s 와 %s는 같은 문장입니다. \n", str1, str2);
	}
	else {
		printf("%s 와 %s는 다른 문장입니다. \n", str1, str2);
	}

	return 0;
}


// str.h
int compare(char* str1, char* str2);


// str.c
#include "str.h"

int compare(char* str1, char* str2) {
	while (*str1) {
		if (*str1 != *str2) {
			return 0;
		}
		str1++;
		str2++;
	}
	if (*str2 == '\0') return 1;

	return 0;
}
```





### 18-2. 파일 뽀개기 (#친구들, 라이브러리)

##### 헤더파일에 대한 설명

```c
//////////////////////// human.h
enum { FEMALE, MALE };

struct Human {
	char name[20];
	int age;
	int gender;
};

struct Human Create_Human(char* name, int age, int gender);
int Print_Human(struct  Human* human);


//////////////////////// str.h
int copy_str(char* dest, char* src);


//////////////////////// human.c
#include <stdio.h>
#include "human.h"
#include "str.h"

struct Human Create_Human(char* name, int age, int gender) {
	struct Human human;
	
	human.age = age;
	human.gender = gender;
	copy_str(human.name, name);

	return human;
}
int Print_Human(struct Human* human) {
	printf("Name: %s \n", human->name);
	printf("Age: %d \n", human->age);
	if (human->gender == FEMALE) {
		printf("Gender: Female \n");
	}
	else if (human->gender == MALE) {
		printf("Gender: Male \n");
	}

	return 0;
}

//////////////////////// str.c
#include "str.h"

int copy_str(char* dest, char* src) {
    while (*src) {
        *dest = *src;
        src++;
        dest++;
    }

    *dest = '\0';

    return 1;
}


//////////////////////// main.c
#include <stdio.h>
#include "human.h" 

int main() {
	struct Human Lim = Create_Human("Lim", 27, FEMALE);

	Print_Human(&Lim);

	return 0;
}
```



##### 라이브러리(string.h) 사용하기

- `string.h ` : 문자열 라이브러리
- `stdio.h` : 입출력 라이브러리
- `strcmp` : 두 문자열이 같다면 0 다르면 0이 아닌 값 리턴

```c
/* 라이브러리의 사용 */
/* strcpy 함수 */
#include <stdio.h>
#include <string.h>

int main() {
	char str1[20] = { "hi" };
	char str2[20] = { "hello every1" };

	strcpy(str1, str2);

	printf("str1 : %s \n", str1);

	return 0;
}

```

```c
/* strcmp */
#include <stdio.h>
#include <string.h>

int main() {
	char str1[20] = { "hi" };
	char str2[20] = { "hello every1" };
	char str3[20] = { "hi" };

    if (!strcmp(str1, str2)) {
        printf("%s and %s is equal \n", str1, str2);
    }
    else {
        printf("%s and %s is NOT equal \n", str1, str2);
    }

    if (!strcmp(str1, str3)) {
        printf("%s and %s is equal \n", str1, str3);
    }
    else {
        printf("%s and %s is NOTequal \n", str1, str3);
    }

    return 0;
}
```



##### 전처리기 명령

- `#define` : 매크로이름에 해당하는 부분을 값으로 대체한다.
- `#ifdef, endif` : `ifdef`에서 지정한 매크로가 정의되어 있으면 속에 있는 코드가 포함된다.

```c
/* #define */
#include <stdio.h>
#define VAR 10

int main() {
    char arr[VAR] = { "hi" };
    printf("%s", arr);
    return 0;
}
```

```c
/* #ifdef, endif */
#include <stdio.h>
#define A

int main() {
#ifdef A
printf("AAA \n");
#endif

#ifdef B
printf("BBB \n");
#endif

    return 0;
}

// answer
AAA
```

