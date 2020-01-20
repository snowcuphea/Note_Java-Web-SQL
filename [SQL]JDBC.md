# JDBC

java로 JDBC연동하는 기술

(SQL문을 자바로 만든 시스템을 통해 실행할 수 있도록 만들어진 자바의 기술)



**[ JDBC api 사용 전 처리 순서 ]**

1. jdbc드라이버를 제조사 홈페이지에서 다운로드 받는다.

   * C:\oraclexe\app\oracle\product\11.2.0\server\jdbc\lib 폴더에 있는 ojdbc.jar파일

2. JVM이 인식할 수 있는 위치에 연결

   1) 이클립스를 사용하는 경우(Application)

   > ①  작업 중인 프로젝트 선택
   >
   > ② 프로젝트에서 단축메뉴 선택 -> [Build path] - [Configure Build parth] - [library]
   > 
   >
   > ③ 대화상자에서 세 번째 탑인 [Libraries탭 선택]
   > ( 어떤 라이브러리, API를 인식시킬 때도 해당 방법으로 넣는다.)
   >
   > ④ [Add External jar...] 선택하고 1번위치에 있는 ojdbc6.jar파일을 등록

   

**[ JDBC api 사용하기 ]**

1. jdbc드라이버를 제조사 홈페이지에서 다운로드 받는다.

   * 오라클 드라이버 로딩 :
     JVM에서 드라이버 내의 api를 접근해서 사용할 수 있도록 Class클래스의 forName메소드를 이용해서 핵심클래서를 로딩하는 작업

     [문법]

     ```java
     Class.forName("DBMS드라이버의 핵심클래스명")
         		  -------------------------⇒패키지명까지 명시
     ```

     > - 오라클: oracle.jdbc.driver.OracleDriver
     >
     > - MySQL : com.mysql.jdbc.Driver

   
   

2. DBMS에 연결하기

   * DriverManager클래스의` getConnection`메소드를 통해 작업

     1) static메소드이므로 클래스이름으로 액세스

     2) throws SQLException하고 있고, SQLException은 RuntimeException의 하위가 아니므로` try~catch`를 이용해서 exception에 대한 처리를 해야한다.

     3) 매개변수

     > *url : DBMS내부에서 인식할 연결문자열 (어떤 DBMS를 쓰냐에 따라 달라진다.)*
     >
     > ​	[오라클]
     >
     > ```java
     > jdbc:oracle:thin:@70.12.115.50:1521:xe
     > ```
     >
     > * jdbc:oracle:thin: 오라클에서 사용하는 프로토콜
     > * @70.12.115.50: DBMS가 설치;되어 있는 PC의 ip
     > * 1521 : port
     > * xe : 서비스명
     >
     > ex) jdbc:oracle:thin:@127.0.0.1:1521:xe => localhost와 동일 - 로컬에 연결
     >
     > [mysql]
     >
     > ```java
     > jdbc:mysql://ip:port/데이터베이스명(port - 3306)
     > ```
     >
     > *user : 접속계정*
     >
     > *password : 접속할계정의 패스워드*

     

     4) 리턴타입

     * 연결정보를 java.sql.Connection타입으로 리턴
       DriverManager의getConnection메소드를 이용하면 DBMS에 연결 후 연결정보를 객체로 만들어서 리턴한다.
     * 연결객체의 타입은 java.sql.Connection이지만 어떤 DBMS를 접속했냐에 따라 Cpnnection의 하위 객체가 리턴된다.
     * 내부에서는 접속된 DBMS회사에서 제공하는 라이브러리속 Connection이리턴되도록 다형성이 적용되어 있다.

     5) 사용방법

     ```java
     Connection con = 
         	DriverManager.getConnection(url,user,password)
     ```

     => 어떤 DBMS를 쓰냐에 따라 다르게 리컨되는 Connection객체를 con이라는 참조변수를 통해 접근할 수 있도록 할당

     

3. SQL을 실행하는 역할을 담당하는 Statement객체 생성

   `statement`			 		: 정적 SQL을 실행 (보안에 취약 - SQLInjection에 취약)
   		↑ 상속									

   `preparedStatement`	: 동적 SQL을 실행 (시큐어코딩에 적합)

   ​		↑ 상속						

   `CallableStatement`	:  각 DBMS에 특화된 SQL을 실행
   											ex.오라클 : PL-SQL

   1) Statement객체를 이용
   	Connection 객체에 있는 createStatement메소드를 통해 상성
   	Connection 정보를 유지해야 한다.

   ```java
   Statement stmt = con.createStatement();
   --------
   	└> java.sql.Statemet타입이지만
   		드라이버파일에 포함된 Statement 객체가 리턴.
   ```

   

   2) PreparedStatement객체를 이용



4. SQL실행

   1) Statement 이용

   > ① executeUpdate : insert, updeate, delete문을 실행
   >
   > ```java
   > int 결과값 = stmt.executeUpdate(sql문)
   > ---------					   -----
   > └> sql문 실행 결과			     └>insert, delete, update
   > ```
   >
   > 몇 개의 row가 변경됐는지 리턴

   2) PreparedStatement 이용
   	=> 동적SQL문을 사용해야 하기 때문에

   * sql이 실행되는 과정은 (반복해서 실행됨)

     * 쿼리문을 읽고 분석
     * 컴파일
     * 실행

   * statement는위의 단계를 모두 반복해서 실행하고 작업하지만, PreparedStatement는 한 번 실행하고 캐시메모리에 저장하고
      캐시메모리에서 읽어서 작업함. (한번만 실행됨)

   * PreparedStatement의 sql문을 실행하는 방식은 sql문을 미리 파싱한 후,
     동적으로 바인딩해서 작업해야 하는  값들만 나중에 연결해서 인식시키고 실행한다.

     ① sql문을 작성할 때 외부에서 입력받아서 처리해야하는 부분을 ?로 정의한다.

     ② sql문을 미리 파싱해야 하므로 실행할 때 sql을 전달하지 않고 PreparedStatement객체를 생성할 때 sql문을 전달한다. 

     ```java
     preparedStatement ptmt = con.prepareStatement(sql문)
     ```

     

     ③?에 값을 셋팅
     	PreparedStatement 객체에 정의되어 있는 setXXXX메소드를 이용
     	ResultSet과 동일한 방식으로 메소드를 구성

     ```java
     setXXXX(index, 값)
     ------- -----  --
     컬럼타입  ?순서    └> 컬럼에 설정할 값
     		1부터시작
     ```

     

     오라클 타입과 매칭되는 setXXXX 메소드

     * char, varchar2 -> setString(1,"XXXX")

     * number, integer -> setInt (1,0000)

     * 소수점이 있는 number -> setDouble(1, 0.0)

     * date -> setDate(1, java.sql.Date객체)

       


     ④ 실행메소드 호출

     * insert, delete, update

       ```java
       int result = ptmt.executeUpdate();
       ```

     * select

       ```java
       ResultSet rs = ptmt.executeQuery();
       ```

   

   

5. 결과값 처리

   1) insert, delete, update모두 동일

   * int로 결과값을 리턴하므로 결과값을 출력

   2) select 

   > ① select문의 실행결과로 반환되는 ResultSet을 참조할 수 있도록 정의한다.

   ```java
   ResultSet rs = stmt.excuteQuery("sql문");
   ```

   > ② ResultSet안에서 모든 레코드를 읽어서 처리할 수 있도록 반복문을 이용해서 처리 (한번에 하나씩 밖에 못읽으니까.)
   > 	처음 반환되는 ResultSet에서 Cursor가 레코드에 위치하지 않으므로 Cursor를 ResultSet안의 레코드에 위치할 수 있도록 내부 메소드를 이용해 처리한다.
   >
   > ```java
   > while(rs.next()){
   >       ----------> 다음 레코드로 Cursor를 이동하고 레코드가 존재하면 					true를 리턴하고
   > 					레코드가 존재하지 않으면 false를 리턴한다.
   >                         
   >        } 
   > ```
   >
   > ③ 레코드의 값을 읽는 작업
   >
   > * 한 번에 하나의 컬럼만 읽을 수 있다.
   >
   > * ResultSet내부에서 제공되는 getXXXX메소드를 이용한다. 
   >   (대부분 XXXX는 데이터 타입이 될 것임)
   >
   >   * rs.getXXXX(1)
   >               --------- > 데이터타입, 테이블에 존재하는 컬럼의 원래순서가 							아니라 조회된 컬럼의 순서(indext가 1부터 시작)
   >
   > * 오라클(DBMS)의 타입과 매칭되는 자바의 타입으로 메소드명이 구성됨.
   >
   >   * varchar2 of char로 정의된 컬럼값 : getString(컬럼의 순서 or 컬럼명)
   >
   >   * 소수점없는 number or integer : getInt(컬럼의순서 or 컬럼명)
   >   * 소수점이 있는 number : getDouble(컬럼의순서 or 컬럼명)
   >   * 날짜데이터 : getDate(컬럼의순서 or 컬럼명)
   >
   >   ```java
   >   while(rs.next()){
   >   	 ----------> 조회된 테이블의 모든 레코드에
   >   					반복 작업하겠다는 말.
   >   	 sysout(rs.getString(1)) -> 조회된 레코드의 첫 번째 컬럼								값을 가져오겠다는 말.
   >   	 sysout(rs.getString("ename")) -> 조회된 레코드의 컬럼명이 					ename인 컬럼의 값을 가져오겠다는 말.
   >   	 	   
   >   	 	   }
   >   ```
   >
   >   

   



6. 자원 반납
   * 자원을 반납하지 않으면 계속 메모리에 할당되어 있는 상태.
     ResultSet, Statement, Connection모두 반납해야 한다.
     close메소드를 이용해 자원해제.
     가장 마지막에 만들어진 객체부터 해제해야 한다.
   * 









1. 드라이버파일을 JVM이 인식할 수 있는위치에 연결 
2. 드라이버 로딩 (클래스들을 로딩)   
   - 내가 new로 생성할 수 없다. 왜냐하면 내부 스펙을확인할 수 없으니까 (lock 걸려있음) 외부에서 갖고온 jar 파일 = 외부에서 갖고온 API.
3. DBMS연결
4. SQL을 실행하는 기능을 갖고있는 객체를 생성 
5. SQL 실행 