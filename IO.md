# I/O

자바 2권 868p

* 자바프로그램 안으로 데이터가 들어오면 입력: 네트워크, 키보드, 바코드 등등으로부터

* 자바프로그램 밖으로 데이터가 나가면 출력 : 네트워크, 모니터, 파일 등등으로 보내기

이렇게 데이터 입출력을 수행하기 위한 것을 스트림이라고 한다. java.io 패키지에 입력스트림, 출력스트림이 있다.



1. Byte 단위 
   * ~InputStream : byte단위 입력
   * ~OutputString : byte단위로 출력
2. 문자 단위
   * ~Reader : 문자단위 입력
   * ~write : 문자단위 출력

FileInputStream에서 파일을 처리할 때 반드시

1.open 2.access 3.close 단계로 해야한다. 그것만 하면 나머지는모두 생성자에서 알아서 처리된다.



버퍼 : 임시적으로 문자열 배열 한것

---

FileReaderTest.java와 BufferedReaderTest.java 코드 내용은 같으나,
Buffer를 사용한 bufferedReaderTest.java의 실행횟수와 실행시간이 10배 더 짧다. 

BufferedReaderTest의 효율이 훨씬 더 높다. 