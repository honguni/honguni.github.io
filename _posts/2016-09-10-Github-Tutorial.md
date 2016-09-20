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

**git repository를 만드는 방법에는 두 가지가 있다.**

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

  *fatal에러 발생 시*

  - git 은 https 로 연결시 내부적으로 curl 의 라이브러리인 libcurl 을 사용하여 연결하는데 사용하는 동적 라이브러리가 https 를 지원하지 않는 버전이라 발생한다. C:\Windows\SysWOW64\libcurl.dll을 %Git_HOME%\bin\libcurl.dll 으로 덮어쓴다.
