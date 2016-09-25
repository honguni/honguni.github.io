---
layout: post
title: JavaWebDev - Servlet - Context Init
---

### 서블릿 초기화 매개변수

  - 서블릿을 생성하고 초기화할 때 서블릿 컨테이너가 전달하는 데이터
  
  - 보통 데이터베이스 연결 정보와 같은 정적인 데이터를 서블릿에 전달할 때 사용
  
  - DD파일(web.xml)에 서블릿 배치 정보 작성
```java
<servlet>
  <servlet-name>MemberListServlet</servlet-name>
  <servlet-class>spms.servlets.MemberListServlet</servlet-class>
  <init-param>
    <param-name>driver</param-name>
    <param-value>org.mariadb.jdbc.Driver</param-value>
  </init-param>
```

---

```xml
<servlet>
  <servlet-name>Hello</servlet-name>
  <servlet-class>lesson03.servlets.HelloWorld</servlet-class>
</servlet>

<servlet-mapping>
  <servlet-name>Hello</servlet-name>
  <url-pattern>/Hello</url-pattern>
</servlet-mapping>
```
2. 서블릿 클래스에 애노테이션 @WebServlet("/~~~") 추가

  - @WebServlet(urlPatterns={"/hello", "/hello.do", "/hello.action"} -> 여러 개의 URL 설정 가능

  *애노테이션으로 서블릿 배치 정보 등록이 편하지만 배치 정보 탐색 시 모든 클래스를 검색하게 되어 느려질 수 있는 단점 존재*

---

### 웹 애플리케이션 배치

1. Eclipse를 통한 배치 - Add and Remove, 톰캣 설정창 하단 모듈 탭

2. 톰캣 실행 환경의 임시 배치 폴더

  - 톰캣서버는 서버 설정에 배치된 폴더(Workspace - 프로젝트의 property에서 확인 가능)

3. 운영 서버에 배치

  - war 파일로 배포한 후 $TOMCAT_HOME$/webapps 폴더에 붙여넣는다.

  - $TOMCAT_HOME$/bin 폴더에서 startup.sh (윈도우에서는 확장자 bat) 으로 톰캣 서버 올린 후

  - 웹브라우저에서 접근 확인 (http://localhost:8080/helloworld)

  - $TOMCAT_HOME$/bin 폴더에서 shutdown.sh 으로 톰캣 서버 종료

---

### GenericServlet

  - 서블릿 클래스가 필요로 하는 init(), destroy(), getServletConfig(), getServletInfo()를 미리 구현하여 상속

  - service() 메서드만 구현하면 된다.

```java
public class CalculatorServlet extends GenericServlet {
	private static final long serialVersionUID = 1L;
	
	@Override
	public void service(ServletRequest request, ServletResponse response)
			throws ServletException, IOException {
		int a = Integer.parseInt(request.getParameter("a"));
		int b = Integer.parseInt(request.getParameter("b"));
		
		response.setContentType("text/plain");
		response.setCharacterEncoding("UTF-8");
		PrintWriter writer = response.getWriter();
		writer.println("a=" + a + "," + "b=" + b + "의 계산결과 입니다.");
		writer.println("a + b = " + (a + b));
		writer.println("a - b = " + (a - b));
		writer.println("a * b = " + (a * b));
		writer.println("a / b = " + ((float)a / (float)b));
		writer.println("a % b = " + (a % b));

	}

}
```

---

