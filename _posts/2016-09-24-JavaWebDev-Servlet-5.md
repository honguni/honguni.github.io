---
layout: post
title: JavaWebDev - Servlet - Filter
---

### 필터

  - 로그출력

  - 사용자 인증 및 권한 검사

  - 암호화 및 복호화

  - 데이터 압축 및 해제

  - 이미지 변환 등

    - 필터 패키지안에 필터 생성
    
```java
  public class CharacterEncodingFilter implements Filter{
	FilterConfig config;
	
	@Override
	public void destroy() {}

	@Override
	public void doFilter(ServletRequest request, ServletResponse response,
			FilterChain nextFilter) throws IOException, ServletException {
		// 서블릿을 실행하기 전에 수행할 작업
		request.setCharacterEncoding("UTF-8");
		nextFilter.doFilter(request, response);
		// 서블릿을 실행한 후 수행할 작업
	}
	@Override
	public void init(FilterConfig config) throws ServletException {
		this.config = config;
	}
  }
```
  - web.xml에 필터 정의
  
```xml
  <filter>
	<filter-name>CharacterEncodingFilter</filter-name>
	<filter-class>filters.CharacterEncodingFilter</filter-class>
  </filter>
	
  <filter-mapping>
	<filter-name>CharacterEncodingFilter</filter-name>
	<url-pattern>/*</url-pattern>
  </filter-mapping>
```
---
