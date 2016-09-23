---
layout: post
title: JavaWebDev - JDBC
---

### 서블릿과 JDBC

  DBMSs -> 각 DBMS들과 애플리케이션 연결하는 Vendor API 사용 -> 각 DBMS에 종속되는 문제 발생 -> ODBC(Open DataBase Connectivity) 등장 -> 표준 API 사용으로 DBMS 종속 탈피

  단점: ODBC API에서 Vendor API를 호출하는 단계가 추가되므로 속도가 느려짐

---

#### JDBC

  - 자바 애플리케이션을 위한 DBMS 접속 인터페이스

  - ODBC 드라이버 사용(JDBC API -> ODBC API -> Vendor API)

  - **JDBC Type2 드라이버** : JDBC API -> Vender

  - **JDBC Type4 드라이버** : JDBC API에서 DBMS와 직접 통신

---

### JDBC 사용 기본 서블릿 (DB 조회) [mariadb 사용]

```java
public class MemberListServlet extends GenericServlet{

	@Override
	public void service(ServletRequest request, ServletResponse response)
			throws ServletException, IOException {
		
		Connection con = null;
		Statement stmt = null;
		ResultSet rs = null;
		try{
			//1. 사용할 JDBC 드라이버를 등록하라.
			DriverManager.registerDriver(new org.mariadb.jdbc.Driver());
		
			//2. 드라이버를 사용하여 MariaDB 서버와 연결하라.
			con = DriverManager.getConnection("jdbc:mariadb://localhost/studydb",
					"root",
					"maria");
			
			//3. 커넥션 객체로부터 SQL을 던질 객체를 준비하라.
			stmt = con.createStatement();
			
			//4. SQL을 던지는 객체를 사용하여 서버에 질의하라
			rs = stmt.executeQuery("SELECT MNO, MNAME, EMAIL, CRE_DATE"
					+ " FROM MEMBERS"
					+ " ORDER BY MNO ASC");
			
			//5. 서버에 가져온 데이터를 사용하여 HTML을 만들어서 웹 브라우저로 출력하라.
			response.setContentType("text/html; charset=utf-8");
			PrintWriter out = response.getWriter();
			out.println("<html><head><title>회원목록</title></head><body>");
			while(rs.next()) {
				out.println(rs.getInt("MNO") + "," +
						rs.getString("MNAME") + "," +
						rs.getString("EMAIL") + "," +
						rs.getDate("CRE_DATE") + "<br />");
			}
			out.println("</body></html>");
			
		} catch (SQLException e) {
			throw new ServletException(e);
			
		} finally {
			try{rs.close();} catch(Exception e){}
			try{stmt.close();} catch(Exception e){}
			try{con.close();} catch(Exception e){}
		}
	}

}
```

---
