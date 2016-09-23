---
layout: post
title: JavaWebDev - Servlet - 1
---

[CGI](https://ko.wikipedia.org/wiki/%EA%B3%B5%EC%9A%A9_%EA%B2%8C%EC%9D%B4%ED%8A%B8%EC%9B%A8%EC%9D%B4_%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4){:target="_blank"} - 웹서버와 애플리케이션 사이의 데이터를 주고받는 규칙

[서블릿](https://ko.wikipedia.org/wiki/%EC%9E%90%EB%B0%94_%EC%84%9C%EB%B8%94%EB%A6%BF){:target="_blank"} - 자바로 만든 CGI 프로그램

[WAS](https://ko.wikipedia.org/wiki/%EC%9B%B9_%EC%95%A0%ED%94%8C%EB%A6%AC%EC%BC%80%EC%9D%B4%EC%85%98_%EC%84%9C%EB%B2%84){:target="_blank"} - 웹 기술을 기반으로 클라이언트·서버 시스템 구조에서 

서버 쪽 애플리케이션의 생성과 실행, 소멸을 관리

---

javax.servlet.Servlet 인터페이스

```java
public class HelloWorld implements Servlet {
	ServletConfig config;
	
	@Override
	public void init(ServletConfig arg0) throws ServletException {
		System.out.println("init");	
		this.config = config;
	}

	@Override
	public void service(ServletRequest arg0, ServletResponse arg1)
			throws ServletException, IOException {
		System.out.println("service");
	}
	
	@Override
	public void destroy() {
		System.out.println("destroy");
		
	}

	@Override
	public ServletConfig getServletConfig() {
		System.out.println("getServletConfig");
		return this.config;
	}

	@Override
	public String getServletInfo() {
		System.out.println("getServletInfo");
		return "HelloWorld Servlet";
	}

}
```

- init() : 서블릿 컨테이너가 서블릿을 생성 후 초기화 작업을 수행하기 위해 호출하는 메서드

- service() : 클라이언트가 요청할 때 마다 호출되는 메서드

- destroy() : 서블릿 컨테이너가 종료되거나 웹 애플리케이션이 멈출 때, 또는 해당 서블릿을 비활성화 

시킬 때 호출되는 메서드

- getServletConfig() : 서블릿 설정 정보를 다루는 ServletConfig 객체 반환

- getServletInfo() : 서블릿을 작성한 사람에 대한 정보, 서블릿 버전, 권리 등을 담은 문자열 반환

---

### 서블릿 배치 정보 작성

1. web.xml에 등록

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

  - 서블릿 클래스가 필요로 하는 init(), destroy(), getServletConfig(), getServletInfo()를 미리 구현

하여 상속

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

