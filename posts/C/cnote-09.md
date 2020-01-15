# 씹어먹는 C언어 필기 (19강)

> Psi님의 [씹어먹는 C언어](<https://modoocode.com/231>) 강좌를 수강하며 기록한 노트입니다.



### 19. main 함수의 인자,  텅 빈 void 형

##### `void`형의 함수, `void`형의 포인터에 대한 이해

- `void`형 함수 : 아무것도 리턴하지 않는 함수.
- `void`형 변수 : 메모리상에 얼만큼의 공간을 설정해야 하는지 모르기 때문에 포인터에 사용하기 적합하다.

```c
/* void */
#include <stdio.h>
void swap(int* a, int* b) {
    int temp;
    temp = *a;
    *a = *b;
    *b = temp;
}

int main() {
    int a = 5;
    int b = 3;
    
    printf("a = %d, b = %d", a, b);

    swap(&a, &b);

    printf("a = %d, b = %d", a, b);

    return 0;
}

```

```c
/* 임의의 주소값 p로부터 byte만큼 읽는 함수 */
#include <stdio.h>
int read_char(void* p, int byte);
int main() {
    int arr[1] = { 0x12345678 };

    printf("arr : %x \n", arr[0]);
    read_char(arr, 4);

    return 0;
}
int read_char(void *p, int byte) {
    do {
        printf("%x \n", *(char*)p);
        byte--;
        p = (char*)p + 1;
    } while (p && byte);

    return 0;
}

```



##### `main` 함수의 인자에 대한 이해(`argc`, `argv`)

- `argc` : 프로그램의 받은 인자의 개수
- `argv` :  프로그램이 받은 인자의 배열

```c
/* main 함수의 인자 */
#include <stdio.h>
int main(int argc, char **argv) {
    int i;
    printf("받은 인자의 개수 : %d \n", argc);
    for (i = 0; i < argc; i++) {
        printf("이 프로그램이 받은 인자 : %s \n", argv[i]);
    }
    return 0;
}
```



### 20-1. 동동동 메모리 동적 할당 (Dynamic Memory Alocation)

##### `malloc` 함수의 이해

- `malloc()` : 자신이 할당한 메모리의 시작 주소를 리턴. 공원에서 원하는 크기의 돗자리를 깔아주는 역할.
- `free()`: 할당받은 메모리 영역을 다 쓴 후 다시 컴퓨터에 돌려주는 함수. free를 제대로 하지 않을 경우 메모리 누수의 문제가 생김.



##### 1차원 배열 메모리 동적 할당 

```c
/* 동적 할당의 이용 */
#include <stdio.h>
#include <stdlib.h>

int main(int argc, char **argv) {
    int student;
    int i, input;
    int* score;
    int sum = 0;

    printf("학생의 수는?");
    scanf("%d", &student);

    score = (int*)malloc(sizeof(int) * student);

    for (i = 0; i < student; i++) {
        printf("학생 %d의 점수", i);
        scanf("%d", &input);

        score[i] = input;
    }

    for (i = 0; i < student; i++) {
        sum += score[i];
    }

    printf("전체 학생 평균 점수 : %d \n", sum / student);
    free(score);

    return 0;
}
```



##### 

##### 2차원 배열 메모리 동적 할당

- 메모리 해제는 할당 순서와 정반대로 실행한다.

```c
/* 2차원 배열의 동적 할당 */
#include <stdio.h>
#include <stdlib.h>

int main(int argc, char **argv) {
    int i;
    int x, y;
    int** arr;

    printf("우리는 arr[x][y]를 만들 것입니다. \n");
    scanf("%d %d", &x, &y);

    arr = (int**)malloc(sizeof(int) * x);
    // int* 형의 원소를 x개 가지는 1차원 배열 생성

    for (i = 0; i < x; i++) {
        arr[i] = (int*)malloc(sizeof(int) * y);
    }

    printf("생성 완료! \n");

    for (i = 0; i < x; i++) {
        free(arr[i]);
    }

    free(arr);

    return 0;
}
```

```c
/* 2차원 배열의 동적 할당 */
#include <stdio.h>
#include <stdlib.h>

void get_average(int** arr, int numStudent, int numSubject);

int main(int argc, char **argv) {
    int i, j, input, sum = 0;
    int subject, students;
    int** arr;

    printf("과목 수 :");
    scanf("%d", &subject);

    printf("학생 수 :");
    scanf("%d", &students);

    arr = (int**)malloc(sizeof(int) * subject);
    // int* 형의 원소를 x개 가지는 1차원 배열 생성

    for (i = 0; i < subject; i++) {
        arr[i] = (int*)malloc(sizeof(int) * students);
    }

    for (i = 0; i < subject; i++) {
        printf("과목 %d 점수 : \n", i);
        for (j = 0; j < students; j++) {
            printf("학생 %d 점수 입력 : \n", j);
            scanf("%d", &input);

            arr[i][j] = input;
        }
    }

    get_average(arr, students, subject);

    for (i = 0; i < subject; i++) {
        free(arr[i]);
    }

    free(arr);

    return 0;
}
void get_average(int **arr, int numStudent, int numSubject) {
    // **arr는 사실상 1차원 배열이기 때문에 (*arr)[3] 처럼 안써도 됨,
    int i, j, sum;

    for (i = 0; i < numSubject; i++) {
        sum = 0;
        for (j = 0; j < numStudent; j++) {
            sum += arr[i][j];
        }
        printf("과목 %d 평균 점수 : %d \n", i, sum / numStudent);
    }
}
```

