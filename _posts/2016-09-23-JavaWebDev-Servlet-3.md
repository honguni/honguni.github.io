---
layout: post
title: JavaWebDev - Servlet - Refresh, Redirect
---

### Refresh

  - 작업결과를 출력 후 다른 페이지로 이동

- 응답헤더를 이용한 Refresh

  ```java
  response.addHeader("Refresh", "1;url=list");
  ```

  - HTTP Response헤더에 값 1;url=list를 가진 Refresh 속성 추가.

  - 1초 후 list페이지로 이동

- meta 태그를 이용한 Refresh

  ```html
  <meta http-equiv='Refresh' content='1; url=list'>
  ```

---

### Redirect

  - 작업결과를 출력하지 않고 다른 페이지로 이동

  ```java
  response.sendRedirect("list");
  ```

  - HTTP Response헤더에 sendRedirect()에 입력된 url 매개변수 값을 가진 Location 속성 추가.

  - 리다이렉트 후 통신 HTTP 응답상태코드는 302(요청한 자원이 다른 URL로 이동되어 Location헤더에 있는 주소로 다시 요청)

---
