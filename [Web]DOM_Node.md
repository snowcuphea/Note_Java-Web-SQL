## 노드

DOM은 표준 접근 방법이기때문에 웬만하면 자동 완성이 된다. 

DOM은 문서의 계층적 구조를 트리로 나타내고, 각 요소를 노드(node)로 나타낸다.
노드는 다음과 같이 상호 관계를 상대적으로 부를 수 있다.

* 부모노드
* 자식노드
* 형제노드



`node` : 문서 안에 들어 있는 요소나 텍스트. 공백까지 포함한다.

`element` 는 태그로 된 것. 공백은 element가 될 수 없다. 



## 관련 기능

* 요소 찾기
  * `getElementById("요소아이디")`
  * `getElementsByClassName("클래스이름")`
  * `getElementsByTagName("태그이름")`
  
  
  
* 노드 반환
  * `childNodes` : 한 요소의 모든 자식 요소에 접근, 배열 반환
  
  * `firstChild` : childNodes의 첫 번째 자식 노드 반환. 
    (앞에서부터 삭제 시 사용한다.)
    
  * `lastChild` : childNodes배열의 마지막 자식 노드 반환
    (뒤에서부터 삭제 시 이용한다. )
    
  * `parentNode` : 현재 노드의 부모 노드 반환
  
  * `nextSibling` : 현재 노드의 다음 형제 노드 반환
  
  * `previousSibling` : 현재 노드의 이전 형제 노드 반환
  
    
  
* 노드 관련 함수

  * .createElement("p");
  * .setAttribute("style", "background: pink");
  * targetNode.appendChild(newpNode);
  * parentNode.removeChild(parentNode.lastElementChild);
  * childnodelist = parentNode.childNodes;



---

## 노드 추가 및 삭제 코드

### 노드 추가

```javascript
function insertP() {
			newpNode = document.createElement("p");//노드 만들기. p태그엘리먼트
			newpNode.setAttribute("style", "background: pink"); //만든 노드에 속성 추가
			plustextNode = document.createTextNode("newP");//만든 노드에 텍스트 추가
			newpNode.appendChild(plustextNode);//노드를 추가함.

			// 2. 삽입될 상위 노드
			targetNode = document.getElementById("root");

			// 3. target노드에 새롭게 생성한 노드를 추가 -하위노드로 추가
			targetNode.appendChild(newpNode);
		
	}
```



### 노드 삭제

```javascript
function deleteP() {
			parentNode = document.getElementById("root");
	
			/*if(parentNode.lastChild.nodeName=="#text"){
				parentNode.removeChild(parentNode.lastChild);
			}*/
			parentNode.removeChild(parentNode.lastElementChild);
		//lastChild 는 모든 노드중에 가장 끝에있는것 (공백 포함)
		//lastElementChild는 element, 즉 태그있는 것 중에 제일 마지막 꺼 (공백 포함 안함)
	}
```



### 일정 수준 노드 전부 삭제

```javascript
function deleteDivAndP() {
		// root의 모든하위 노드 제거
		// 배열로 모든 자식노드들을 모아서 삭제하는 방식
		
		parentNode = document.getElementById("root");
		childnodelist = parentNode.childNodes;
		size = childnodelist.length;
		for(i=0; i<size;i++){
			console.log(size);//콘솔 : F12 -> console 창
			parentNode.removeChild(parentNode.lastChild);
		} //length를 for문에 주면 중간에 멈춘다.삭제할때마다 사이즈가 		계속 변하기 때문이다.
		//따라서 size를 고정해주고 for문에 넣어준다. 
```



### 노드 삭제 시 공백을 고려해서 모두 삭제하기

방법 1.

```javascript
for(i=0; i<size;i++){
		console.log(size);//콘솔 : F12 -> console 창
		parentNode.removeChild(parentNode.lastChild);
	} //length를 for문에 주면 중간에 멈춘다.삭제할때마다 사이즈가 계속 변하기 때문이다.
		//따라서 size를 고정해주고 for문에 넣어준다. 
```

방법 2.

```javascript
while(parentNode.hasChildNodes()){ 
    console.log("삭제완료");
	parentNode.removeChild(parentNode.lastChild);
		}
```

방법 3.

```javascript
while(childnodelist.length!=0){ 
	parentNode.removeChild(parentNode.lastChild);
		}
```













## 웹 콘솔창 기능

웹 브라우저에서 F12 => Console 창 에서 타입 체크가 가능하다. (`typeof` )

![image-20200110144552996](C:\Users\student\AppData\Roaming\Typora\typora-user-images\image-20200110144552996.png)

![image-20200110144634358](C:\Users\student\AppData\Roaming\Typora\typora-user-images\image-20200110144634358.png)

`===` 는 값만 비교하는 것이 아니라, 타입까지 체크한다. 

