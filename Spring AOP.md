# Spring AOP

---

> Spring AOP 란 , **관점 지향 프로그래밍** 의 약자로 일반적으로 사용하는 클래스 에서 중복되는 공통 코드 부분을 별도의 영역으로 분리해 내고, 코드가 실행 되기 전이나 이 후의 시점에 해당 코드를 붙여 넣음으로써 소스 코드의 중복을 줄이고, 필요할 때마다 가져다 쓸 수 있게 객체화하는 기술을 말한다.



# Spring AOP 용어

---

* AsPect
  * 여러 객체에 공통으로 적용되는 기능을 분리하여 작성한 클래스
* Joinpoint
  * 객체(인스턴스) 생성 시점, 메소드 호출 시점, 예외 발생 시점 등 특정 작업이 시작되는 ㅅ지점
* Advice
  * Joinpoint에 삽입되어 동작될 코드, 메소드
  * Before Advice : joinpoint 앞에서 실행
  * Around Advice : joinpoint 앞과 뒤에서 실행
  * After Advice : joinpoint 호출이 리턴되기 직전에 실행
  * After Returning Advice : joinpoint 메소드 호출이 정상적으로 종료된 후에 실행
* PointCut
  * 조인 포인트의 부분 집합/ 실제 Advice가 적용되는 부분
* Introduction
  * 정적인 방식의 AOP 기술
* Weaving
  * 작성한 Advice (공통 코드)를 핵심 로직 코드에 삽입
  * 컴파일 시 위빙 : 컴파일 시 AOP가 적용된 클래스 파일이 새로 생성
  * 클래스 로딩 시 위빙 : JVM에서 로딩한 클래스의 바이트 코드를 AOP가 변경하여 사용
  * 런타임 시 위빙 : 클래스 정보 자체를 변경하지 않고, 중간에 프록시를 생성하여 경유
* Proxy
  * 대상 객체에 Advice가 적용된 후 생성되는 객체
* Target Object 
  * Advice를 삽입할 대상 객체