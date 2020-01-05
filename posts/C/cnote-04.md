# 씹어먹는 C언어 필기 (11강)

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

