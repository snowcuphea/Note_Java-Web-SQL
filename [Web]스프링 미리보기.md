Web, DB연동, 트랜잭션, 로그, IoC컨테이너(객체를 관리, lifecycle, 컨테이너)

## 스프링의 특징

- 스프링에서는 객체를 Bean 이라고 부른다.
- 클래스를 운영하는 방식이 정해져있다.
- xml로 설정파일을 관리한다.

[conf.properties](http://conf.properties) 설정파일을 생성해서, 요청할 문자열들을 적자. (추후 기능이 있는 자바 코드를 수정할 필요가 없고, 명세를 적어놓은 properites 설정파일만 수정하거나 추가하면 된다.)

name 과 value가 있는 map을 생성해서 해당 값이 있는 경우 요청을 수행할 수 있도록 한다.

스프링은 내부에서 사용되는 객체를 알아서 대신 생성해서 넘겨주는 작업을 해준다.

스프링과 관련된 라이브러리 중 beans와 context가 들어가는 라이브러리의 클래스들은 객체생성과 관련된 일들을 하는 클래스들이다. core는 핵심 기능 라이브러리들

## [ 설정파일 만들기 ]

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c4740916-c063-413f-91bb-1fa6bf5db37f/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c4740916-c063-413f-91bb-1fa6bf5db37f/Untitled.png)

## [ 나만의 라이브러리 추가 ]

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f8262176-798b-446e-a4ed-61c7a8f4c2b0/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f8262176-798b-446e-a4ed-61c7a8f4c2b0/Untitled.png)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/10671af5-dbac-4256-8cdf-149c0996e226/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/10671af5-dbac-4256-8cdf-149c0996e226/Untitled.png)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d91ce482-a8d5-4156-9423-cfe961cb0d49/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d91ce482-a8d5-4156-9423-cfe961cb0d49/Untitled.png)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/812a7553-fab1-468e-8d4b-6791360e5b8c/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/812a7553-fab1-468e-8d4b-6791360e5b8c/Untitled.png)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b133f973-5836-412a-96ee-c8a9b94c5fc3/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b133f973-5836-412a-96ee-c8a9b94c5fc3/Untitled.png)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5913c65e-2879-4b28-a3c6-9dce82c7e287/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5913c65e-2879-4b28-a3c6-9dce82c7e287/Untitled.png)

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b834590d-9a79-425b-a7da-ff19eeb9f4c9/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b834590d-9a79-425b-a7da-ff19eeb9f4c9/Untitled.png)