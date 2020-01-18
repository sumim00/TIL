# [etc] Linux 명령어

- pwd : print working directory, 현재 위치의 경로를 보여준다.

- clear :  터미널창의 내용을 지운다.

- exit : 터미널창 종료

- ls : 현재 어떤 디렉토리나 파일이 있는지 확인하는 명령어

| 옵션 | 설명                                                         |
| ---- | ------------------------------------------------------------ |
| -a   | 숨김 파일과 디렉터리도 함께 표시                             |
| -l   | 파일이나 디렉터리의 상세 정보를 함께 표시  참고로 항목 맨 앞이 `-`로 시작한다면 파일, `d` 로 시작한다면 폴더 |
| -r   | 파일의 정렬 순서를 거꾸로 표시                               |
| -t   | 파일 작성 시간 순으로 (내림차순) 표시                        |

- cd : 디렉토리 이동

| 옵션 | 설명                                |
| ---- | ----------------------------------- |
| ~    | 현재 접속 중인 사용자의 홈 디렉터리 |
| ./   | 현재 사용자가 작업중인 디렉터리     |
| ../  | 현재 디렉터리의 상위 디렉터리       |

- mkdir : 디렉터리 생성 -p : 디렉터리1/디렉터리2/디렉터리3 디렉터리 여러개 한 번에 생성
- rmdir : 디렉터리 삭제. but 비어있어야 함.

- rm : 디렉터리 삭제

| 옵션 | 설명                         |
| ---- | ---------------------------- |
| -r   | 하위 디렉터리까지 삭제       |
| -f   | 삭제여부 묻지 않고 바로 삭제 |

- cat : concatenate, 텍스트 문서의 내용 확인

| 옵션                                 | 설명                                         |
| ------------------------------------ | -------------------------------------------- |
| $ cat 파일                           | 파일의 내용을 화면에 표시                    |
| $ cat 파일1, 파일2...파일n > 새 파일 | 파일n개를 차례로 연결해서 새로운 파일을 생성 |
| $ cat 파일1 >> 파일2                 | 파일1의 내용을 파일2 끝에 연결               |

- head, tail : 텍스트로 작성된 파일의 앞 10행 또는 마지막 10행만 출력
- more : 텍스트로 작성된 파일을 화면에 페이지 단위로 출력
- less : more와 용도가 비슷하지만 기능이 더 확장된 명령 
- vim : 빔을 사용해 텍스트 작성
- file : 어떤 종류의 파일인지를 표시 `# file myfolder/`

| 명령           | 설명                                                         |
| -------------- | ------------------------------------------------------------ |
| `i` 키         | insert. 입력모드로 바뀌어 텍스트를 입력할 수 있다.           |
| `esc` 키       | ex모드로 바뀌어 문서를 저장, 종료할 수 있다.                 |
| :w 또는 :write | 편집 중이던 문서를 저장한다.                                 |
| :q 또는 :quit  | 편집기를 종료한다.                                           |
| :wq            | 편집 중이던 문서를 저장하고 종료한다.                        |
| :q!            | 문서를 저장하지 않고 편집기를 종료한다. 확장자가 .swp인 임시 파일 생성 |



- cp : 파일이나 디렉터리를 복사 `#cp abc.txt cba.txt`
  - -r : 디렉터리를 복사하는 경우 디렉터리 전체가 복사

- touch : 크기가 0인 새 파일을 생성. 이미 있는 경우 수정 시간 변경 `# touch abc.txt`
- mv : 파일과 디렉터리의 이름을 변경하거나 위치 이동 `# mv abc.txt www.txt`





```bash
limjiyoung@DESKTOP-BQ5IHHR:~/vimTest$ touch file1
limjiyoung@DESKTOP-BQ5IHHR:~/vimTest$ ls -l
total 0
-rw-rw-rw- 1 limjiyoung limjiyoung  0 Jan 16 23:55 file1
-rw-rw-rw- 1 limjiyoung limjiyoung 43 Jan 16 23:48 test.txt
```





file Type

| 문자 | 파일 종류                        |
| ---- | -------------------------------- |
| -    | 일반 파일                        |
| d    | 디렉터리 파일                    |
| b    | 블록 디바이스 파일               |
| c    | 문자 디바이스 파일               |
| l    | 심볼릭 링크 (다른 파일을 가리킴) |



ln -s 심볼릭 링크 만들기 `ln -s <TARGET> <LINK_NAME> `

```bash
lrwxrwxrwx 1 limjiyoung limjiyoung     9 Jan 17 12:12 LINK_NAME -> TARGET
```



chmod -h 

심볼릭 링크 파일의 소유자를 바꾸려면 -h를 추가하면 되는데 MacOS만 가능.



grep : 텍스트 파일에서 특정 패턴(문자열)을 가진 줄을 찾아서 출력

`$ grep [option] pattern file(s)`





##### head

문서 내용의 앞부분 출력 (기본 10줄)

자주 사용되는 옵션

- -c, --bytes=[ - ]NUM
- -n, --lines=[ - ]NUM
- NUM
  - -byte입력 시 K, M, G, T 입력 가능 (예: 10M)
  - '-' 입력 시 문서의 마지막 NUM bype/line 을 제외하고 출력

사용 예제

- head /etc/passwd
- head -n 1 /etc/passwd
- cat /etc/passwd | head -n -5



##### tail

문서 내용의 뒷부분 출력 (기본 10줄)

자주 사용되는 옵션

- -c, --bytes=[ + ]NUM
- -n, --lines=[ + ]NUM
- -f, --follow=[ ={name|descr} ] : 추가되는 내용 대기. 추가되는 내용은 append하여 출력
- -F
- NUM
  - -byte입력 시 K, M, G, T 입력 가능 (예: 10M)
  - '+' 입력 시 문서의 마지막 NUM bype/line 지점에서 출력

사용 예제

- tail /etc/passwd -n 1
- taill /etc/passwd -n +5
- cat /etc/passwd | tail -n 15
- cat /etc/passwd | tail -n +15

 

echo haha > aa

echo hihi >> aa



##### wc

word count, line/word/byte count 출력

자주 사용되는 옵션

- -l : 라인 수만 출력

사용 예제

- wc FILENAME FILENAME2 // 여러개 한 번에 보기 + 합계도 출력
- wc -l FILENAME
- cat FILENAME | wc -l  //stdin으로부터 라인수만 획득
- wc -l FILENAME | cut -d ' ' -f 1
- wc -l FILENAME | awk '{ print $1 }'  // 라인수만 획득
- wc *.c   // 여러 파일 입력 시 합계 출력



##### nl

line number, 파일 내용을 라인넘버와 함께 출력

자주 사용되는 옵션

- -ba : 모든 라인에 대해 라인 넘버링
- -v N : 시작 라인 넘버를 N으로 지정
- -s : 라인 넘버 출력 후 출력할 separaror 지정

사용 예제

- cat FILENAME
- nl FILENAME
- nl -ba FILENAME
- nl -ba -s ":     " FILENAME
- nl -ba -s ":     " FILENAME | tail



##### sort

정렬하여 출력

자주 사용되는 옵션

- 위치 지정
  - -k, --key=KEYDEF : key에 의한 정렬 수행
  - -t, --field-seperator : 필드 구분자
- 정렬 기준
  - -f, 대소문자 구분 없음
  - -g,
  - -n, 90>123
  - -r, 내림차순
  - -u, 내용이 아예 같을 경우 한줄만 출력

사용 예제

- sort -t: -k 5,5 -k 1,1 --debug (:기준으로 정렬. 첫 번째 비교는 5컬럼 두 번째 비교는 1컬럼)
- ls -al | sort -k 5 (리스트를 5컬럼 기준으로 정렬)





##### uniq

중복된 내용을 제거하고 출력 (단, 연속되어 있는 경우!)

자주 사용되는 옵션

- -d, --repeated : 중복된 내용만 출력
- -u, --unique : 중복되지 않은 내용만 출력
- -i, --ignore-case : 대소문자 무시

사용 예제

- nl uniq_sample
- uniq uniq_sample | nl
- sort uniq_sample  | uniq | nl
- sort uniq_sample  | uniq -i | nl
- sort uniq_sample  | uniq -d | nl
- sort uniq_sample  | uniq-u | nl
- grep "shm_open" *.c | awk -F: '{ print $1 }' | uniq



##### cut

컬럼 잘라내기

자주 사용되는 옵션

- -b, --bytes=LIST		:byte 선택
- -c, --characters=LIST:character 선택
- -f, --fields=LIST :필드(컬럼) 선택
- -d, --delimiter=DELIM : tab 대신 사용할 구분자 지정
- --complement : 선택 반전
- --output-delimiter=STRING : 출력시 사용할 구분자 지정



사용 예제

- wc /etc/passwd -l | cut -d ' ' -f 1
- head /etc/passwd | cut -d ':' -f 1,7
- head /etc/passwd | cut -d ':' -f 1,7 --output-delimiter=": "
- ls -al | cut -b -10 (마지막 -10은 1-10의 축약.)
- ls -al | cut -b -10 --complement
- ls -al | head | cut -b -10



##### tr

어떤 내용을 변환(translate)한다.

tr [OPTION] ... SET1 [SET2]

자주 사용되는 옵션

- -c, -C, --complement
- -d, --delete
- SET
  - CHAR-CHAR2  : CHAR1부터 CHAR2까지 (예: 'a-z')	
  - [:alnum:]  : 문자+숫자
  - [:alpha:]  : 문자
  - [:blank:]  : 공백
  - [:space:]  : 공백 + newline
  - [:degit:] / [:xdigit:]  : 10진수 숫자 / 16진수 숫자
  - [:lower:] / [:upper:]  : 소문자 / 대문자

사용 예제

- head FILE | tr [:lower:] [:upper:]
- head FILE tr -d '0'



##### sed

stream editor 출력된 내용을 조작해서 화면에 보여줌.

자주 사용되는 옵션

- {RANGE}p : range 내의 라인 출력
- {RANGE}d  : range 내의 라인 삭제
- /SEARCHPATTERN/p  : SEARCHPATTERN과 매치되는 라인 출력
- /SEARCHPATTERN/d  : SEARCHPATTERN과 매치되는 라인 삭제
- s/REGEX/REPLACE/  : REGEX에 매치되는 부분을 REPLACE로 교체

사용 예제

- head FILE | sed -n '1, 3p' // -n은 기본 출력을 없앰
- head FILE | sed '1, 3d'
- head FILE | sed -n '/nologin/p'
- head FILE | sed 's/demon/DEMON/'
- head FILE | sed 's/demon/DEMON/g' // g 안쓰면 한 컬럼 당 1개만 바뀜
- head FILE | sed '3,5 s/:/^/g'
- head FILE | sed -n '/games/,+2p' // 결과 라인으로부터 2줄 더 출력



##### awk

텍스트 처리 script language

synax : awk options 'selection _criteria {action}' input-file

자주 사용되는 옵션

- -F  : field seperator 지정 (기본은 공백)

주요 내장 변수

- $1, $2, $3...$N  : Nth field
- NR  : number of records
- NF  : number of fields
- FS  : field separator(default 'white space')
- RS : redord separator(default 'new line')
- OFS  : Output field separator
- ORS  : Output record separator

사용 예제

- head FILE | awk '{print $1}'
- head FILE | awk -F: '/j/ {print $1}'
- head aa | awk -F: '/aa/ {print NR "===>" $1, NF}'



##### find

조건에 맞는 파일을 찾아 명령을 수행한다.

기본 사용방법: find [OPTIONS] path EXPR

자주 사용되는 옵션

- 조건
  - -name : 이름으로 검색
  - -regex : regex에 매치로 검색
  - -empty : 빈 디렉터리 혹은 빈 검색
  - -size : 사이즈로 검색
    - -N : 이하
    - -N : 이상
  - -type : 파일 타입으로 검색
    - d : 디렉터리
    - p : named pope
    - f : regular file
    - s : socket
  - -perm : 퍼미션으로 검색
    - mode : 정확히 일치하는 파일
    - +mode : 모든 flag가 포함된 파일
    - /mode : 어떤 flag라도 포함된 파일
- 액션
  - -delete : 파일 삭제
  - -ls : ls -dils 명령 수행
  - -print : 파일 이름 출력
  - -printf : 파일 이름을 포맷에 맞게 출력
  - -exec : 주어진 명령 수행
  - -execdir : 해당 디렉터리로 이동하여 명령 실행
  - -ok : 사용자에게 확인 후 exec
  - -okdir : 사용자에게 확인 후 execdir

사용 예제

- find .
- find `pwd` -name "*.txt" // 절대경로로 .txt 출력
- find `pwd` -regextype egrep -regex '.*kl.*.txt$' // 중간에 kl이 있고 .txt로 끝나는 파일
- find . -perm 0777 | wc -l // 퍼미션이 777인 파일 개수 출력
- find . -perm /u+x -ls
- find . -name "*.txt" -exec stat {} \; // exec, ok는 `\;`로 마무리
- find . -name "*.txt" -ok rm -f {} \;



##### grep

파일 내용 중 원하는 내용을 찾는다.

grep [OPTIONS] PATTERN [FILE...]

자주 사용되는 옵션

- -r : recursive (하위 디렉터리도 검색)
- -i : ignore case
- -v : invert match (매치가 안되는 경우를 알려줌)
- -q : quiet mode 

사용 예제

- grep fork *.c
- grep j *.txt | awk -F: '{ print $1 }' | sort -u // j가 포함된 txt파일 리스트를 출력하되, 앞부분 (파일명)만 유니크하게 정렬하여 출력
- grep j *.txt -q // 하고 `echo $?`를 쳤을 때, 성공적으로 찾으면 0 아니면 1 반환
-  grep "\<for\>" *.txt // `\< 내용 \>` 하면 단어 단위로 검색 가능
- grep "^$" *.txt // `^`는 입력한 단어로 시작하는 것만, `$` 는 입력한 단어로 끝나는 것만 출력. `^$`를 쓰면 안에 내용이 없는 파일 반환.
- grep "^static.*(void)$" *.c // static으로 시작하고 void로 끝나는 파일 반환.



##### aprppos

man page 이름과 설명을 검색한다.

자주 사용되는 옵션

- -s, --sections=LIST, --section=LIST : 탐색할 섹션을 colon으로 구분하여 입력

사용 예제

- apropos pthread
- apropos pthread -s 7
- apropos '.*'



##### locate 

설명

- 파일의 위치를 찾아 보여준다.
- 단, updatedb가 저장해놓은 DB파일 내에서 검색하므로 누락 파일이 생길 수 있음.
- locate [OPTION]...PATTERN...

자주 사용되는 옵션

- -i , --ignore-case대소문자 구분없이 검색
- -l, --limit, -n LIMIT : 출력 결과를 LIMIT만큼 출력
- --regex : PATTERN을 REGEX로 해석

사용 예제

- locate main.c
- locate --regex "\/main.c$" -n 3 :// 맨 끝이 `/main.c`인 파일의 위치를 3개만 출력



##### which

실행 파일의 위치를 보여준다.

사용 예제

- which ls // ls툴의 위치
- which chmod
- which ls strace chmod