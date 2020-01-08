# 씹어먹는 C언어 필기 (15강)

> Psi님의 [씹어먹는 C언어](<https://modoocode.com/231>) 강좌를 수강하며 기록한 노트입니다.



### 15-1. 일로와봐, 문자열(string)

##### 널 종료 문자열

- 자동으로 문자열의 종료 시점을 알리는 종료 문자가 Null이다.

```c
/* 널 뽀개기 */
#include <stdio.h>
int main() {
	char null_1 = '\0';
	char null_2 = 0;
	char null_3 = (char)NULL;

	char not_null = '0';

	printf("NULL의 정수(아스키)값 : %d, %d, %d \n", null_1, null_2, null_3);
	printf("'0'의 정수(아스키)값 : %d \n", not_null);

	return 0;
}
```



##### 문자열 활용

- `%c`가 한 문자만을 출력했다면, `%s`는 종료 문자가 나올 때까지 문자열을 출력한다.
- `" "`는 문자열(1개 이상의 문자)를 지정할 때 사용하고, `' '`는 한 개의 문자를 지정할 때 사용한다.

```c
/* 문자열의 시작 */
#include <stdio.h>
int main() {
	char sentence_1[4] = { 'P', 's', 'i', '\0' };
	char sentence_2[4] = { 'P', 's', 'i', 0 };
	char sentence_3[4] = { 'P', 's', 'i', (char)NULL };
	char sentence_4[4] = { "Psi" }; // 자동으로 sentence_4[4]에 널이 들어간다. 

	printf("sentence_1 : %s \n", sentence_1); // %s 를 통해 문자열을 출력
	printf("sentence_2 : %s \n", sentence_2);
	printf("sentence_3 : %s \n", sentence_3);
	printf("sentence_4 : %s \n", sentence_4);

	return 0;
}
```

```c
/* 포인터 간단 복습 */
#include <stdio.h>
int main() {
	char word[30] = { "long sentence" };
	char *str = word;

	printf("%s \n", str);

	return 0;
}
```

```c
/* 문자열 바꾸기 */
#include <stdio.h>
int main() {
	char word[] = { "long sentence" };
	printf("조작 이전 : %s \n", word);

	word[0] = 'a';
	word[1] = 'b';
	word[2] = 'c';
	word[3] = 'd';

	printf("조작 이후 : %s \n", word);

	return 0;
}
```

```c
/* 문자열 개수 세기 */
#include <stdio.h>

int str_length(char* str);
int main() {
	char str[] = {"What is your name?"};

	printf("이 문자열의 길이 : %d", str_length(str));

	return 0;
}
int str_length(char *str) {
	int i = 0;
	while (str[i]) {
		i++;
	}
	return i;
}
```



##### 문자열 입력

```c
/* 문자열 입력 받기 */
#include <stdio.h>

int main() {
	char words[30];
	printf("30자 이내의 문자열을 입력해주세요! : \n");
	scanf("%s", words);

	printf("문자열 : %s \n", words);

	return 0;
}
```



### 15-2. 일로와봐, 문자열(string) - 버퍼에 관한 이해

##### 버퍼(stdin)에 대한 이해

- `scanf` 함수는 `stdin`으로무터 의미가 있는 문자가 나올 때까지 모든 공백 문자들을 무시한다.
- `%c` 는 `stdin`에 남아 있는 한 개의 문자를 가져온다.
- `%d` 또는 `%s` 는 공백문자 (` ' '`, `'\n'`, `\t`) 등을 무시하고 실질적인 문자 이후의 값을 인식한다.



##### 고질적인 `scanf` 문제에 대한 해결 및 이해

- `getchar();`함수를 이용하여 버퍼 내 `\n` 같은 데이터를 비울 수 있다.
- 결론 : 되도록 문자 대신 문자열을 입력받도록 하자.

```c
/* getchar 함수를 이용한 버퍼 비우기 */
#include <stdio.h>
int main() {
    int num;
    char c;

    printf("숫자를 입력하세요 : ");
    scanf("%d", &num);

    getchar(); // stdin에서 한 문자를 읽어 그 값을 리턴한다.

    printf("문자를 입력하세요 : ");
    scanf("%c", &c);
    return 0;
}
```



### 15-3. 일로와봐, 문자열(string) - 문자열 지지고 볶기 & 리터럴

##### 문자열 리터럴(literal)에 대한 이해

- 리터럴 : 소스 코드 상에서 고정된 값을 가지는 것, C언어의 경우 큰 따옴표(`" "`)로 묶인 것들을 문자열 리터럴이라고 부른다.
- 리터럴이 보관되는 곳은 오직 읽기만 가능하며, 변경할 수 없다.

```c
/* 문자열 */
#include <stdio.h>
int main() {
    char str[] = "hello";
    char *pstr = "goodbye"; // 리터럴 "goodbye"의 시작 주소값을 가져와서 pstr에 대입.

    str[1] = 'a';
    pstr[1] = 'a'; // error

    return 0;
}
```



##### 문자열 다루기 (복사, 합치기, 비교하기)

##### 문자열을 복사하는 함수

```c
/* copy_str 사용 예제 */
#include <stdio.h>
int copy_str(char *src, char *dest);
int main() {
  char str1[] = "hello";
  char str2[] = "hi";

  printf("복사 이전 : %s \n", str1);

  copy_str(str1, str2);

  printf("복사 이후 : %s \n", str1);

  return 0;
}
int copy_str(char *dest, char *src) {
  while (*src) {
    *dest = *src;
    src++; // 포인터 + 1 은 배열의 다음 원소를 가리킨다.
    dest++;
  }

  *dest = '\0';

  return 1;
}
```



##### 문자열을 더하는 함수

```c
/* stradd 사용 예제 */
#include <stdio.h>
int stradd(char *src, char *dest);
int main() {
  char str1[100] = "hello my name is ";
  char str2[] = "Psi";

  printf("합치기 이전 : %s \n", str1);

  stradd(str1, str2);

  printf("합친 이후 : %s \n", str1);

  return 0;
}
int stradd(char *dest, char *src) {
    while (*dest) {
        dest++;
    }
    while (*src) {
        *dest = *src;
        dest++;
        src++;
    }
    *dest = '\0';

  return 1;
}
```



##### 비교하는 함수

```c
/* 비교함수 사용 예제 */
#include <stdio.h>
int compare(char* str1, char* str2);
int main() {
    char str[20] = "hello every1";
    char str2[20] = "hello everyone";
    char str3[20] = "hello every1 hi";
    char str4[20] = "hello every1";

    if (compare(str, str2)) {
        printf("%s 와 %s 는 같다 \n", str, str2);
    }
    else {
        printf("%s 와 %s 는 다르다 \n", str, str2);
    }

    if (compare(str, str3)) {
        printf("%s 와 %s 는 같다 \n", str, str3);
    }
    else {
        printf("%s 와 %s 는 다르다 \n", str, str3);
    }

    if (compare(str, str4)) {
        printf("%s 와 %s 는 같다 \n", str, str4);
    }
    else {
        printf("%s 와 %s 는 다르다 \n", str, str4);
    }

    return 0;
}
int compare(char *str1, char *str2) {
    while (*str1) {
        if (*str1 != *str2) {
            return 0;
        }
        str1++;
        str2++;
    }
    if (*str2 == '\0') return 1; //str2도 str1과 함께 끝났다면 참

  return 0;
}
```



### 15-4. 일로와봐, 문자열(string) - 도서 관리 프로젝트

- 책을 추가하고, 검색하고, 빌리고, 반납하는 기능을 가진 프로그램 만들기

```c
/* 도서 관리 프로그램 */
#include <stdio.h>
int add_book(char(*book_name)[30], char(*auth_name)[30], char(*publ_name)[30],
    int* borrowed, int* num_total_book);
int search_book(char(*book_name)[30], char(*auth_name)[30], char(*publ_name)[30], int* num_total_book);
int compare(char* str1, char* str2);
int borrow_book(int* borrowed);
int return_book(int* borrowed);

int main() {
    int user_choice;        // 유저가 선택한 메뉴
    int num_total_book = 0; // 현재 책의 수

    // 각각  책, 저자, 출판사를 저장할 배열 생성. 책의 최대 개수는 100권
    char book_name[100][30], auth_name[100][30], publ_name[100][30];
    // 빌렸는지 상태 표시.
    int borrowed[100];

    while (1) {
        printf("도서 관리 프로그램 \n");
        printf("메뉴를 선택해주세요. \n");
        printf("1. 책을 새로 추가하기 \n");
        printf("2. 책을 검색하기 \n");
        printf("3. 책을 빌리기 \n");
        printf("4. 책을 반납하기 \n");
        printf("5. 프로그램 종료하기 \n");

        printf("당신의 선택은? : \n");
        scanf("%d", &user_choice);

        if (user_choice == 1) {
            add_book(book_name, auth_name, publ_name, borrowed, &num_total_book);
        }
        else if (user_choice == 2) {
            search_book(book_name, auth_name, publ_name, &num_total_book);
        }
        else if (user_choice == 3) {
            borrow_book(borrowed);
        }
        else if (user_choice == 4) {
            return_book(borrowed);
        }
        else if (user_choice == 5) {
            break;
        }
    }

    return 0;
}
// 책을 추가하는 함수
int add_book(char(*book_name)[30], char(*auth_name)[30], char (*publ_name)[30],
            int *borrowed, int *num_total_book) {

    printf("추가할 책의 제목 : \n");
    scanf("%s", book_name[*num_total_book]);
    
    printf("추가할 책의 저자 : \n");
    scanf("%s", auth_name[*num_total_book]);

    printf("추가할 책의 출판사 : \n");
    scanf("%s", publ_name[*num_total_book]);

    borrowed[*num_total_book] = 0;
    printf("추가 완료! \n");

    (*num_total_book)++;

    return 0;
}
// 책을 검색하는 함수
int search_book(char(*book_name)[30], char(*auth_name)[30], char(*publ_name)[30], int* num_total_book) {
    int user_input;
    int i;
    char user_search[30];

    printf("어느 것으로 검색 할 것인가요? \n");
    printf("1. 책 제목 검색 \n");
    printf("2. 지은이 검색 \n");
    printf("3. 출판사 검색 \n");
    scanf("%d", &user_input);

    printf("검색할 단어를 입력해주세요 : ");
    scanf("%s", user_search);

    if (user_input == 1) {
        for (i = 0; i < num_total_book; i++) {
            if (compare(book_name[i], user_search)) {
                printf("번호 : %d, 책 이름 : %s, 지은이 : %s, 출판사 : %s",
                    i, book_name[i], auth_name[i], publ_name[i]);
            }
        }
    }
    else if (user_input == 2) {
        for (i = 0; i < num_total_book; i++) {
            if (compare(auth_name[i], user_search)) {
                printf("번호 : %d, 책 이름 : %s, 지은이 : %s, 출판사 : %s",
                    i, book_name[i], auth_name[i], publ_name[i]);
            }
        }
    }
    else if (user_input == 3) {
        for (i = 0; i < num_total_book; i++) {
            if (compare(publ_name[i], user_search)) {
                printf("번호 : %d, 책 이름 : %s, 지은이 : %s, 출판사 : %s",
                    i, book_name[i], auth_name[i], publ_name[i]);
            }
        }
    }
    return 0;
}
int compare(char *str1, char *str2) {
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
// 책을 빌리는 함수
int borrow_book(int *borrowed) {
    int book_num;

    printf("빌릴 책의 번호를 말해주세요 \n");
    printf("책 번호 :");
    scanf("%d", &book_num);

    if (borrowed[book_num] == 1) {
        printf("이미 대출된 책입니다! \n");
    }
    else {
        printf("책이 성공적으로 대출되었습니다! \n");
        borrowed[book_num] = 1;
    }

    return 0;
}
// 책을 반납하는 함수
int return_book(int* borrowed) {
    int book_num;

    printf("반납할 책의 번호를 말해주세요 \n");
    printf("책 번호 :");
    scanf("%d", &book_num);

    if (borrowed[book_num] == 0) {
        printf("이미 반납되어 있는 책입니다! \n");
    }
    else {
        printf("책이 성공적으로 반납되었습니다! \n");
        borrowed[book_num] = 0;
    }

    return 0;
}
```

