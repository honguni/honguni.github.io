---
layout: post
title: JavaWebDev - Servlet - Context Init
---

### 서블릿 초기화 매개변수

  - 서블릿을 생성하고 초기화할 때 서블릿 컨테이너가 전달하는 데이터

  - 보통 데이터베이스 연결 정보와 같은 정적인 데이터를 서블릿에 전달할 때 사용

  - DD파일(web.xml)에 서블릿 배치 정보 작성
  ```html
  <context-param>
    <param-name>driver</param-name>
    <param-value>org.mariadb.jdbc.Driver</param-value>
  </context-param>
  ```
