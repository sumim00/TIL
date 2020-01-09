# 씹어먹는 C언어 필기 (13~14강)

>  Psi님의 [씹어먹는 C언어](<https://modoocode.com/231>) 강좌를 수강하며 기록한 노트입니다.



### 13-1. 마술 상자 함수 (function)

##### 함수

- 함수 : 특별한 값을 입력 받아 연산을 취하여 결과를 출력하는 것.
- 사용방법 : `리턴형 함수명 () {};`

```c
/* 함수 */
#include <stdio.h>
int print_hello() {
	printf("Hello! \n");
	return 0;
}
int main() {
	printf("함수를 불러보자 : ");
	print_hello();

	printf("또 부를까? : ");
	print_hello();
	return 0;
}
```



##### `main` 함수

- 컴퓨터는 프로그램을 실행할 때 `main ` 함수부터 찾는다.
- `main` 함수가 리턴하는 데이터는 운영체제가 받는다.



##### 인자

```c
/* 함수의 인자 */
#include <stdio.h>
int slave(int master_money) {
	master_money += 10000;
	return master_money;
}
int main() {
	int my_money = 100000;
	printf("2020.01.07 재산 : $%d", slave(my_money));

	return 0;
}
```

```c
// 연습문제 5 : N을 인자로 받아 소인수분해 결과 출력하기
#include <stdio.h>
int factorize(int N) {
    int k = 2;

    for (;;) {
        if (N != k && N % k == 0) {
            N = N / k;
            printf("%d * ", k);
        }
        else if (N != k && N% k != 0) {
            k++;
        }
        else if (N == k) {
            printf("%d", k);
            break;
        }
        
    };

    return 0;
}
int main() {
    int N;
    
    printf("소인수분해할 수 : ");
    scanf("%d", &N);
    
    factorize(N);

    return 0;
}
```





### 13-2. 마술 상자 함수 (function)

##### 포인터로 받는 인자

- 어떤 함수가 특정한 타입의 변수/배열의 값을 바꾸려면 함수의 인자는 반드시 타입을 가리키는 포인터형을 이용해야 한다.

```c
/* 드디어 써먹는 포인터 */
#include <stdio.h>
int change_val(int *pi) {
    printf("-------- change_val 함수 안에서 --------\n");
    printf("pi의 값 : %p \n", pi);
    printf("pi가 가리키는 것의 값 : %d \n", *pi);

    *pi = 3;

    printf("-------- change_val 함수 끝~ --------\n");
    return 0;
}
int main() {
    int i = 0;

    printf("i 변수의 주소값 : %p \n", &i);
    printf("호출 이전의 i의 값 : %d \n", i);
    change_val(&i);
    printf("호출 이후의 i의 값 : %d \n", i);

    return 0;
}
```

```c
/* 두 변수의 값을 교환하는 함수 */
#include <stdio.h>
int swap(int *a, int *b) {
    int temp = *a;

    *a = *b;
    *b = temp;
    
    return 0;
}
int main() {
    int i, j;

    i = 3;
    j = 5;

    printf("SWAP 이전 : i : %d, j : %d \n", i, j);

    swap(&i, &j);

    printf("SWAP 이후 : i : %d, j : %d \n", i, j);

    return 0;
}
```



##### 함수의 원형

- 함수의 정의 부분을 맨 위에 한번 더 써주는 것.
- 오류를 잡아낼 수 있다.

```c
/* 함수의 원형 */
#include <stdio.h>
int swap(int* a, int* b);
int main() {
    int i, j;

    i = 3;
    j = 5;

    printf("SWAP 이전 : i : %d, j : %d \n", i, j);

    swap(&i, &j);

    printf("SWAP 이후 : i : %d, j : %d \n", i, j);

    return 0;
}

int swap(int* a, int* b) {
    int temp = *a;

    *a = *b;
    *b = temp;

    return 0;
}
```



##### 배열을 인자로 받기

```c
/* 배열을 인자로 받기 */
#include <stdio.h>
int add_number(int *parr);
int main() {
    int arr[3];
    int i;

    /* 사용자로부터 3개의 원소를 입력받는다. */
    for (i = 0; i < 3; i++) {
        scanf("%d", &arr[i]);
    }

    add_number(arr);

    printf("배열의 각 원소 : %d, %d, %d", arr[0], arr[1], arr[2]);

    return 0;
}

int add_number(int *parr) {
    int i;
    for (i = 0; i < 3; i++) {
        parr[i]++;
    }

    return 0;
}
```

```c
/* 입력받은 배열의 10개의 원소들 중 최대값을 출력 */
#include <stdio.h>
int max_number(int* parr);
int main() {
    int arr[10];
    int i;

    /* 사용자로부터 10개의 원소를 입력받는다. */
    for (i = 0; i < 10; i++) {
        scanf("%d", &arr[i]);
    }

    printf("배열의 최대값 : %d", max_number(arr));

    return 0;
}

int max_number(int *parr) {
    int i;
    int max = parr[0];
    for (i = 0; i < 10; i++) {
        if (parr[i] > max) {
            max = parr[i];
        }
    }

    return max;
}
```

```c
/* 연습문제 2 : 입력받은 배열의 10개의 원소들 중 최대값을 출력 */
#include <stdio.h>
int max_number(int* parr);
int main() {
    int arr[10];
    int i;

    /* 사용자로부터 10개의 원소를 입력받는다. */
    for (i = 0; i < 10; i++) {
        scanf("%d", &arr[i]);
    }

    max_number(arr);

    return 0;
}

int max_number(int *parr) {
    int i, j;
    int temp;
    for (i = 0; i < 10; i++) {
        for (j = i+1; j < 10; j++) {
            if (parr[i] < parr[j]) {
                temp = parr[i];
                parr[i] = parr[j];
                parr[j] = temp;
            }
        }
        printf("%d번째 %d \n", i + 1, parr[i]);
    }


    return 0;
}
```



### 13-3. 마술 상자 함수 (function)

##### 더블 포인터 인자

```c
/* 포인터가 가리키는 변수를 서로 바꾼다 */
#include <stdio.h>
int pswap(int **pa, int **pb);
int main() {
    int a, b;
    int *pa, *pb;

    pa = &a;
    pb = &b;

    printf("pa 가 가리키는 변수의 주소값 : %p \n", pa);
    printf("pa 의 주소값 : %p \n \n", &pa);
    printf("pb 가 가리키는 변수의 주소값 : %p \n", pb);
    printf("pb 의 주소값 : %p \n", &pb);

    printf(" ------------- 호출 -------------- \n");
    pswap(&pa, &pb);
    printf(" ------------- 호출끝 -------------- \n");

    printf("pa 가 가리키는 변수의 주소값 : %p \n", pa);
    printf("pa 의 주소값 : %p \n \n", &pa);
    printf("pb 가 가리키는 변수의 주소값 : %p \n", pb);
    printf("pb 의 주소값 : %p \n", &pb);


    return 0;
}

int pswap(int **ppa, int **ppb) {
    int *temp = *ppa;

    printf("ppa 가 가리키는 변수의 주소값 : %p \n", ppa);
    printf("ppb 가 가리키는 변수의 주소값 : %p \n", ppb);

    *ppa = *ppb;
    *ppb = temp;

    return 0;
}
```



##### 2차원 배열 인자

```c
/* 2차원 배열의 각 원소를 1씩 증가시키는 함수 */
#include <stdio.h>
int add1_element(int(*arr)[2], int row);
int main() {
    int arr[3][2];
    int i, j;

    for (i = 0; i < 3; i++) {
        for (j = 0; j < 2; j++) {
            scanf("%d", &arr[i][j]);
        }
    }

    add1_element(arr, 3);

    for (i = 0; i < 3; i++) {
        for (j = 0; j < 2; j++) {
            printf("arr[%d][%d] : %d \n", i, j, arr[i][j]);
        }
    }

    return 0;
}

int add1_element(int (*arr)[2], int row) {
    int i, j;
    for (i = 0; i < row; i++) {
        for (j = 0; j < 2; j++) {
            arr[i][j]++;
        }
    }

    return 0;
}
```



##### 상수 인자

##### 함수 포인터

```c
(함수의 리턴형) (*포인터 이름) (첫 번째 인자 타입, 두 번째 인자 타입...)
```

```c
/* 함수 포인터 */
#include <stdio.h>
int max(int a, int b);
int main() {
    int a, b;
    int (*pmax)(int, int);
    pmax = max;

    scanf("%d %d", &a, &b);
    printf("max(a, b) : %d \n", max(a, b));
    printf("pmax(a, b) : %d \n", pmax(a, b));

    return 0;
}

int max(int a, int b) {
    if (a > b)
        return a;
    else
        return b;

    return 0;
}
```



