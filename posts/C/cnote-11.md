# 씹어먹는 C언어 필기 (23강)

> Psi님의 [씹어먹는 C언어](<https://modoocode.com/231>) 강좌를 수강하며 기록한 노트입니다.



### 23-1. 파일하고 이야기하기 (파일 입출력에 대한 기본적 이해)

##### 파일 입출력, 스트림

- RAM과 달리 하드디스크는 비휘발성 저장매체이며 데이터를 파일 단위로 보관한다.
- 스트림 : 두 개의 다른 장치를 이어주는 파이프의 역할. 모니터와 키보드는 표준 스트림이 자동 생성되며, 파일은 `fopen`으로 생성한다.
- `FILE` : 스트림에 대한 정보가 담긴 구조체.

![](https://modoocode.com/img/154733414D1894062D76CF.webp)

##### `fopen, fputs, fgets, fgetchar` 함수

- `fopen(인자1, 인자2)` : 인자2가 `w`인 경우 쓰기만 가능하며, 인자1의 파일이 현재 없다면 생성하고 존재한다면 내용을 지운다.
- `fputs(기록할 문자열, 스트림)` : 파일에 문자열을 기록한다. 
- `fclose(스트림)`: 스트림을 닫는다. 닫지 않으면 계속 쓰기 상태로 남는다.
- `fgets(입력받을 변수, 최대 문자 개수 -1, 스트림)` : 파일의 내용을 읽어온다. 받을 메모리 크기를 제한할 수 있어 `scanf`처럼 오버플로우가 생기지 않는다. -1은 NULL을 위해 남겨놓는 것.
- `fgetc(스트림)` : 한 글자씩 입력받는다.

```c
/* a.txt에 내용을 기록한다. */
#include <stdio.h>

int main() {
	FILE* fp;
	fp = fopen("a.txt", "w");

	if (fp == NULL) { // fopen이 실패할 경우 NULL 리턴
		printf("Write Error! \n");
		return 0;
	}

	fputs("Hello World! \n", fp);

	fclose(fp);
	return 0;
}
```

```c
/* fgets로 a.txt에서 내용을 입력받는다. */
#include <stdio.h>

int main() {
	FILE* fp = fopen("a.txt", "r");
	char buf[20]; // 내용을 입력받을 곳
	if (fp == NULL) {
		printf("READ ERROR! \n");
		return 0;
	}
	fgets(buf, 20, fp);
	printf("입력받는 내용 : %s \n", buf);
	fclose(fp);

	return 0;
}
```

```c
/* fgetc - 한 글자씩 입력받기 */
#include <stdio.h>

int main() {
	FILE* fp = fopen("a.txt", "r");
	char c;

	while ((c = fgetc(fp)) != EOF) {
        //EOF : end of file. 문자열의 마지막에 NULL이 있듯 파일 마지막에는 -1가 있다.
		printf("%c", c);
	}
	fclose(fp);

	return 0;
}
```



##### 파일 위치 지정자와 `fseek` 함수

- `fseek(스트림, 지정 위치로부터 떨어진 거리, 지정위치)` : 지정위치로부터 n만큼 파일 위치지정자를 돌린다.
- 지정위치에 입력하는 매크로 상수
  - `SEEK_SET` : 파일의 맨 처음
  - `SEEK_CUR` : 현재 위치
  - `SEEK_END` : 파일의 맨 마지막

```c
/* fseek */
#include <stdio.h>

int main() {
    // 현재 fp에 abcdef가 들어있는 상태
	FILE* fp = fopen("a.txt", "r");

	fgetc(fp);
	fgetc(fp);
	fgetc(fp);
	fgetc(fp);

	// d까지 입력받았으며 파일 위치지정하는 이제 e를 가리키고 있다.

	fseek(fp, 0, SEEK_SET);
	printf("다시 파일에서 처음부터 입력받는다면 : %c \n", fgetc(fp));

	fclose(fp);

	return 0;
}

// 다시 파일에서 처음부터 입력받는다면 : a
```

```c
/* 출력 스트림도 마찬가지*/
#include <stdio.h>
int main() {
  FILE *fp = fopen("a.txt", "w");
  fputs("Psi is an excellent C programmer", fp);
  fseek(fp, 0, SEEK_SET);
  fputs("is Psi", fp); // 끼워넣기가 아닌 덮어쓰기
  fclose(fp);
  return 0;
}

// is Psi an excellent C programmer
```



### 23-2. 파일하고 이야기하기 (파일 입출력)

##### 파일 위치 지시자 (File Position Indicator)

- 다음에 입력받아야 할 위치를 가리키는 역할



##### `fseek` 함수 다루기

```c
/* fseek */
#include <stdio.h>

int main() {
    FILE* fp = fopen("some_data.txt", "r");
    char data[10];
    char c;

    if (fp == NULL) {
        printf("EORROR! \n");
        return 0;
    }

    fgets(data, 5, fp);
    printf("입력받은 데이터 : %s \n", data);

    c = fgetc(fp);
    printf("그 다음에 입력받은 문자 : %c \n", c);

    fseek(fp, -1, SEEK_CUR);

    c = fgetc(fp);
    printf("그렇다면 무슨 문자가? : %c \n", c);

    fclose(fp);
    return 0;
}

/*
입력받은 데이터 : Ther
그 다음에 입력받은 문자 : e
그렇다면 무슨 문자가? : e
*/
```

```c
/* 파일의 마지막 문자 보기 */
#include <stdio.h>

int main() {
    FILE* fp = fopen("some_data.txt", "r");
    char data[10];
    char c;

    if (fp == NULL) {
        printf("EORROR! \n");
        return 0;
    }

    fseek(fp, -1, SEEK_END); // 맨 끝엔 EOF가 있다.

    c = fgetc(fp);
    printf("파일의 마지막 문자 : %c \n", c);

    fclose(fp);
    return 0;
}

// 파일의 마지막 문자 : !
```



##### 파일에 쓰기, 읽기 같이하기

##### `fopen`에서 `"r+", "w+", "a", "a+"` 형태. 쓰기/읽기 전환 시 문제점

- `r+` : 읽기 및 쓰기 형식. 파일이 존재하지 않으면 열지 않음. 있으면 내용 유지.
- `w+` : 읽기 및 쓰기 형식. 파일이 존재하지 않으면 새로 생성. 있으면 내용 삭제.
- `a` : append, 덧붙이기 형식. 파일의 맨 끝부터 내용이 쓰여진다. 
- `a+` : 읽기 및 덧붙이기 형식. 쓰기 작업은 오로지 파일 끝 부분에서부터 쓸 수 있다.
- 쓰기/읽기 전환 시 : `fseek` 또는 `fflush` 함수로 파일 위치 지정자를 다시 설정해야 한다.

```c
/* r+ 인자 사용하기 */
#include <stdio.h>

int main() {
    FILE* fp = fopen("some_data.txt", "r+");
    char data[100];
    
    fgets(data, 100, fp);
    printf("현재 파일에 있는 내용 : %s \n", data);

    fseek(fp, 5, SEEK_SET);

    fputs("is nothing on this file", fp);

    return 0;
}

// Thereis nothing on this file
```

```c
/* append 기능 */
#include <stdio.h>

int main() {
    FILE* fp = fopen("some_data.txt", "a");
    char c;
    
    if (fp == NULL) {
        printf("파일 열기를 실패하였습니다! \n");
        return 0;
    }

    fputs("IS ADDED!", fp);
    fclose(fp);
}
// happy
// happyIS ADDED!
```

```c
/* 쓰기/읽기 변환 시 주의할 점 : 대소문자 변환하기 */
#include <stdio.h>

int main() {
    FILE* fp = fopen("some_data.txt", "r+");
    char c;
    
    if (fp == NULL) {
        printf("파일 열기를 실패하였습니다! \n");
        return 0;
    }

    while ((c = fgetc(fp)) != EOF) {
        if (65 <= c && c <= 90) {
            fseek(fp, -1, SEEK_CUR);
            fputc(c + 32, fp);

            /*
            쓰기-읽기 모드 전환을 위해서는 무조건
            fseek함수와 같은 파일 위치 지정자 설정 함수들을
            호출해야 한다.
            */
            fseek(fp, 0, SEEK_CUR);
        }
        else if (97 <= c && c <= 122) {
            fseek(fp, -1, SEEK_CUR);
            fputc(c - 32, fp);

            /* fseek가 아닌 다른 방법 */
            fflush(fp);
        }
    }

    fclose(fp);
}

// Happy
// hAPPY
```



##### `fprintf` 함수와 `fscanf` 함수

- `fscanf(스트림, 타입, 받아올 변수)` : 지정한 타입에 맞게 데이터를 읽어온다. `fgets`와 달리 `\n`, 띄어쓰기,탭 문자(`\t`) 중 어느 하나가 나올 때까지 읽어들이므로 단어별로 읽을 때 유용하다. 
- `fprintf(스트림, 내용)` : 지정한 스트림에 내용을 출력한다.

```c
/* fscanf */
#include <stdio.h>

int main() {
    FILE* fp = fopen("some_data.txt", "r");
    char data[100];
    
    if (fp == NULL) {
        printf("파일 열기 오류! \n");
        return 0;
    }

    printf("---- 입력 받은 단어들 ---- \n");

    while (fscanf(fp, "%s", data) != EOF) {
        printf("%s \n", data);
    }
    
    fclose(fp);
}
/*
----입력 받은 단어들----
Apple
Banana
Coconut
*/
```

```c
/* fscanf, fprintf */
#include <stdio.h>
#include <string.h>

int main() {
    FILE* fp = fopen("some_data.txt", "r+");
    char data[100];
    
    if (fp == NULL) {
        printf("파일 열기 오류! \n");
        return 0;
    }

    while (fscanf(fp, "%s", data) != EOF) {
        if (strcmp(data, "this") == 0) {
            fseek(fp, -(long)strlen("this"), SEEK_CUR);
            fputs("that", fp);

            fflush(fp);
        }
    }
    fprintf(fp, "끝! \n");

    fclose(fp);
}
/*
this is C
that is C끝!
*/
```



##### 도서 관리 프로그램에 입출력 처리 적용

```c
/* 도서 관리 프로그램 */
#include <stdio.h>
#include <stdlib.h>

typedef struct BOOK {
	char book_name[30];
	char auth_name[30];
	char publ_name[30];
	int borrowed;
} BOOK;

// 추가, 검색, 대여, 반납 함수 1개씩
int register_book(BOOK* book_list, int* nth);
int search_book(BOOK* book_list, int total_num_book);
char compare(char* str1, char* str2);
int return_book(BOOK* book_list);
int borrow_book(BOOK* book_list);
int print_book(BOOK* book_list, int total_num_book);

int main() {
	int user_choice;
	int num_total_book = 0;
	BOOK* book_list;
	printf("도서관의 최대 보관 장서 수를 설정해주세요 : ");
	scanf("%d", &user_choice);

	book_list = (BOOK*)malloc(sizeof(BOOK) * user_choice);
	while (1) {
		printf("도서 관리 프로그램 \n");
		printf("메뉴를 선택해주세요! \n");
		printf("1. 책을 새로 추가하기 \n");
		printf("2. 책을 검색하기 \n");
		printf("3. 책을 대여하기 \n");
		printf("4. 책을 반납하기 \n");
		printf("5. 프로그램 종료 \n");
		printf("6. 책 리스트를 book_list.txt에 출력하기 \n");
		printf("당신의 선택은? \n");

		scanf("%d", &user_choice);

		if (user_choice == 1) {
			register_book(book_list, &num_total_book);
		}
		else if (user_choice == 2) {
			search_book(book_list, num_total_book);
		}
		else if (user_choice == 3) {
			borrow_book(book_list);
		}
		else if (user_choice == 4) {
			return_book(book_list);
		}
		else if (user_choice == 5) {
			break;
		}
		else if (user_choice == 6) {
			print_book(book_list, num_total_book);
		}
	}
	free(book_list);
	return 0;
}

int register_book(BOOK* book_list, int* nth) {
	printf("책의 이름 : ");
	scanf("%s", book_list[*nth].book_name);
	printf("책의 저자 : ");
	scanf("%s", book_list[*nth].auth_name);
	printf("책의 출판사 : ");
	scanf("%s", book_list[*nth].publ_name);
	book_list[*nth].borrowed = 0;
	(*nth)++;
	return 0;
}
int search_book(BOOK* book_list, int total_num_book) {
	int user_input;
	int i;
	char user_search[30];
	printf("어느 것으로 검색할 것인가요? \n");
	printf("1. 책 제목 검색 \n");
	printf("2. 책 저자 검색 \n");
	printf("3. 책 출판사 검색 \n");
	scanf("%d", &user_input);
	printf("검색할 단어를 입력해주세요. \n");
	scanf("%s", user_search);
	printf("검색 결과. \n");

	if (user_input == 1) {
		for (i = 0; i < total_num_book; i++) {
			if (compare(book_list[i].book_name, user_search)) {
				printf("번호 : %d, 책 이름 : %s, 저자 : %s, 출판사 : %s \n",
					i, book_list[i].book_name, book_list[i].auth_name, book_list[i].publ_name
				);
			}
		}
	}
	else if (user_input == 2) {
		for (i = 0; i < total_num_book; i++) {
			if (compare(book_list[i].auth_name, user_search)) {
				printf("번호 : %d, 책 이름 : %s, 저자 : %s, 출판사 : %s \n",
					i, book_list[i].book_name, book_list[i].auth_name, book_list[i].publ_name
				);
			}
		}
	}
	else if (user_input == 3) {
		for (i = 0; i < total_num_book; i++) {
			if (compare(book_list[i].publ_name, user_search)) {
				printf("번호 : %d, 책 이름 : %s, 저자 : %s, 출판사 : %s \n",
					i, book_list[i].book_name, book_list[i].auth_name, book_list[i].publ_name
				);
			}
		}
	}

	return 0;
}
char compare(char* str1, char* str2) {
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
int borrow_book(BOOK* book_list) {
	int book_num;
	printf("빌릴 책의 번호를 입력해주세요 : ");
	scanf("%d", &book_num);

	if (book_list[book_num].borrowed == 1) {
		printf("이미 대출된 책입니다. \n");
	}
	else {
		printf("책이 성공적으로 대출되었습니다. \n");
		book_list[book_num].borrowed = 1;
	}

	return 0;
}
int return_book(BOOK* book_list) {
	int book_num;
	printf("반납할 책의 번호를 입력해주세요 : ");
	scanf("%d", &book_num);

	if (book_list[book_num].borrowed == 0) {
		printf("이미 반납된 책입니다. \n");
	}
	else {
		printf("책이 성공적으로 반납되었습니다. \n");
		book_list[book_num].borrowed = 0;
	}

	return 0;
}
int print_book(BOOK* book_list, int total_num_book) {
	FILE* fp = fopen("book_list.txt", "w");
	int i;

	if (fp == NULL) {
		printf("출력 오류! \n");
		return -1;
	}

	fprintf(fp, "책 이름 / 저자 이름 / 출판사 / 반납 유무 \n");
	for (i = 0; i < total_num_book; i++) {
		fprintf(fp, "%s / %s / %s", book_list[i].book_name, book_list[i].auth_name, book_list[i].publ_name);
		if (book_list[i].borrowed == 0)
			fprintf(fp, "/ NO \n");
		else 
			fprintf(fp, "/ YES \n");
	}
	fclose(fp);
}
```

