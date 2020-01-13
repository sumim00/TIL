# 씹어먹는 C언어 필기 (16강)

> Psi님의 [씹어먹는 C언어](<https://modoocode.com/231>) 강좌를 수강하며 기록한 노트입니다.



### 16-1. 모아 모아 구조체(struct)

##### 구조체에 대한 소개

- 구조체 : 각 원소의 타입이 제각각인 배열
- 구조체를 정의할 때는 모든 원소의 타입을 명시해 주어야 한다.
- `.`을 이용하여 구조체 멤버에 접근한다.

```c
/* 구조체 예제1 */
#include <stdio.h>
struct Human {
	int age;	// 나이
	int height;	// 키
	int weight;	// 몸무게
};
int main() {
	struct Human Jiy;

	Jiy.age = 26;
	Jiy.height = 168;
	Jiy.weight = 60;

	printf("Jiy에 대한 정보 \n");
	printf("나이 %d \n", Jiy.age);
	printf("키 %d \n", Jiy.height);
	printf("몸무게 %d \n", Jiy.weight);
}
```

```c
/* 구조체 예제2 */
#include <stdio.h>
char copy_str(char* dest, const char* src);
struct Books {
	char name[30];
	char auth[30];
	char publ[30];
	int borrowed;
};
int main() {
	struct Books Harry_Potter;

	copy_str(Harry_Potter.name, "Harry Potter");
	copy_str(Harry_Potter.auth, "J.K. Rolling");
	copy_str(Harry_Potter.publ, "Scholastic");
	Harry_Potter.borrowed = 0;

	printf("책 이름 : %s \n", Harry_Potter.name);
	printf("저자 이름 : %s \n", Harry_Potter.auth);
	printf("출판사 이름 : %s \n", Harry_Potter.publ);

	return 0;
}
char copy_str(char *dest, const char *src) {
	while (*src) {
		*dest = *src;
		src++;
		dest++;
	}

	*dest = '\0';

	return 1;
}
```

```c
/* 구조체 예제2 */
#include <stdio.h>
struct Books {
	char name[30];
	char auth[30];
	char publ[30];
	int borrowed;
};
int main() {
	struct Books book_list[3];
	int i;

	for (i = 0; i < 3; i++) {
		printf("%d번째 책 정보 입력", i);
		scanf("%s%s%s", book_list[i].name, book_list[i].auth, book_list[i].publ);
		book_list[i].borrowed = 0;
	}

	for (i = 0; i < 3; i++) {
		printf("------------------------------- \n");
		printf("%d번째 책 정보 \n", i);
		printf("이름 : %s \n", book_list[i].name);
		printf("저자 : %s \n", book_list[i].auth);
		printf("출판사 : %s \n", book_list[i].publ);

		if (book_list[i].borrowed == 0) {
			printf("안 빌려감 \n");
		}
		else {
			printf("빌려감 \n");
		}
	}

	return 0;
}
```



##### 구조체 포인터 및 `->`라는 새로운 연산자 도입

- `(*ptr).a`라는 문장은 `ptr->a`로 사용할 수 있다.

```c
/* 구조체 포인터 */
#include <stdio.h>
struct test {
	int a, b;
};
int main() {
	struct test st;
	struct test *ptr;

	ptr = &st;

	//(*ptr).a = 1;
	ptr->a = 1;
	//(*ptr).b = 2;
	ptr->b = 2;

	printf("st의 1멤버 : %d \n", st.a);
	printf("st의 2멤버 : %d \n", st.b);

	return 0;
}
```



### 16-2. 모아 모아 구조체(struct) - 구조체 인자로 가진 함수

##### 구조체 포인터

```c
/* 구조체 포인터 연습 */
#include <stdio.h>
int add_one(int *a);
struct TEST {
	int c;
};
int main() {
	struct TEST t;
	struct TEST *pt = &t;

	pt->c = 0;

	add_one(&t.c);

	printf("t.c : %d \n", t.c);

	add_one(&pt->c);

	printf("pt->c : %d \n", pt->c);

	return 0;
}
int add_one(int *a) {
	*a += 1;
	return 0;
}
```



##### 구조체의 대입

- 구조체도 `=`를 통해 서로 복사할 수 있다.

```c
/* 구조체 대입 */
#include <stdio.h>
struct TEST {
	int i;
	char c;
};
int main() {
	struct TEST st, st2;

	st.i = 1;
	st.c = 'c';

	st2 = st;

	printf("st2 : %d %c", st2.i, st2.c);

	return 0;
}
```

```c
/* 구조체 string 대입 */
#include <stdio.h>
int copy_str(char *dest, char *src);
struct TEST {
	int i;
	char str[20];
};
int main() {
	struct TEST a, b;

	b.i = 3;
	copy_str(b.str, "hello, world");

	a = b;

	printf("st2 : %d %s", a.i, a.str);

	return 0;
}
int copy_str(char *dest, char *src) {
	while (*src) {
		*dest = *src;
		src++;
		dest++;
	}
	*dest = '\0';

	return 1;
}
```



##### 구조체를 인자로 받기

```c
/* 구조체를 인자로 전달하기 */
#include <stdio.h>
int set_human(struct TEST *a, int age, int gender, char *name);
char copy_str(char* dest, const char* src);
struct TEST {
	int age;
	int gender;
	char name[30];
};
int main() {
	struct TEST human;
	set_human(&human, 10, 1, "Lim");
	printf("AGE: %d, GENDER: %d, NAME: %s", human.age, human.gender, human.name);

	return 0;
}
int set_human(struct TEST *a, int age, int gender, char* name) {
	a->age = age;
	a->gender = gender;
	copy_str(a->name, name);
	return 0;
}
char copy_str(char* dest, const char* src) {
	while (*src) {
		*dest = *src;
		src++;
		dest++;
	}

	*dest = '\0';

	return 1;
}
```



### 16-3. 구조체와 친구들(공용체(union), 열거형(enum))



##### 구조체 안의 구조체

```c
/* 구조체 안의 구조체 */
#include <stdio.h>
struct employee {
	int age;
	int salary;
};
struct company {
	struct employee data;
	char name[10];
};
int main() {
	struct company Kim;

	Kim.data.age = 31;
	Kim.data.salary = 3000000;

	printf("Kim's age : %d \n", Kim.data.age);
	printf("Kim's salary : %d$/year \n", Kim.data.salary);

	return 0;
}
```



##### 구조체를 리턴하는 함수

```c
/* 구조체를 리턴하는 함수 */
#include <stdio.h>
struct AA function(int j);
struct AA {
	int i;
};
int main() {
	struct AA a; // 구조체 변수 정의

	a = function(10);
	printf("a.i : %d \n", a.i);

	return 0;
}
struct AA function(int j) {
	struct AA A;
	A.i = j;

	return A;
}
```



##### 구조체 변수의 정의 방법

```c
/* 구조체 변수의 정의 방법 */
#include <stdio.h>
char copy_str(char* dest, char* src);
int Print_Obj_Status(struct obj* OBJ);
struct obj {
	char name[20];
	int x, y;
} Ball;
int main() {
    // struct obj Ball = {.name = "123", .x = 3, .y = 4};
    // 이런 식으로도 작업 가능
	Ball.x = 3;
	Ball.y = 4;
	copy_str(Ball.name, "RED BALL");

	Print_Obj_Status(&Ball);

	return 0;
}
int Print_Obj_Status(struct obj *OBJ) {
	printf("Location of %s \n", (*OBJ).name);
	printf("( %d , %d ) \n", OBJ->x, OBJ->y);

	return 0;
}
char copy_str(char* dest, char* src) {
	while (*src != NULL) {
		*dest = *src;
		src++;
		dest++;
	}
	*dest = '\0';

	return 1;
}
```

```c
/* 구조체 변수의 정의 방법 */
#include <stdio.h>
int Print_Status(struct HUMAN *human);
struct HUMAN {
	int age;
	int height;
	int weight;
	int gender;
};
int main() {
	struct HUMAN Eve = { 27, 166, 58, 0 };
	struct HUMAN Adam = { 31, 182, 75, 1 };
	
	Print_Status(&Adam);
	Print_Status(&Eve);


	return 0;
}
int Print_Status(struct HUMAN *human) {
	if (human->gender == 0) {
		printf("FEMALE \n");
	}
	else {
		printf("MALE \n");
	}

	printf("AGE: %d, HEIGHT: %d, WEIGHT: %d \n", human->age, human->height, human->weight);
	if (human->gender == 0 && human->height >= 180) {
		printf("HE IS A WINNER! \n");
	}
	else if (human->gender == 0 && human->height <= 180) {
		printf("HE IS A LOSER! \n");
	}

	return 0;
}
```



##### 구조체 초기화 방식

```c
///////////////////// 지역
struct obj {
  char name[20];
  int x, y;
}
int main(){
    struct obj Ball = {.name = "abc", .x = 3, .y = 4};
}

///////////////////// 글로벌
struct obj {
  char name[20];
  int x, y;
} Ball = {"abc", 3, 4};
```



##### 공용체(union)

- 공용체는 각 멤버들의 메모리 시작 주소가 동일하며 구조체와 달리 메모리를 공유한다.

![](https://modoocode.com/img/1210640D4C14DC693AF455.webp)

```c
/* 공용체 */
#include <stdio.h>
union A {
	int i;
	char j;
};
int main() {
	union A a;
	a.i = 0x12345678;
	printf("%x", a.j);

	return 0;
}

// answer
// 78
```

- 일반적으로 컴퓨터에서는 높은 주소값에 상위 비트를 적는 리틀 엔디안을 사용하고 있다.



##### 열거형 (Enum)

- 열거형으로 정의하면 컴파일러는 각 원소에 0부터 차례로 정수값을 매긴다.
- 0부터 순서대로가 아닌 원하는 수로 지정할 수 있다.

```c
/* 열거형의 도입 */
#include <stdio.h>
enum { RED, BLUE, WHITE, BLACK};
int main() {
	int palette = 2;
	switch (palette) {
		case RED:
			printf("palette : RED \n");
			break;
		case BLUE:
			printf("palette : BLUE \n");
			break;
		case WHITE:
			printf("palette : WHITE \n");
			break;
		case BLACK:
			printf("palette : BLACK \n");
			break;
	}

	return 0;
}
```

```c
/* 열거형의 도입 2 */
#include <stdio.h>
enum { RED = 3, BLUE, WHITE, BLACK};
int main() {
	int palette = BLACK;
	printf("%d \n", palette);

	return 0;
}
```

