---
layout: post
title: Git 시작하기
---

### 분산 버전 관리 시스템 (DVCS)

- 클라이언트가 서버의 저장소를 전부 복제

- 서버에 문제가 생기더라도 복제물로 작업 진행 가능

  #### 사용자 정보 설정 및 확인

  ```
  $ git config --global user.name "NAME"
  $ git config --global user.email EMAIL@example.com
  $ git config --list
  ```

**git 저장소 만들기**

(1) init

  - 프로젝트 디렉토리에서 아래 명령어를 실행

  ```
  $ git init
  ```

(2) clone

  - 다른 저장소를 복제
  ```
  $ git clone [RepositoryURL]
  ```

    *fatal에러 발생 시*  - git 은 https 로 연결시 내부적으로 curl 의 라이브러리인 libcurl 을 사용하여 연결하는데 사용하는 동적 라이브러리가 https 를 지원하지 않는 버전이라 발생한다. C:\Windows\SysWOW64\libcurl.dll을 %Git_HOME%\bin\libcurl.dll 으로 덮어쓴다.

**저장소 생성 및 관리 기본 사이클**

파일작업 -> 상태확인 -> 기록추적 -> 커밋(커밋메시지작성)

  ```
  $ git status
  $ git add [FILE]
  $ git commit
  ```

**브랜치와 체크아웃**

  ```
  $ git branch			//현재 브랜치 확인
  $ git branch [NAME]		//[NAME]이름의 브랜치 생성
  $ git checkout [NAME]		//[NAME]브랜치로 작업공간 이동
  $ git merge [NAME]		//현재 브랜치와 [NAME]브랜치 병합
  ```

### 원격저장소

**로컬저장소와 원격저장소 간의 연결**

```
$ git remote add [저장소별칭] [원격저장소URL]
$ git remote -v						//연결확인
```

**로컬 작업내역을 원격저장소에 올리기**

```
$ git push origin --all
```

**PULL과 FETCH**

  - pull 명령은 원격 저장소의 정보를 가져오면서 자동으로 병합 수행! (변경사항을 세세하게 파악하기 어렵다.)

  - fetch를 이용해서 원격 저장소의 커밋을 가져오고, 확인 후 수동으로 병합하는 것을 추천

(1) FETCH

```
$ git fetch

$ git status

$ git merge origin/master
```

(2) PULL

```
$ git pull origin master
```
