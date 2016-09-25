---
layout: post
title: JavaWebDev - Servlet - ContextInit
---

### 서블릿 초기화 매개변수

  - 서블릿을 생성하고 초기화할 때 서블릿 컨테이너가 전달하는 데이터
  
  - 보통 데이터베이스 연결 정보와 같은 정적인 데이터를 서블릿에 전달할 때 사용
  
  - DD파일(web.xml)에 서블릿 배치 정보 작성
  
  ```xml
  <servlet>
    	<servlet-name>MemberListServlet</servlet-name>
    	<servlet-class>spms.servlets.MemberListServlet</servlet-class>
  	<init-param>
   		<param-name>driver</param-name>
  		<param-value>org.mariadb.jdbc.Driver</param-value>
  	</init-param>
  	<init-param>
  		<param-name>url</param-name>
  		<param-value>jdbc:mariadb://localhost/studydb</param-value>
  	</init-param>
  	<init-param>
  		<param-name>username</param-name>
  		<param-value>root</param-value>
  	</init-param>
  	<init-param>
  		<param-name>password</param-name>
  		<param-value>maria</param-value>
  	</init-param>
  </servlet>
  
  <servlet-mapping>
  	<servlet-name>MemberListServlet</servlet-name>
  	<url-pattern>/member/list</url-pattern>
  </servlet-mapping>
  ```

---
