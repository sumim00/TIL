# 씹어먹는 C언어 필기 (21~22강)

> Psi님의 [씹어먹는 C언어](<https://modoocode.com/231>) 강좌를 수강하며 기록한 노트입니다.



### 21. 매크로 함수, 인라인 함수

##### 매크로 함수

- 전처리기가 문장 그대로 치환하기 때문에 괄호를 제대로 쓰지 않을 경우 오류가 나기 쉽다.
- `#` : 인자 앞에 #를 붙이면 문자열로 바뀐다. `#var -> "var"`
- `##` : 입력된 것을 하나로 합쳐준다. `x##y -> xy`

```c
#define (함수이름(인자)) (치환할 것)
```

```c
/* 매크로 함수 */
#include <stdio.h>
#define square(x) x * x

int main() {
    printf("square(3) : %d \n", square(3)); // 3 * 3 으로 치환
    printf("square(3 + 1) : %d \n", square(3 + 1)); // 3 + 1 * 3 + 1 로 치환
    return 0;
}

// square(3) : 9
// square(3 + 1) : 7
// 위와 같은 오류를 해결하기 위해서는 #define square(x) (x) * (x) 형태로 변경
```

```c
/* 라디안에서 도로 바꾸기 */
#include <stdio.h>
#define RADTODEG(x) (x) * 57.295

int main() {
    printf("5 rad는 : %f 도 \n", RADTODEG(5));
    printf("1/5 rad는 : %f 도 \n", 1 / RADTODEG(5));
    return 0;
}

// 5 rad는 : 286.475000 도
// 1 / 5 rad는 : 0.000000 도
// 위와 같은 오류를 해결하기 위해서는 #define RADTODEG(x) ((x) * 57.295) 형태로 변경
```

```c
/* 변수의 이름 출력하기 */
#include <stdio.h>
#define PrintVariableName(var) printf(#var "\n"); 
// 인자 앞에 #를 붙이면 문자열로 바뀐다. #var -> "var"

int main() {
    int a;

    PrintVariableName(a);

    return 0;
}

// a
```

```c
/* ##의 사용 */
#include <stdio.h>
#define AddName(x, y) x##y
// 입력된 것을 하나로 합쳐준다. x##y -> xy

int main() {
    int AddName(a, b);

    ab = 3;

    printf("%d \n", ab);

    return 0;
}

// 3
```



##### 인라인 함수

- 매크로 함수의 문제를 해결하기 위한 함수.
- 단순한 작업들을 보기 편하게 처리할 수 있다.
- 특징 : 매크로 함수와 동일하게 함수를 직접 호출받고 리턴받는 형태가 아닌 바로 치환한다는 특징이 있다.
- 장점 : 매크로 함수와 달리 컴파일러가 똑똑하게 진짜 함수처럼 동작하게 해준다는 장점이 있으며 디버깅 또한 편리하다.

```c
/* 인라인 함수 */
#include <stdio.h>
__inline int square(int a) { return a * a; }

int main() {
    printf("%d", square(3+1));

    return 0;
}

// 16
```

```c
/* 인라인 함수 2 */
#include <stdio.h>
__inline int max(int a, int b) {
    if (a > b) {
        return a;
    }
    else {
        return b;
    }
}

int main() {
    printf("3과 2중 최대값은 : %d", max(3, 2));

    return 0;
}

// 3과 2중 최대값은 : 3
```



### 22. C언어의 잡다한 키워드들 (typedef, volatile, #pragma)

##### `typedef`

- 형이 자주 바뀌거나, 장문의 형을 짧게 축약하고 싶을 경우 사용한다.

```c
typedef (이름을 새로 부여하고자 하는 타입) (새로 준 타입의 이름)
```

```c
/* typedef의 이용 */
#include <stdio.h>
struct HUMAN {
    int age;
    int height;
    int weight;
    int gender;
};
typedef struct HUMAN Human;
int Print_status(Human human);
int main() {
    struct HUMAN Eve = { 27, 168, 70, 0 };
    struct HUMAN Adam = { 23, 180, 75, 1 };

    Print_status(Eve);
    Print_status(Adam);

    return 0;
}
int Print_status(Human human) {
    if (human.gender == 0) {
        printf("Female \n");
    }
    else {
        printf("Male \n");
    }

    printf("Age: %d, Height: %d, Weight: %d \n", human.age, human.height, human.weight);

    if (human.gender == 1 && human.height >= 180) {
        printf("He is Winner! \n");
    }
    else if (human.gender == 1 && human.height < 180) {
        printf("He is Looser! \n");
    }

    return 0;
}
```

```c
/* 간단한 계산기 프로그램 */
#include <stdio.h>
typedef int CAL_TYPE;
int main() {
    CAL_TYPE input;
    CAL_TYPE a, b;

    while (1) {
        printf("----------- 계산기 ----------- \n");
        printf("1. 덧셈 \n");
        printf("2. 뺄셈 \n");
        printf("3. 종료 \n");

        scanf("%d", &input);
        if (input == 1) {
            printf("두 수 : ");
            scanf("%d %d", &a, &b);
            printf("%d와 %d의 합 : %d \n", a, b, a + b);
        }
        else if (input == 2) {
            printf("두 수 : ");
            scanf("%d %d", &a, &b);
            printf("%d와 %d의 차 : %d \n", a, b, a - b);
        }
        else 
        break;
    }

    return 0;
}
```

```c
/* 여러가지 typedef 예제들 */

#include <stdio.h>
int add(int a, int b) { return a + b; }
typedef int CAL_TYPE;
typedef int (*Padd)(int, int);
typedef int Arrays[10];
int main() {
    CAL_TYPE a = 10;
    // == int a = 10;
    Arrays arr = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 0 };
    // == int arr[10] = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 0 };
    Padd ptr = add;
    // == int (*ptr)(int, int) = add;
    printf("a : %d \n", a);
    printf("arr[3] : %d \n", arr[3]);
    printf("add(3, 5) : %d \n", ptr(3, 5));
    return 0;
}
```



##### `volatile`

- `volatile` : 최적화 작업을 수행하지 않는다.

```c
/* volatile */
#include <stdio.h>

typedef struct SENSOR {
    int sensor_flag;
    int data;
} SENSOR;

int main() {
    volatile SENSOR* sensor;
    while (!(sensor->sensor_flag)) {
    }
    printf("Data: %d \n", sensor->data);

    return 0;
}
```





##### `#pragma`

- 컴파일러에게 말하는 전처리기 명령
- `#pragma pack(숫자)` : 구조체가 더블 워드 경계에 (데이터가 4의 배수) 놓인 경우 주로 사용한다. 숫자의 배수만큼 구조체 크기를 할당한다.
- `#pragma once` : 헤더 파일을 한 번만 읽게 한다.

```c
/* #pragma pack */
#include <stdio.h>
/* 전처리기 명령에는 ;를 붙이지 않는다. */
#pragma pack(1)

struct Weird {
    char arr[2];
    int i;
};

int main() {
    struct Weird a;
    printf("size of a : %d \n", sizeof(a));
    return 0;
}
// pragma 이전 : size of a : 8
// pragma 이후 : size of a : 6
```



##### 헤더파일 중복 방지하는 법 (#pragma once)

```c
////// 1번째 weird.h
#ifndef WEIRD_H // WEIRD_H가 없으면 참.
#define WEIRD_H
struct Weird {
    char arr[2];
    int i;
};
#endif

////// 2번째 weird.h
#pragma once
struct Weird {
    char arr[2];
    int i;
};

////// main.c
#include <stdio.h>
#include "weird.h"
#include "weird.h"

int main() {
    struct Weird a;
    a.i = 3;
    printf("Weird 구조체의 a.i : %d \n", a.i);
    return 0;
}
```

