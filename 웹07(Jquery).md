## Jquery

- jquery중요성이 줄어드는 추세. -> 자바스크립트 자체를 이해하는게 중요.

- 다음의 세가지를 편하게 처리하기 위해 jQuery를 씀

  1. DOM
     - 선택자 연습!! (이클립스에서 jquery_selector.html), 459Page 표
     - DOM관련 메소드!!
  2. Ajax
3. Effect
  4. jQuery UI
     - jquery.com 접속하기

### DOM

#### 1. 선택자 연습.

- 아래 코드는 Jquery의 CDN인데 head에 있어도 되지만 맨 아래쪽에 선언해주는게 속도도 빠르고 제일 좋다.

- <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script> 



![image-20200113093851269](images/image-20200113093851269.png)





- 선택자 연습1

![image-20200113094350950](images/image-20200113094350950.png)

![image-20200113094822333](images/image-20200113094822333.png)







- 선택자 연습2

  

- 선택자 연습 3, 

  - href를 누르면 href속성을 갖고 있는 모든 구성요소의 color를 skyblue로 하겠다.

  ![image-20200113095028523](images/image-20200113095028523.png)

  ![image-20200113095103509](images/image-20200113095103509.png)



- 선택자 연습4
  - target이 _blank인 것만 변경하겠다.

![image-20200113100836848](images/image-20200113100836848.png)

![image-20200113100732220](images/image-20200113100732220.png)

-  a 태그중 target이 _blank가 아닌것을 핑크로 변경.

![image-20200113101449745](images/image-20200113101449745.png)

![image-20200113101505797](images/image-20200113101505797.png)



- 선택자 연습 5
  - 타입이 버튼인것들을 변경

![image-20200113101807364](images/image-20200113101807364.png)

![image-20200113101843751](images/image-20200113101843751.png)



- 선택자 연습 6
  - tr태그의 짝수, 홀수만 변경 -> 0부터 들어가기 때문에 아래처럼 변경된것.

![image-20200113102419245](images/image-20200113102419245.png)

![image-20200113102519581](images/image-20200113102519581.png)

![image-20200113102457323](images/image-20200113102457323.png)



#### 2. DOM관련 메소드

![image-20200113104109577](images/image-20200113104109577.png)

![image-20200113103512416](images/image-20200113103512416.png)

![image-20200113103526439](images/image-20200113103526439.png)

![image-20200113103548001](images/image-20200113103548001.png)

![image-20200113103604032](images/image-20200113103604032.png)

- remove눌렀을 때

![image-20200113103619288](images/image-20200113103619288.png)

- empty눌렀을 때

![image-20200113103638402](images/image-20200113103638402.png)



- data 변수가 jquery가 아닐때.
  - 기존의 문자열이 없어지지 않고 계속 추가가능. <p>라는 노드가 계속 추가되는 것.
  - data 변수가 jquery일땐 함수가 jquery객체를 공유하기 때문에 하나만 출력 가능하고, 다른 버튼을 누르면 지워짐.

![image-20200113104257233](images/image-20200113104257233.png)

![image-20200113104327557](images/image-20200113104327557.png)





- children(): 특정 노드의 하위노드를 모두 반환, 근데 엘리먼트 노드만 반환함.

![image-20200113104903655](images/image-20200113104903655.png)

![image-20200113104949093](images/image-20200113104949093.png)



- for문을 안 쓰고없이 모든 요소들을 변경할 수 있다. -> 자바스크립트로 짰으면 for문 썼어야됨.

![image-20200113105131255](images/image-20200113105131255.png)

![image-20200113105147904](images/image-20200113105147904.png)





![image-20200113110841366](images/image-20200113110841366.png)

![image-20200113110917859](images/image-20200113110917859.png)



![image-20200113111329921](images/image-20200113111329921.png)

![image-20200113111352743](images/image-20200113111352743.png)



- js_dom에서 domExam.html을 jquery파일에 복사 후 jQuery_dom_exam01.html로 이름 변경

``` jQuery
$(document).ready(function(){
			$("#insertP").on("click",function() {
				data = "<p>newP</p>"; //insert에만 필요하니까 여기에 정의
				$("#root").append(data)
				$("p:last").css("background-color", "yellow"); //p태그의 마지막 요소
			});
			$("#deleteP").on("click",function() {
				$("#root").children().last().remove();
			});	
			$("#deleteDivAndP").on("click",function() {
				$("#root").empty();
			});
		});
```

![image-20200113131036918](images/image-20200113131036918.png)

``` jQuery
<위 그림에서 방법3 적용한 것.>
$(document).ready(function(){
			$("#insertP").on("click",function() {
				data = $("<p>newP</p>"); //insert에만 필요하니까 여기에 정의
				$("#root").append(data)
				data.attr("style","background-color: yellow;border: 1px solid    													blue; font-weight: bolder;");
			});
```





- jquery_exam01.html (김샘자바 예제)

![image-20200113135425279](images/image-20200113135425279.png)

![image-20200113135252230](images/image-20200113135252230.png)



![image-20200113141049841](images/image-20200113141049841.png)

![image-20200113141105005](images/image-20200113141105005.png)



![image-20200113141216100](images/image-20200113141216100.png)

![image-20200113141229901](images/image-20200113141229901.png)



- 매개변수가 있으면 setter, 매개변수가 없으면 getter

![image-20200113142120175](images/image-20200113142120175.png)



![image-20200113143259813](images/image-20200113143259813.png)

![image-20200113143309033](images/image-20200113143309033.png)



## jQuery Ui

![image-20200113154800050](images/image-20200113154800050.png)

밑에 관련 소스 있다. 사이트를 이용해서 필요한 기능을 구현할 수 있다.

id 태그를 유의하여 기능을 작성해놓은곳에 id를 동일하게 맞춰주도록 한다. 