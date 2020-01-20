## Tomcat

bin 에 실행파일들잇다. bat파일들

conf 는설정파일을 모아놓은 폴더

ml : 단어에 의미가 있어서 실행됨



web.xml : 공통으로 정의할 것들 정의

서버가 인식하는 기본위치는? webapps.

webapps폴더 안에 docs, examples, root 등등 웹 어플리케이션 폴더들이 있다.
root는 디폴트로 인식되는 폴더

웹 요청 방식 : `http://127.0.0.1:8088/context명/폴더명.../요청할web application`

http://127.0.0.1:8088/docs/index.html

http://127.0.0.1:8088/manager/html

http://127.0.0.1:8088/examples/servlets/index.html

http - 프로토콜
x.x.x.x - 웹서버 IP
8088 : port (web의 기본port는 80이며 생략가능하다. )
context명 - 기본 context는 생략한다.(defalut값은 root가 기본이 된다.)

폴더 하나에 하나의사이트를 포함하고 있다.(web application 폴더, == context )
(webapps는 톰캣에서 context들을 모아놓은 폴더)

서버에 대한 정의는 server.xml에 한다. 

태그(in html) = 엘리먼트(in xml)



![image-20191231094902832](images/image-20191231094902832.png)

연결에 대한 정보. port변경 가능

xml은 대소문자 가린다. (http는 대소문자 구분 없다.)



wepapps 폴더가 아닌 c드라이브에 만든 mypro를 인식시키기 위한 작업으로,
Context 태그를 추가한다. 

![image-20191231104950137](images/image-20191231104950137.png)



서버가 스타트할 때 설정파일을 다 읽는다. 서버는 스타트된 상태인데 중간에 서버파일을 바꾸면 인식을 못하기 때문에, xml변경 시 무조건 서버를 내렸다가 올려야 한다.  (Stop service 한 뒤에 다시 Start service 해주자)

![image-20191231105143759](images/image-20191231105143759.png)



stop하고 start다시 한 뒤 접속해보면 안열리던 주소가 접속 가능해진다.
(http://127.0.0.1:8088/mypro/index.jsp) // 여기서 mypro는 webapps 안이 아닌, 외부 C드라이브 밑에 내가 임의로 생성한 파일. 해당 파일 경로를 server.xml 파일을 열어 Context로 추가함으로써 열리게 할 수 있다. 

![image-20191231105319499](images/image-20191231105319499.png)



정적-> 파일로 찾아 들어가는거

동적



![image-20191231112527293](images/image-20191231112527293.png)

![image-20191231112550740](images/image-20191231112550740.png)



Context는 표준화된 폴더 구조를 갖고있따. 이 폴더엔 어떤게 들어가야하고, 저 폴더엔 어떤게 들어가야하는지 정해져있다(규칙 존재). 위 사진을보면 webapps 폴더 밑에 있는 각 하위 폴더에 모두 web-inf 가 있다.

Context폴더 바로 밑에는 jsp파일, html파일, javascriprt, css , image등을 위치시킨다.

또한 `WEB-INF` 에는 `web.xml`, `lib` 가 있다.

* web.xml : 설정파일
* lib : 외부 라이브러리. ojbc oracle6 넣어야 한다.
*  ![웹구조1](images/웹구조1.png)

![image-20191231113844235](images/image-20191231113844235.png)



스펙 확인하기. 내가 사용하는 was에서 지원하는 어플리케이션의 버전을 봐야한다. (톰캣의 버전 말고)
톰캣의 9.0버전 확인해보면 자바 버전은 8 이상이다.
servlet 은 4.0이하버전 다 사용 가능. JSP는 2.3이하 전부 가능(2.3까지 지원)



![image-20191231114115226](images/image-20191231114115226.png)

![image-20191231114442007](images/image-20191231114442007.png)

![image-20191231114519629](images/image-20191231114519629.png)



자바 읽히려면 라이브러리 필요

![image-20191231114806825](images/image-20191231114806825.png)





![image-20191231131052488](images/image-20191231131052488.png)



![image-20191231131121140](images/image-20191231131121140.png)


![image-20191231135725471](images/image-20191231135725471.png)![image-20191231131717659](images/image-20191231131717659.png)



서버등록

![image-20191231131804690](images/image-20191231131804690.png)

clientwb누르고 add





![image-20191231131827184](images/image-20191231131827184.png)



![image-20191231131956247](images/image-20191231131956247.png)





![image-20191231132055596](images/image-20191231132055596.png)

실행이 안되는 오류상황일 경우
1) port 가 이미 사용중인 경우
2) port가 제대로 안잡혀있는 경우 







![image-20191231133210858](images/image-20191231133210858.png)

![image-20191231133311493](images/image-20191231133311493.png)

8005로 바꿔줬다.  그 담에 다시 start 하면된다. 





![image-20191231133541726](images/image-20191231133541726.png)

![image-20191231133630640](images/image-20191231133630640.png)

![image-20191231133812274](images/image-20191231133812274.png)

---



![image-20191231134153858](images/image-20191231134153858.png)

.metadata : 설정파일 저장된 곳





![image-20191231134227447](images/image-20191231134227447.png)

여기 가

![image-20191231134252490](images/image-20191231134252490.png)



![image-20191231134310078](images/image-20191231134310078.png)

이클립스상 서버가 인식하는 위치

(이클립스 프로그램 안에서 보이는 파일 위치는 우리가 보기 편하라고 되어있어서 실제 위치랑 조금 다를 수 잇다.)



![image-20191231134344169](images/image-20191231134344169.png)

서버가 인식하는 위치에는 똑같이  표준화된 폴더 형태 구조로 되어있다.







br은 같은 문단 줄바꿈이고, p는 문단줄바꿈이다. 