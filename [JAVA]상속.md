## 상속

1. 코드 양, 중복을 줄일 수 있다.

<<상속관계에서 생성자가 갖는 특징>>

 * 모든 생성자 메소드의 첫째줄에는 부모클래스의 기본생성자를 호출하는 명령문이 생략되어있다. 

 * 자동으로 상위클래스를 메모리에 올릴 수 있도록 하자.

 * 또, 자바에서 만드는 모든 클래스는 자바에서 동작하는 객체가 가진 특징을 모두 가져야 한다.

     

 * 모든 클래스의 최상위 클래스 (아무것도 상속하지 않고 있으면)자동으로 object라는 클래스가 상속되어 있다.(안보이지만)

 * 오브젝트 클래스는 객체가 가진 특징을 갖게하는 클래스이다. 

 * 그래서 모든 클래스는최종적으로 object라는 클래스를 부모클래스를 갖고 있으므로, 객체의 특징을 갖고 있는 것이다. 
 
 
 * 생성자 메소드 = 리턴타입이 없는 메소드

     

 * 1. 클래스의 모든 생성자메소드의 첫 번째 문장에는 부모클래스의 기본생성자를 호출하는 명령문이 생략되어 있다.

 * => 부모클래스도 메모리에 할당되어야 사용할 수 있으므로

 * => 부모의 생성자를 호출하는 방법은 super

 * super()는 부모의 매개변수 없는 기본생성자

     

 * => 이미 다른 생성자를 호출하는 경우에는, super()를 할 수 없다. 

 * this()를 호출하는 경우 super()를 호출할 수 없다. 

 * 2. 모든 클래스의 최상위클래스는 java.lang.Object클래스 이다.

 * => 자바에서 실행되는 모든 객체가 갖는 공통의 특징을 정의한 클래스로

 * 상속받고 있는 클래스가 없는 경우, 컴파일러가 자동으로 상속하도록 한다. 
      

 * 3. 부모클래스에 정의되어 있는 멤버변수가 값을 셋팅해야 하는 경우에도

 * 하위클래스에서 전달될 수 있도록 정의하다.

 * super(값1, 값2...)를 통해 접근한다.
      *------------------------------

 *	부모의 매개변수가 있는 생성자를 호출하는 
 
 
 * 부모가 받을 데이터, 내가 받을 데이터 모두 내가 받을 수 있게 처리해야 한다. 

 * this.으로 연출할 수 없는 상황이 있기 때문에 부모클래스에서 호출해서 사용할수 있도록 설계해야 한다. => get/set 메소드 활용하면 좋은 경우들이 있다.

     

```java
class SuperA extends java.lang.Object{ //결국 최상위 클래스는 오브젝트 클래스인 것이다.
	private String name;
	private int age;
	
	SuperA(){ //기본생성자
		super(); // 사실 super();가 생략되어 있는 것이다.
	}
	SuperA(String name, int age) { //앞에 public없어도됨
		super();
		this.name = name;
		this.age = age;
	}
	
}

class SubA extends SuperA{
	String addr; //subA의 경우 superA를 상속하고 있어서 다른 클래스를 상속할 수 없다.
	int point;
	SubA(){ // 서브에이의 기본생성자
		super();
		//super()가 생략되어있다. 모든 생성자메소드의 첫 번째 문장에는 super()가 생략되어있다.
	}
	SubA(String addr){
		super();
		this.addr = addr;
		
	}
	
	SubA(String addr, int point){
		this(addr);
		this.point = point;
		
	}
	SubA(String name, int age, String addr, int point){
		
		//this(addr); //바로 위에 SubA(String addr)에서this.addr = addr; 있으므로
					//현재 객체에 이미 정의되어있는 또다른 생성자를 호출한 것이다. 
		super(name, age); //부모의 매개변수 2개 생성자를 호출.
		//자식이 부모클래스의 private 변수로는( private String name;private int age;)접근 못한다.
		//다른 클래스니까.그래서 super(String,int)를 호출하면 해결할 수 있다.
		this.addr = addr;
		this.point = point;
	}


}

public class Inheritance03 {
	public static void main(String[] args) {
		SubA obj = new SubA("일산", 1000);
		System.out.println(obj.name + "," + obj.addr + ","
				+ obj.age + "," + obj.point); //상위클래스에 있던 하위클래스에 있든 
		//무조건 하위클래스에서 한번에 처리해줘야 한다. 

	}

}

```

