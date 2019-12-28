# [etc] Git

#### Git의 기능

1. 버전 관리 - 문서를 수정할 때마다 언제 어떤 것을 변경했는지 기록한다.
2. 백업하기 - GitHub와 같은 원격 저장소를 이용하여 자료를 백업한다.
3. 협업하기 - 협업 과정에서 일어나는 문제들을 중간에 정리한다.



#### Git 환경 설정

깃을 사용하기 전에 먼저 사용자 정보를 입력한다. 이를 통해 어떤 버전을 누가 만들었는지 파악할 수 있다.

```bash
$ git config --global user.name "Jiyoung"
$ git config --global user.email "jiyoung@gmail.com"
```



#### 리눅스 명령어

``` bash
$ cd ~				// 홈 디렉토리로 이동
$ cd ..				// 상위 디렉토리로 이동
$ mkdir mine		// 새 디렉토리 mine 생성
$ pwd				// 현재 디렉토리 표시
$ ls -l				// 디렉토리의 폴더 상세 정보 표시
$ ls -a				// 디렉토리 내 숨김 파일과 숨김 디렉토리 표시
$ rm -r mine		// mine 디렉토리와 하위 디렉토리와 파일 삭제 
$ vim test.txt		// 빔을 이용하여 test.txt 파일 작성
$ cat test.txt		// test.txt의 내용을 터미널 창에 표시
$ clear				// 터미널 창 내용 지우기
$ exit				// 터미널 창 종료
```





#### Reference

이고잉·고경희, 『지옥에서 온 문서 관리자 깃&깃허브 입문』,  이지스퍼블리싱, 2019