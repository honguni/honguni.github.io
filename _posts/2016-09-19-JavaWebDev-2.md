---
layout: post
title: JavaWebDev - HTTP
---

  웹 브라우저와 웹 서버 사이에 데이터를 주고 받는 규칙을 정의한 것이다.

**프록시서버** : 클라이언트와 서버 사이에서 통신을 중계해 주는 컴퓨터나 프로그램

  - Charles, Fiddler, WireShark 등

#### [HTTP 응답 상태코드](https://ko.wikipedia.org/wiki/HTTP_%EC%83%81%ED%83%9C_%EC%BD%94%EB%93%9C){:target="_blank"}

- 400 : 잘못된 요청

- 403 : 서버가 요청 거부

- 404 : 요청한 자원을 찾을 수 없음

- 500 : 내부 서버 오류

---

**GET 요청** - 데이터를 URI에 붙여 서버에 보낸다.
- 데이터 조회에 적합(보안성 저하)
- 대용량 데이터 전송 불가

GET 요청이 발생하는 경우
1. 주소창에 URL 입력
2. 링크를 클릭
3. 입력폼의 method속성을 GET으로 지정

  **POST 요청** - HTTP 메시지 본문에 데이터 포함

#### 파일 업로드 시 Content-Type 헤더

Content-Type: multipart/form-data

바이너리 데이터에 '&'문자에 해당하는 코드 값이 매개변수 값을 분리할 때 문제 발생
Content-Type 헤더의 임의의 boundary 값이 매개변수 값을 분리할 때 사용할 구분자를 정한다.
