# 씹어먹는 C언어 필기 (11~12강)

>  Psi님의 [씹어먹는 C언어](<https://modoocode.com/231>) 강좌를 수강하며 기록한 노트입니다.



### 11-1. C언어의 아파트(배열), 상수

배열 : 특정한 형(Type)의 변수들의 집합

```c
/* 배열 기초 */
#include <stdio.h>
int main() {
	int arr[10] = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };

	printf("Array 3번째 원소 : %d \n", arr[2]);

	return 0;
}
```

```c
/* 평균 구하기 */
#include <stdio.h>
int main() {
	int arr[5];
	int i, ave = 0;

	for (i = 0; i < 5; i++) {
		printf("%d 번째 학생의 성적은? ", i + 1);
		scanf("%d", &arr[i]);
	};
	for (i = 0; i < 5; i++) {
		ave = ave + arr[i];
	};
	printf("전체 학생의 평균은 : %d \n", ave / 5);

	return 0;
}
```

```c
/* 평균 구하기 + 합불여부 */
#include <stdio.h>
int main() {
	int arr[5];
	int i, ave = 0;

	for (i = 0; i < 5; i++) {
		printf("%d 번째 학생의 성적은? ", i + 1);
		scanf("%d", &arr[i]);
	};
	for (i = 0; i < 5; i++) {
		ave = ave + arr[i];
	};
	ave = ave / 5;
	printf("전체 학생의 평균은 : %d \n", ave);

	for (i = 0; i < 5; i++) {
		printf("%d 번째 학생은", i + 1);
		if (arr[i] >= ave)
			printf("합격입니다. \n");
		else
			printf("불합격입니다. \n");
	}

	return 0;
}
```



##### 소수 프로그램

```c
/* 소수 프로그램 : 내가 짠 거 */
#include <stdio.h>
int main() {
	int arr[100];
	int i, j, count;
	int ok;
	count = 0;
	i = 3;
	
	for (;;) {
		ok = 0;
		for (j = 2; j < i; j++) {
			if (i % j == 0) {
				ok = 1;
				break;
			}
		}
		if (ok == 0) {
			arr[count] = i;
			count++;
		}
		i++;
		if (count == 100) {
			break;
		}
	}
	printf("소수들 : ");
	for (i = 0; i < count; i++) {
		printf("%d , ", arr[i]);
	}

	return 0;
}
```

```c
/* 소수 프로그램 */
#include <stdio.h>
int main() {
	int guess = 5;
	int prime[1000];
	int index = 1;
	int i;
	int ok;
	prime[0] = 2;
	prime[1] = 3;

	for (;;) {
		ok = 0;
		for (i = 0; i < index; i++) {
			if (guess % prime[i] != 0) {
				ok++;
			}
			else {
				break;
			}
		}
		if (ok == (index + 1)) {
			index++;
			prime[index] = guess;
			printf("소수 : %d \n", prime[index]);
			if (index == 999) break;
		}
		guess += 2;
	}

	return 0;
}
```



##### 상수

```c
const (상수의 형) (상수 이름) = (상수의 값);
```

```c
/* 상수 */
#include <stdio.h>
int main() {
	const int a = 3;

	printf("%d", a);

	return 0;
}
```



##### 초기화되지 않은 값

```c
/* 초기화 되지 않은 값 */
#include <stdio.h>
int main() {
	int arr[3] = { 1 };
	
	printf("네 값은 뭐니 : %d", arr[1]);
	return 0;
}
// answer
0
```

- 위와 같이 정의한다면 컴파일러는 내부적으로 `int arr[3] = { 1, 0, 0 }`으로 인식한다. 



##### 연습문제

```c
/* 문제1 : 학생 성적순 정렬하기 */
#include <stdio.h>
int main() {
	int arr[10];
	int i, j, k = 0;

	for (i = 0; i < 10; i++) {
		printf("%d 번째 학생의 성적은?", i + 1);
		scanf("%d", &arr[i]);
	}

	for (i = 0; i < 10; i++) {
		for (j = i+1; j < 10; j++) {
			if (arr[i] < arr[j]) {
				k = arr[i];
				arr[i] = arr[j];
				arr[j] = k;
			}
		}
	}

	printf("성적순 정렬 결과 \n");
	for (i = 0; i < 10; i++) {
		printf("%d 등 : %d \n", i+1, arr[i]);
	}
	
	return 0;

}
```

```c
/* 문제2 : 학생 성적 막대그래프 */
#include <stdio.h>
int main() {
	int arr[10];
	int i, j, k = 0;

	for (i = 0; i < 10; i++) {
		printf("%d 번째 학생의 성적은?", i + 1);
		scanf("%d", &arr[i]);
	}

	for (i = 0; i < 10; i++) {
		printf("%d 번째 학생의 그래프", i + 1);
		k = arr[i];
		for (j = 0; j < k; j++) {
			printf("■");
		}
		printf("\n");
	}

	return 0;

}
```



### 11-2. C언어의 아파트2 (고차원의 배열)

#####  배열의 배열

```c
(배열의 형) (배열의 이름)[?][?];
```

```c
/* 2차원 배열 */
#include <stdio.h>
int main() {
	int arr[3][3] = { 1, 2, 3, 4, 5, 6, 7, 8, 9 };

	printf("arr 배열의 2행 3열의 수를 출력 : %d \n", arr[1][2]);
	printf("arr 배열의 1행 2열의 수를 출력 : %d \n", arr[0][1]);

	return 0;

}
```

```c
/* 학생 점수 입력 받기 */
#include <stdio.h>
int main() {
	int score[3][2];
	int i, j;

	for (i = 0; i < 3; i++) {
		for (j = 0; j < 2; j++) {
			if (j == 0) {
				printf("%d번째 학생의 국어 점수 : ", i + 1);
				scanf("%d", &score[i][j]);
			}
			else if (j == 1) {
				printf("%d번째 학생의 수학 점수 : ", i + 1);
				scanf("%d", &score[i][j]);
			}
		}
	}

	for (i = 0; i < 3; i++) {
		printf("%d번째 학생의 국어 점수 : %d, 수학 점수 : %d \n", i + 1, score[i][0], score[i][1]);
	}

	return 0;

}
```



##### 2차원 배열 정의하기

```c
int arr[2][3] = { 1, 2, 3, 4, 5, 6 };			// O
int arr[2][3] = { {1, 2, 3}, {4, 5, 6} };		// O
int arr[] = { 1, 2, 3, 4 };						// O
int arr[];										// X 배열의 크기는 임의로 정해지지 않는다.
int arr[][3] = { {4, 5, 6}, {7,8, 9} };			// O
int arr[][2] = { {1, 2}, {3, 4}, {5, 6}, {7} }; // O
int arr[2][] = { {4, 5, 6}, {7, 8, 9} };		// X 다차원 배열에선 맨 앞의 크기를 제외한 나머지 크기들은 정확히 지정해줘야 한다.
```





### 12-1. 포인터는 영희이다! (포인터)

- 포인터 : 특정한 데이터의 주소값을 보관하는 변수.

```c
(포인터에 주소값이 저장되는 데이터의 형) *(포인터의 이름);
// or
(포인터에 주소값이 저장되는 데이터의 형)* (포인터의 이름);
```

```c
/* 포인터의 시작 */
#include <stdio.h>
int main() {
	int *p;
	int a;
	a = 2;

	p = &a;

	printf("포인터 p에 들어 있는 값 : %p \n", p);
	printf("int 변수 a가 저장된 장소 : %p \n", &a);
	return 0;
}
// answer
포인터 p에 들어 있는 값 : 00B5F93C
int 변수 a가 저장된 장소 : 00B5F93C
```

```c
/* *연산자의 이용 */
#include <stdio.h>
int main() {
	int *p;
	int a;

	p = &a;
	a = 2;

	printf("a의 값 : %d \n", a);
	printf("*p의 값 : %d \n", *p);
	return 0;
}

// answer
a의 값 : 2
* p의 값 : 2
```



- `&` : 특정 메모리의 주소값을 알 수 있는 단항 연산자.
- `*` : 포인터에 저장된 주소값에 위치한 데이터를 알 수 있는 단항 연산자.

```c
/* 연산자 */
#include <stdio.h>
int main() {
	int *p;
	int a;
	a = 2;

	p = &a;
	*p = 3;

	printf("a의 값 : %d \n", a);
	printf("p의 값 : %d \n", *p);
	return 0;
}
// answer
a의 값 : 3
p의 값 : 3
```



##### 상수 포인터

```c
/* 상수 포인터? */
#include <stdio.h>
int main() {
  int a;
  int b;
  const int* const pa = &a;

  *pa = 3;  // 올바르지 않은 문장
  pa = &b;  // 올바르지 않은 문장

  return 0;
}
```



##### 포인터의 덧셈, 뺄셈

- 포인터는 포인터가 가리키는 형의 크기만큼 계산한다  

```c
/* 포인터의 덧셈 */
#include <stdio.h>
int main() {
	int a;
	char b;
	double c;
	int* pa = &a;
	char* pb = &b;
	double* pc = &c;

	printf("pa의 값 : %p \n", pa);
	printf("(pa + 1)의 값 : %p \n", pa + 1);
	printf("pb의 값 : %p \n", pb);
	printf("(pb + 1)의 값 : %p \n", pb + 1);
	printf("pc의 값 : %p \n", pc);
	printf("(pc + 1)의 값 : %p \n", pc + 1);

	return 0;
}

// answer
pa의 값 : 010BF74C
(pa + 1)의 값 : 010BF750
pb의 값 : 010BF743
(pb + 1)의 값 : 010BF744
pc의 값 : 010BF730
(pc + 1)의 값 : 010BF738

```



##### 배열과 포인터와의 관계

- 배열의 이름을 그대로 출력하면 배열의 첫 번째 원소의 주소값을 나타낸다.

```c
#include <stdio.h>
int main() {
  int arr[3] = {1, 2, 3};

  printf("arr 의 정체 : %p \n", arr);
  printf("arr[0] 의 주소값 : %p \n", &arr[0]);

  return 0;
}

// answer
arr 의 정체 : 0x7fff1e868b1c 
arr[0] 의 주소값 : 0x7fff1e868b1c 
```



##### `[]` 연산자

- 우리가 `[]`을 사용하면 컴파일러에 의해 자동으로 `*()`으로 변환된다.

```c
/* [] 연산자 */
#include <stdio.h>
int main() {
	int arr[5] = { 1, 2, 3, 4, 5 };

	printf("arr[3] : %d \n", arr[3]);
	printf("*(arr+3) : %d \n", *(arr + 3));
	return 0;
}

// answer
arr[3] : 4
* (arr + 3) : 4
```





##### 1차원 배열을 가리키는 포인터

```c
/* 1차원 배열 가리키기 */
#include <stdio.h>
int main() {
	int arr[3] = { 1, 2, 3 };
	int *parr;

	parr = arr;
	// parr = &arr[0] 와 동일

	printf("arr[1] : %d \n", arr[1]);
	printf("parr[1] : %d \n", parr[1]);
	return 0;
}
```

```c
/* 포인터 이용하기 */
#include <stdio.h>
int main() {
	int arr[10] = { 100, 98, 97, 95, 94, 91, 100, 99, 90, 99 };
	int *parr = arr;
	int sum = 0;

	while (parr - arr <= 9) {
		sum += (*parr);
		parr++;
	}

	printf("내 시험점수 평균 : %d \n", sum / 10);
	return 0;
}
```





##### 2차원 배열을 가리키는 포인터

``` c
/* 2차원 배열의 행/열 개수 구하기 */
#include <stdio.h>
int main() {
	int arr[2][3] = { {1, 2, 3}, {4, 5, 6} };

	printf("전체 크기 : %d \n", sizeof(arr));
	printf("총 열의 개수 : %d \n", sizeof(arr[0]) / sizeof(arr[0][0]));
	printf("총 행의 개수 : %d \n", sizeof(arr) / sizeof(arr[0]));

	return 0;
}
```



- 2차원 배열을 가리키는 포인터는 배열의 크기에 관한 정보가 있어야 한다.

```c
/* (배열의 형) */ (* /*포인터 이름*/)[/*2차원 배열의 열 개수*/];
int (*parr)[3];
```

```c
/* 배열의 포인터 */
#include <stdio.h>
int main() {
	int arr[2][3] = { {1, 2, 3}, {4, 5, 6} };
	int(*parr)[3];

	parr = arr;

	printf("parr[1][2] : %d, arr[1][2] : %d \n", parr[1][2], arr[1][2]);

	return 0;
}
```



##### 더블 포인터 (`**`)

- 포인터를 가리키는 포인터

```c
/* 포인터의 포인터 */
#include <stdio.h>
int main() {
	int a;
	int *pa;
	int **ppa;

	pa = &a;
	ppa = &pa;

	a = 3;

	printf("a : %d, *pa : %d, **ppa : %d \n", a, *pa, **ppa);
	printf("&a : %p, pa : %p, ppa : %p \n", &a, pa, *ppa);
	printf("&pa : %p, ppa : %p \n", &pa, ppa);
	return 0;
}

// answer
a: 3, * pa : 3, ** ppa : 3
& a : 008FF9F0, pa : 008FF9F0, ppa : 008FF9F0
& pa : 008FF9E4, ppa : 008FF9E4
```



##### 포인터 배열

```c
/* 포인터 배열 */
#include <stdio.h>
int main() {
	int *arr[3];
	int a = 1, b = 2, c = 3;
	arr[0] = &a;
	arr[1] = &b;
	arr[2] = &c;

	printf("a : %d, *arr[0] : %d \n", a, *arr[0]);
	printf("b : %d, *arr[1] : %d \n", b, *arr[1]);
	printf("c : %d, *arr[2] : %d \n", c, *arr[2]);

	printf("&a : %d, arr[0] : %d \n", &a, arr[0]);

	return 0;
}
```

