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
  - 서블릿에서 ServletConfig객체를 이용하여 초기화값 획득

```java
  //1. 사용할 JDBC 드라이버를 등록하라.
  //DriverManager.registerDriver(new org.mariadb.jdbc.Driver());
  //ServletConfig config = this.getServletConfig();
  //Class.forName(config.getInitParameter("driver"));
  Class.forName(this.getInitParameter("driver"));
			
  //2. 드라이버를 사용하여 MariaDB 서버와 연결하라.
  //con = DriverManager.getConnection("jdbc:mariadb://localhost/studydb",
  //		"root",
  //		"maria");
  con = DriverManager.getConnection(
                this.getInitParameter("url"),
                this.getInitParameter("username"),
                this.getInitParameter("password"));
```

  - DB정보가 바뀌더라도 web.xml만 편집하면 되기 때문에 유지보수가 쉬워짐

---

### 컨텍스트 초기화 매개변수

  - 모든 서블릿이 사용 가능

  - DD파일 (web.xml)

```xml
  <context-param>
	<param-name>driver</param-name>
	<param-value>org.mariadb.jdbc.Driver</param-value>
  </context-param>
  <context-param>
	<param-name>url</param-name>
	<param-value>jdbc:mariadb://localhost/studydb</param-value>
  </context-param>
  <context-param>
	<param-name>username</param-name>
	<param-value>root</param-value>
  </context-param>
  <context-param>
	<param-name>password</param-name>
	<param-value>maria</param-value>
  </context-param>

  <servlet>
	<servlet-name>MemberListServlet</servlet-name>
	<servlet-class>spms.servlets.MemberListServlet</servlet-class>
  </servlet>
```
  - 서블릿
  
```java
  //1. 사용할 JDBC 드라이버를 등록하라.
  ServletContext ctx = this.getServletContext();
  Class.forName(ctx.getInitParameter("driver"));
			
  //2. 드라이버를 사용하여 MariaDB 서버와 연결하라.
  con = DriverManager.getConnection(
		ctx.getInitParameter("url"),
		ctx.getInitParameter("username"),
		ctx.getInitParameter("password"));
```

---
