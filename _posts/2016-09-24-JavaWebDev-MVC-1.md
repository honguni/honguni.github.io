---
layout: post
title: JavaWebDev - MVC - JSP
---

### [MVC 아키텍처](https://ko.wikipedia.org/wiki/%EB%AA%A8%EB%8D%B8-%EB%B7%B0-%EC%BB%A8%ED%8A%B8%EB%A1%A4%EB%9F%AC){:target="_blank"}

  - Controller : 요청에 대해 실제 업무를 수행하는 모델 컴포넌트 호출

  - Model : 데이터 저장소와 연동하여 사용자가 입력한 데이터나 출력할 데이터를 다룸

  - View : 모델이 처리한 데이터나 작업 결과를 가지고 출력할 화면을 구성

---

### JSP

  **지시자** - <%@ ~~ %>

    - page 지시자

      - JSP 페이지와 관련된 속성 정의
      ```jsp
      <%@page
            language="java"
            contentType="text/html; charset=UTF-8"
            pageEncoding="UTF-8"%>
      ```

  **스크립틀릿** - <% ~~ %> 사이의 코드

    - 자바코드로 그대로 복사

  **선언부** - <%! ~~ %>

    - 클래스 선언부로 그대로 복사  

  **표현식** - <%= ~~ %>

    - value 속성의 값
    
---
