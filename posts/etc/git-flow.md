# [etc] Git Flow

#### Git Flow란?

git을 통해 협업을 할 때 사용하는 방법 중 하나.

브랜치를 feature - develop - release - hotfix - master 의 5단계로 나누어 코드를 관리하는 브랜칭 기법.

![](https://miro.medium.com/max/741/0*UBDl71VkK3hyoJ9z.png)

### 브랜치의 종류

#### Master

실제 클라이언트에서 이용하는 최종 형태의 메인 브랜치. 프로젝트에 하나만 존재한다.

#### Develop

현재 개발이 진행중인 브랜치. master 브랜치와 동일하게 프로젝트 당 하나만 존재한다.

#### Feature

새로운 기능을 추가하기 위한 브랜치. feature로 기능 개발이 완료되면 develop브랜치로 병합한다.

#### Release

 실제 프로젝트를 배포하기 위한 브랜치. develop브랜치로부터 개발한 기능들을 받아오고, 버그들을 수정하며 배포 준비가 완료되면 master 브랜치에 병합한다.

#### Hotfix

Master 브랜치에서 예상하지 못한 오류가 생길 경우 이를 수정하기 위한 브랜치. master로부터 파생되며, 수정한 버그들을 적용하기 위해 상황에 따라 master, develop, release 브랜치에 병합된다.



## Refer

[Git에 대해 알아보자 1. Git의 개념과 Git Flow](<https://cupjoo.tistory.com/6>)

[Git flow 사용해보기](<https://boxfoxs.tistory.com/347>)