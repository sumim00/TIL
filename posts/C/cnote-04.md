# 씹어먹는 C언어 필기 (11~강)

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

