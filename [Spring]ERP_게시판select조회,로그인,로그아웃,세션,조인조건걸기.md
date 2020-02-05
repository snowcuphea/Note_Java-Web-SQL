## 게시판 카테고리별 보기

1. baord.xml에 새로운 select문 생성

파라미터타입은 스트링. 하나를 가져올꺼니까
대부분 스트링이다.

![image-20200203092359203](C:\Users\LG\AppData\Roaming\Typora\typora-user-images\image-20200203092359203.png)

2. DAO에 메소드를 하나 만든다.  DAO는 sql문 하나당 하나씩 만들어져야 한다.
   DAOImpl도 해당 부분 추가 및 수정해준다. 

   ![image-20200203092431404](C:\Users\LG\Desktop\Note\[Spring]ERP_Board_CategorySearch)



3. top.jsp

   ![image-20200203093225896](images/image-20200203093225896.png)

4.  Boardcontroller가서 boardList 매개변수 수정

   컨트롤러 하나가지고 통합하려고 이렇게 한다. (컨트롤러 하나로 두 개의 기능 처리)

   ![image-20200203094130674](images/image-20200203094130674.png)



5. BoardService 에서 수정

![image-20200203093459733](images/image-20200203093459733.png)



6. BoardServiceImpl도 String으로 category 받아준다. 

![image-20200203093724354](images/image-20200203093724354.png)



7. help > eclipse market > tern > 맨 위에꺼 설치

![image-20200203094230578](images/image-20200203094230578.png)

![image-20200203094652920](images/image-20200203094652920.png)

![image-20200203094712309](images/image-20200203094712309.png)







8. 액션을 처리하는 부분, boardlist.jsp 에서 처리한다. 근데 submit이 아니라서 할 수 없어서, jquery로 실행되게 할 것이다.

![image-20200203095731944](images/image-20200203095731944.png)



9. 컨트롤러 파일에서 리다이렉트 또한 category=all추가해준다. 해주지 않으면 글 작성 시 등록 버튼 누르면 오류난다. 

![image-20200203102112582](images/image-20200203102112582.png)



10. category 는 response이자 request. 선택한 카테고리를 뷰로 보여주기 위해서 설정한다. 

![image-20200203103126053](images/image-20200203103126053.png)

![image-20200203110049986](images/image-20200203110049986.png)



또한 internet explorer는 한글인코딩을 자동으로 해주지 않기 때문에 한글인코딩을 지원하는 소스를 적어준다. `encodeURI()`

![image-20200203103917532](images/image-20200203103917532.png)

---

# 검색어 별로 조회

1. board.xml 에 추가해준다.

![image-20200203105210877](images/image-20200203105210877.png)

2. boardDAOImpl

![image-20200203104638144](images/image-20200203104638144.png)



3. board.xml에 tag에 대한 경우를 jsp의 select 태그 각각의 value값에 대해 조건을 준다. 

![image-20200203112714014](images/image-20200203112714014.png)



4. boardserviceImpl 수정

![image-20200203110753848](images/image-20200203110753848.png)





5. 컨트롤러 수정

![image-20200203111436593](images/image-20200203111436593.png)

![image-20200203111407520](images/image-20200203111407520.png)



---



---

---

---

---

---

---

---

---

# 실습 : multi.erp.emp 로그인



EmpServiceImpl, EmpDAOIMpl, emp.xml(namespace-multi.erp.emp)



request view -> Controller -> service -> dao -> mapper.xml
  (login.jsp)			    ㅣ
							   	ㅣ
							response view(board/list.do)
								로그인 후 top.jsp의 이미지가 로그인 사용자 이미지로 변경 



---

1. memberVO 에서 생성자, getter setter, toString 추가
2. config > mybatis-config.xml에 MemberVO추가

![image-20200203133138959](images/image-20200203133138959.png)



3. emp.xml에서 memberlogin의 타입을 emp로 설정. DTO로 하려고

![image-20200203133418860](images/image-20200203133418860.png)



4. MemberVO에서 로그인 파라미터 매핑용 생성자 추가

![image-20200203133554090](images/image-20200203133554090.png)



5. DAOImpl에서 login메소드 작성 - selectOne메소드 사용

![image-20200203134001862](images/image-20200203134001862.png)



6. Service 하는 곳 작성

![image-20200203134759644](images/image-20200203134759644.png)





7. 컨트롤러 작성. 일단 데이터를 잘 받아왔는지부터 체크하기 위해서 sysout으로 뿌려본다. 

![image-20200203134734520](images/image-20200203134734520.png)





8. web-inf > emp > login.jsp 들어가서 form 의 acdtion 경로 수정

![image-20200203135031346](images/image-20200203135031346.png)





type='image' 이면 submit버튼과 같은 역할을 한다. 

![image-20200203135202835](images/image-20200203135202835.png)





스프링을 사용하는 목적 DI를 쓰는 목적

1. 의존성, 커플링을 낮추면서 유지보수를 최적화
2. Spring



아직은 이 로그인파라미터 맵핑용 생성자를 사용안한다. 기본생성자는 무조건 !!!! 호출된다. 

![image-20200203142959405](images/image-20200203142959405.png)



user 프로필 이미지 바꾸기

top.jsp 파일로 가서 객체 만들고, 이미지 부분 수정해준다. 

![image-20200203145331040](images/image-20200203145331040.png)

로그인은 유저가 있든 말든 모두 처리하나, 프로필 이미지는 로그인에 성공했을때, 즉 유저가 있을 때만 발생하기 때문에 그에 대해 조건을 걸어준다.

if부분은 로그인 사용자가 아닌 전체 사용자한테 보여주고, else부분은 로그인 한 사용자에게만 보이는 화면이다.

![image-20200203145749265](images/image-20200203145749265.png)



상태정보유지

쿠키 : 클라이언트에게 노출됨

세션 : 서버 메모리에 사용자별로 공간을 하나 만들어서 저장할 수 있도록 제공됨.
주로 로그인한 사용자의 정보가 저장된다. 

브라우저를 띄워놓고 세션을 그만하도록 없애지 않는 이상, 브라우저를 사용하는 동안은 살아있다. 

세션을 만드는 시점 : 로그인
세션을 끊는 시점 : 로그아웃 

---

리퀘스트 : 한번 요청이 들어갔다가 나오면 없어짐
세션 : 브라우저를 띄워놓으면 계속 사용할 수 있다. (은행같이 보안이 중요한 곳은 세션 유효시간을 걸어놓기도 한다. )

리퀘스트와 세션에 저장해야 하는 데이터 구분은 어떻게 할까?

* 게시판 : 리퀘스트로 구현
* 로그인 : 세션으로 구현 





컨트롤러 수정

![image-20200203152730013](images/image-20200203152730013.png)



그에 맞게 top.jsp 도 세션 관련 객체를 받을 수 있도록 수정해준다.

![image-20200203153136492](images/image-20200203153136492.png)



로그아웃 시 세션을 끊어야 하므로, 그에 대한 동작을 컨트롤러에서 작성해준다.

![image-20200203153444369](images/image-20200203153444369.png)

---



조인 조건을 활용하기 



MemberVO에 3개 변수 추가해주고, 전체생성자와 getter, setter 만든다. toString도 다시만든다.

![image-20200203155308892](images/image-20200203155308892.png)



emp.xml에 조건을 걸어준다. 

![image-20200203155357566](images/image-20200203155357566.png)



결과화면

![image-20200203155550968](images/image-20200203155550968.png)

이처럼 한 테이블이 아닌, 조인조건을 통해서 여러 테이블에서 정보를 출력할 수 있다. 



---



