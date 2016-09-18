---
layout: post
title: Git 시작하기
---


 분산 버전 관리 시스템(DVCS)

!클라이언트는 서버의 저장소를 전부 복제!

 - 서버에 문제가 생기더라도 복제물로 다시 작업 가능하다!



git CLI 명령어

사용자 정보

$ git config --global user.name "NAME"

$ git config --global user.email EMAIL@example.com



설정확인

$ git config --list



편집기는 vi 사용



git bash 에서의 붙여넣기는 shift + insert



-----------------------------------------------------------------------------

################ git 의 기본 사용법 ######################

git 저장소를 만드는 방법 두 가지!

 (1) init 

- 프로젝트의 디렉토리에서 아래 명령어 실행

$ git init



(2) clone

$ git clone https://github.com/libgit2/libgit2

// fatal: Protocol https not supported or disabled in libcurl

- git 은 https 로 연결시 내부적으로 curl 의 라이브러리인 libcurl 을 사용하여 연결하는데 사용하는 동적 라이브러리가 https 를 지원하지 않는 버전이라 발생한다. C:\Windows\SysWOW64\libcurl.dll을 %Git_HOME%\bin\libcurl.dll 으로 덮어쓴다.





<저장소 생성 및 관리 기본 사이클!>

저장소 생성 후 파일 작업.

git status 명령으로 상태 확인.

git add <FILE> 명령으로 파일 기록 추적

git commit 으로 커밋! (커밋 메시지 작성)

 -> git commit -a                         옵션을 추가하면 add 명령 없이 모든 저장소 파일을 커밋

 -> git commit -m "커밋메시지"      커밋메시지를 바로 작성

 -> ex) & git commit -am "added file"

//하지만 기본적으로는 브랜치를 생성하여 추가, 수정, 커밋하며 프로젝트 진행한다는 것



<브랜치와 체크아웃>

$ git branch                     //현재 브랜치 확인

$ git branch <NAME>        //NAME이름의 브랜치 생성

$ git checkout <NAME>     //NAME 브랜치로 작업공간 이동

 ( 별 표시(*) 로 현재 작업 중인 브랜치 표시 )

  -> $ git checkout -b <NAME>   //브랜치를 만들면서 동시에 체크아웃



<브랜치 병합>

다른 브랜치로 체크아웃 후

 $ git merge <브랜치이름>





<추가 기능들>

 - .gitignore : 불필요한 파일 및 폴더 무시

 .gitignore 파일 생성     //$ touch .gitignore

 https://www.gitignore.io 에서 운영체제, 프로그래밍 언어 이름 등을 입력 후 생성

   # 기본적인 규칙들 http://igotit.tistory.com/932 참고



<충돌 해결>

merge 충돌 시 다음과 같은 상황 발생



충돌이 발생한 시작 부분 ( <<<<<<<<< HEAD), 경계(========), 끝 부분 ( >>>>>>>>>> hotfix )

 //일반적인 해결은 직접 파일 수정



git diff [브랜치이름]        // 브랜치 사이에 차이점 알아보는 명령



<기록 보기>

$ git log --stat           //각 커밋에서 수정된 파일의 통계 정보를 보여줌

$ git log --graph        //브랜치 분기와 병합 내역을 아스키 그래프로 보여줌



<원격저장소를 로컬저장소에 복사>

$ git clone [원격저장소url]



<로컬저장소와 원격저장소 간의 연결>

$ git remote add [저장소별칭] [원격저장소url]

$ git remote -v                     //연결확인



<로컬 작업 내역을 원격 저장소에 올리기>

$ git push origin --all

// origin (원격저장소별칭) --all (모든 브랜치를 푸시 | 같은 이름의 브랜치가 존재하고 내역이 다르면 푸시 거부, 예를 들어 README.md)



<pull과 fetch>

 - pull 명령은 원격 저장소의 정보를 가져오면서 자동으로 병합 수행! (변경사항을 세세하게 파악하기 어렵다.)

 - fetch를 이용해서 원격 저장소의 커밋을 가져오고, 확인 후 수동으로 병합하는 것을 추천

일반적인 실행 단계



// 원격 저장소 master브랜치의 파일 수정

(1) fetch

$ git fetch

$ git status

$ git merge origin/master

//충돌 확인 후 수정



(2) pull

$ git pull origin master



