
# Chapter 04 조건문 반복문

- switch 제약조건
    - 1 switch문의 조건식 결과는 정수 또는 문자열이어야 한다
    - 2 case문의 값은 정수 상수만 가능, 중복되면 X
    - 즉, 변수(int num 등) 실수(1.0 등) 불가

- for문 
    - 내부 순서
        - 초기화, 조건식, 구문, 증감식
    - 다수의 증감문
        - for(int i=0, int j=10; i<=10; i++, j--);
    - 향상된 for 문
        - for( tpye value : arr OR collection ) { ... }
    - 이름이 붙은 반복문
        - break, continue 로 빠져나갈 수 있는 범위 지정을 위해 사용
        - ```
          // for문에 Loop 이름 붙이기
          Loop : for(int i=0; i<10; i++) {
                    for(int j=0; j<10; j++) {
                        if(i==2)
                            continue Loop;  // 이중 for 문 전체를 continue;
                            continue;       // 안쪽 for 문만 continue;
                        if(j==5)
                            break Loop; // 이중 for 문 전체를 break;
                            break;      // 안쪽 for 문만 break;

                        ...
                    }
          }
          ```

# Chapter 05 배열

- 길이가 0인 배열
    - int arr = new int[0];

- 배열 선언과 동시에 초기화
    - int arr = new int[] {0, 1, 2, 3, 4};
    - int arr = {0, 1, 2, 3, 4};

- System.arraycopy(src, 0, dest, 0, src.length)
    - src[0] 에서 dest[0]로 src.length만큼 복사

- char 배열은 for문 없이 println으로 모든 문자 출력 가능

- String 배열 선언과 동시에 초기화
    - String[] names = new String[] {"Kim", "Park", "Yi"};
    - String[] names = {"Kim", "Park", "Yi"};

- String 객체는 read only
    - ```
      String str = "Java";
      str += "8";
      ```
    - 결과: Java8
    - 문자열이 변경되는 것 같지만, 변경 불가능하므로 새 문자열 생성

- String 주요 메서드
    - char charAt(int index) : index에 있는 문자 반환
    - int length() : 문자열 길이 반환
    - String substring(int form, int to) : from ~ to 사이의 문자열 반환(to는 범위 미포함)
    - boolean equals(Object obj) : 문자열의 내용이 obj와 같은지 확인
    - char[] toCharArray() : 문자열을 문자배열(char[])로 변환해서 반환한다

- 커맨드 라인을 통해 입력 받기
    - java GetMainArgs abc 123
    - main(String[] args)의 args[0] = "abc", args[1] = "123"이 됨

- 가변배열
    - ```
      int[][] tmp = new int[5][];
      tmp[0] = new int[1];
      tmp[1] = new int[2];
      tmp[2] = new int[3];
      tmp[3] = new int[4];
      tmp[4] = new int[5];
      ```

# Chapter 06 객체지향 프로그래밍 I

- 객체 배열(참조변수 배열)
    - Tv[] tvArr = new Tv[3];
    - Tv[] tvArr = {new Tv(), new Tv(), new Tv()};

- 변수의 종류
    - ```
      class Variables {
          int iv;           // instance 변수
          static int cv;    // class 변수 (static 변수, 공유 변수)

          void method() {
              int lv = 0;   // 지역 변수
          }
      }
      ```
    - 클래스 변수 (공통 요소-규격 등-에 사용)
        - 선언위치 : 클래스 영역
        - 생성시기 : 클래스가 메모리에 올라갔을 때
    - 인스턴스 변수 (개별 요소에 사용)
        - 선언위치 : 클래스 영역
        - 생성시기 : 인스턴스가 생성 됐을 때
    - 지역변수(클래스 내부 변수, 매개변수 등)
        - 선언위치 : 클래스 이외의 영역(메서드 내부, 생성자, 초기화 블럭 내부 등)
        - 생성시기 : 변수 선언문이 실행됐을 때
    
- 메서드의 사용 이유
    - 높은 재사용성
    - 중복 코드 제거
    - 프로그램 구조화
    
- 매개변수 유효성 검사
    - 들어온 매개변수의 값이 적절한지 확인
    - divide 0 문제 등을 일으킬수 있으므로

- JVM 메모리 구조
    - 프로그램 실행시, JVM은 필요한 메모리를 할당 받아 method area, call stack, heap으로 나눠 관리
    - Method Area
        - 클래스 데이터 및 클래스 변수 저장
    - Call Stack
        - 메서드 작업에 필요한 메모리 공간 제공
        - 메서드 작업 수행하는 동안 지역변수, 매개변수 등 연산의 중간 결과등을 저장하는데 사용
        - 작업 끝나면 반환
    - Heap
        - 인스턴스가 생성되는 공간
        - 인스턴수 변수들이 생성됨

- 재귀호출
    - 스택오버 플로우등의 문제 발생할 수 있으므로, 매개변수 유효성 검사를 잘 해주어야함
    - 반복문이 더 빠르지만 논리적인 간결함이 주는 이점 때문에 사용
    - 점화식일때 많이 사용 (대표적으로 팩토리얼)

- 클래스 메서드(static 메서드)와 인스턴스 메서드
    - 클래스 메서드
        - 인스턴스와 상관 없는 메스드를 클래스 메서드로 정의
    - 인스턴스 메서드
        - 메서드 작업 수행시, 인스턴스 변수를 필요로 하는 메서드
    - 메서드 설계
        - 멤버변수 중, 모든 인스턴스 공통으로 사용하는 것 = static
        - 클래스 변수는 인스턴스 생성이 없어도 사용 가능
        - 클래스 메서드는 인스턴스 변수 사용 불가능
        - 메스드 내에서 인스턴스 변수를 사용치 않는다면 클래스 메서드로 전환 고민

- 가변인자(varargs)와 오버로딩
    - 가변인자외에 다른 매개변수가 있다면, 가변인자가 마지막에 선언되어야 함
    - String... args = 가변인자 매개변수
    - ```
      static String concatenate(String delim, String... args) {
          String result = "";

          for(String str: args) {
              result += str + delim;
          }

          return result;
      }
      ```

- 초기화 블럭
    - 초기화 작업이 복잡하여 명시적 초기화로 부족한 경우 사용
    - ```
      class InitBlock {
          static {
            /* 클래스 초기화 블럭 */ 
          }

          { 
            /* 인스턴스 초기화 블럭 */ 
          }

          InitBlock() {

          } 

          ...
      }
      ```

- 멤버변수의 초기화 순서
    - 클래스 변수 초기화 시점 : 클래스 처음 로딩 될때 단 한번
    - 인스턴스 변수 초기화 시점 : 인스턴스 생성시 마다 각 인스턴스별 초기화
    - 클래스 변수 초기화 순서 : 기본값 -> 명시적 초기화 -> 클래스 초기화 블럭
    - 인스턴스 변수 초기화 순서 : 기본값 -> 명시적 초기화 -> 인스턴스 초기화 블럭 -> 생성자

# Chapter 07 객체지향 프로그래밍 II

- 클래스간 관계 설정
    - is a
        - 상속관계
    - has a
        - 포함관계

- 자바는 단일상속만 허용

- 최상위 클래스 Object

- super();
    - 부모의 디폴트 생성자를 호출
    - 만약 부모의 디폴트 생성자가 없다면 Error

- import static 문
    - import -> 클래스 패키지명 생략
    - import static -> static 멤버 호출시 클래스 이름 생략
    - import static java.lang.Math.random;
        - Math.random() -> random() 으로 사용 가능

- 제어자
    - static
        - 메서드에 선언, 공통으로 사용하는 메서드(body가 있는 메서드여야 함)
        - 변수에 선언, 공통으로 사용하는 변수
    - final
        - 클래스에 선언, 확장할 수 없는 클래스
        - 메서드에 선언, 오버라이딩 불가 메서드(private선언과 둘중 하나만)
        - 변수에 선언, 값 변경이 불가능한 변수
    - abstract
        - 클래스에 선언, 클래스 내에 추상 메서드 존재 의미
        - 메서드에 선언, 추상 메서드임을 의미
    - native
        - 자바가 아닌 언어(보통 C나 C++)로 구현한 후 자바에서 사용하려고 할 때 이용하는 키워드
    - transient
        - serializable 사용시, 보안 등의 문제로 보내고 싶지 않은 멤버 변수등에 사용
        - transient 선언시, null값 전송
    - synchronized
        - 멀티스레드 환경에서 data의 thread-safe를 위해 사용
        - 너무 남용하면, context switching 비용으로 인해 오히려 성능 저하를 가져옴
        - 메서드에 선언, 메서드에 접근시 rock, 메서드 종료시 unlock
        - 변수에 선언, 변수 접근시 rock, 변수 종료시 unlock
    - volatile
        - 변수에 선언, 변수 값 Read & Write시, cache가 아닌 메모리를 대상으로 한다는 의미
        - 왜 필요? 
            - 멀티스레드 환경에서 각 스레드별 캐시가 다르므로 변수 값 불일치 문제 발생
        - 언제 사용?
            - 하나의 스레드만 Read & Write를 하고 나머지 스레드는 Read만을 하는 경우
        - 사용하지 말아야할 경우?
            - 여러 스레드가 write를 하는 경우 -> synchronized 사용
        - ref : https://nesoy.github.io/articles/2018-06/Java-volatile
    - strictfp
        - 플랫폼 간 부동소수점 연산의 결과를 동일하게 해주는 키워드

- 접근제어자
    - public > protected > (default) > private
    - private : 같은 클래스 내에서 접근
    - default : 같은 패키지 내에서 접근
    - protected : 상속관계에 있는 자손클래스에서 접근 가능
    - public : 접근 제한이 전혀 없음

- 생성자의 접근 제어자
    - 싱글톤 패턴에 사용
    - ```
      class Singleton {
          private static Singleton s = new Singleton();
          
          private Singleton() {
              ...
          }

          // 인스턴스를 생성하지 않고 호출할 수 있어야 하므로 static 이어야 함
          public static Singleton getInstance() {
              return s;
          }
      }

      class SingletonTest {

          public static void main(String[] args) {

              Singleton s = Singleton.getInstance();
          }
      }
      ```
      
- 참조변수의 형변환
    - ```
      class Car {
          ...
      }

      class Bus extends Car {
          ...
      }

      class Main {
         public  static void main(String[] args) {

             // 업 캐스팅
             Car car = new Bus();

             // 다운 캐스팅
             Bus bus = (Bus)new Car();
         }
      }
      ```

- instanceof 연산자
    - 상속받은 객체들을 구분할 수 있게 도와주는 연산자
    - 결과가 true : 검사한 타입으로 형 변환이 가능하다는 의미

- 바인딩
    - 참조변수와 인스턴스간 바인딩에 따라 호출되는 메서드가 달라짐

- 매개변수의 다형성
    - 매개변수를 상위 클래스로 해줌으로써, 서로 다른 하위 클래스를 인자로 받을 수 있는 다형성이 생김

- 추상 클래스
    - 직접적인 인스턴스 생성 불가
    - 설령 추상 메서드를 지니지 않았더라도 직접적인 인스턴스 생성이 불가능

- 추상 메서드
    - 상속받아서 오버라이딩해서 사용하기 위해 미완으로 남겨놓는 메서드
    - Remote로 쓰임?

- 인터페이스
    - 100% 추상 클래스
    - 모든 멤버변수는 public static final, 생략가능
    - 모든 메서드는 public abstract, 생략가능
    - 인터페이스는 인터페이스로부터만 상속 가능
    - 다중 상속 가능
    - 클래스에서 인터페이스를 implements 할 때, 인터페이스의 메서드 중 일부만을 구현한다면 abstract 클래스가 되어야 함
    - 장점
        - 개발시간 단축
        - 표준화
        - 독립적인 프로그래밍
        - 서로 관계없는 클래스간 관계 구축

- 인터페이스를 이용한 다형성
    - 매개변수가 인터페이스
        - 인터페이스로 구현한 인스턴스가 매개변수
    - 리턴값이 인터페이스
        - 메서드가 해당 인터페이스를 구현한 클래스의 인스턴스 반환

- 인터페이스의 이해
    - User(A) 와 Provider(B) 사이를 직접적인 관계에서 A-I-B의 간접적 관계로 변경
    - JDBC가 이렇게 되어있음

- 내부 클래스
    - 클래스 내에 선언되는 클래스
    - 외부 클래스와 긴밀한 관계
    - 내부 클래스는 외부 클래스 이외의 클래스에서는 잘 쓰이지 않는 관계
    - 장점
        - 내부 클래스에서 외부 클래스 멤버에 쉽게 접근 가능
        - 캡슐화
    - 내부 클래스 파일 생성명
        - ``` 
          class Outer {
              class InstanceInner {

              }

              static class StaticInner {

              }

              void myMethod() {
                  class LocalInner {

                  }
              }
          }
          ```
        - Outer.class, Outer$InstanceInner.class, Outer$StaticInner.class, Outer$1LocalInner.class

- 익명 클래스
    - 클래스 선언과 동시에 객체 생성
    - 오직 하나의 객체만 생성할 수 있는 일회용 클래스
    - new 조상클래스 명() { ... }
    - new 구현인터페이스 명() { ... }
    - 사용 이유?
        - 

# Chapter 08 예외처리 (exception handling)

- 프로그램 오류
    - 컴파일 에러 
    - 런타임 에러
    - 논리적 에러

- 런타임 에러
    - 에러(Error)
        - 치명적, 비정상적인 종료
        - 메모리 부족(OutOfMemoryError), 스택오버플로우(StackOverflowError)
    - 예외(Exception)
        - 수습 가능한 문제
        - 예외 계층도
        <img src="https://t1.daumcdn.net/cfile/tistory/217C6B4552AF12B432" style="cursor: pointer;max-width:100%;height:auto" width="650" height="600" filename="exception2.jpg" filemime="image/jpeg">
        - Exception 클래스
            - 사용자의 실수와 같은 외적인 요인에 의해 발생하는 예외
        - RuntimeException 클래스
            - 프로그래머의 실수로 발생하는 예외

- 예외 처리
    - 정의 : 프로그램 실행시 발생하는 예외에 대비한 코드를 작성
    - 목적 : 프로그램 비정상 종료를 막고, 정상적인 상태 유지

 - 모든 예외 클래스는 Exception 클래스의 자손
    - catch (Exception e) 로 어떤 종류의 예외라도 받을 수 있음
    
- printStackTrace(), getMessage()
    - 예외에 대한 정보 확인 메서드
    - printStackTrace() 를 통해 파일 입출력 가능

- 멀티 catch 블럭
    - ```
      try {

      } catch (ExceptionA e) {
        ...
      } catch (ExceptionB e) {
        ...
      }

      try {
        ...
      } catch (ExceptionA e | ExceptionB e) {
        ...
      }
      ```
    - 여러개의 catch 문을 하나로 합칠 수 있음
    - 단, Exception간 부모 자식 관계를 허용하지 않음

- 예외 발생 시키기
    - throw new Exception 으로 고의 예외 발생도 가능

- 메서드에 예외 선언
    - ```
      void method() throws Exception1, Exception2, ... {
        ...
      }
      ```
    - 메서드 내에서 발생할 가능성이 있는 예외를 메서드 선언부에 명시
    - 메서드 사용자에게 이에 대한 처리를 강제

- finally
    - 예외 발생여부 상관없이 실행되어야할 코드를 실행하는 블록
    - 예외 발생시, try -> catch -> finally 순
    - 예외 없을시, try -> finally 순

- try - with - resources
    - 입출력에 사용되는 클래스 중, 사용한 후 꼭 닫아서 자원 반환을 해줘야 할때 사용
    - try 블럭을 벗어나는 순간 자동으로 close() 호출
    - 이후, catch - finally 블럭 실행

- 사용자 정의 예외 만들기
    - ```
      class MyException extends Exception {
          MyException(String msg) {
              super(msg);
          }
      }
      ```
    - Exception 클래스 상속시, checked 예외
    - RuntimeException 클래스 상속시, unchecked 예외 (선택적, 최근 선호)

# Chapter 09 java.lang패키지와 유용한 클래스

- Object 클래스
    - equals(Object obj)
        - 두 객체의 같고 다름을 참조변수의 값으로 판단
    - hashcode()
        - 주소값 대신 주는 코드
        - 객체의 주소값을 이용하여 해시코드 만들어 반환
    - toString()
        - 클래스명@16진수_해시코드값 반환
    - clone()
        - 자신을 복제하여 새 인스턴스 생성
        - Cloneable 인터페이스를 구현한 클래스에서만 호출 가능
        - 얕은 복사이므로 깊은 복사가 필요하면 오버라이딩 필요
        - 예외처리 필요
    - getClass()
        - 자신이 속한 클래스의 "Class"객체를 반환
        - Class객체?
            - 클래스의 모든 정보 담고있음
            - 클래스당 1개
            - '클래스 로더'에 의해 메모리에 올라갈 때 자동 생성
                - 클래스 로더 : .class 파일을 메모리에 올림

- String 클래스 (p470 참고)
    - 덧셈(+) 연산자
        - 문자열 내부 변경이 불가능한 문자열 클래스
        - 인스턴스 내 문자열이 바뀌는 것이 아니라 새 문자열을 담은 String인스턴스 생성
        - 메모리 공간을 차지하므로 결합 횟수를 줄이는 것이 좋음
    - constructor
        - ```
          String s = new String("hello");
          ```
        - ```
          char[] ch = {'h','e','l','l','o'};
          String s = new String(ch);
          ```
        - ```
          StringBuffer sb = new StringBuffer("hello");
          String s = new String(sb);
          ```
    - charAt(int index)
        - 지정된 index에 있는 문자를 반환
        - ```
          String s = new String("hello");
          char ch = s.charAt(0);
          ```
    - compareTo(String str)
        - 입력된 문자열과 사전순서로 비교, 같으면 0, 이전 -1, 이후 양수 1
        - ```
          int i1 = "aaa".compareTo("aaa");   // return 0
          int i2 = "aaa".compareTo("bbb");   // return -1
          int i3 = "bbb".compareTo("aaa");   // return 1
          ```
    - concat(String str)
        - 입력된 문자열을 뒤에 덧붙임
        - ```
          String s1 = "hello";
          String s2 = s1.concat(" world");  // s2 = "hello world"
          ```
    - contains(String str)
        - 입력된 문자열이 포함되어있는지 확인, return true or false
        - ```
          String s = "hello";
          boolean b = s.contains("he");     // b = true
          ```
    - endsWith(String str)
        - 입력된 문자열로 끝나는지 검사, return true or false
        - ```
          String s = "hello.txt";
          boolean b = s.endsWith("txt");    // b = true
          ```
    - equals(String str)
        - 두 객체 안의 리터럴 내용이 같은지 판단, return true or false
        - ```
          String s = "hello";
          boolean b = s.equals("hello");    // b = true
          ```
    - equalsIgnoreCase(String str)
        - 두 객체 안의 리터럴 내용이 같은지 판단(대소문자 무시), return true or false
        - ```
          String s = "hello";
          boolean b = s.equalsIgnoreCase("hello");    // b = true
          ```
    - indexOf(char ch)
        - 주어진 문자가 문자열에 존재하는지 확인하여, 위치를 반환(없다면 -1)
        - ```
          String s = "hello";
          int index = s.indexOf('h');       // index = 0
          ```
    - indexOf(char ch, int pos)
        - 주어진 문자가 문자열 해당 위치부터 존재하는지 확인하여, 위치를 반환(없다면 -1)
        - ```
          String s = "hello";
          int index = s.indexOf('e',0);       // index = 1
          ```
    - indexOf(String str)
        - 주어진 문자열이 문자열에 존재하는지 확인하여, 시작 위치를 반환(없다면 -1)
        - ```
          String s = "hello";
          int index = s.indexOf('el');       // index = 1
          ```
    - intern()
        - 문자열을 상수풀에 등록하고, 이미 같은 내용이 있을 경우 해당 문자열 주소 반환
    - String replace(char old, char new)
        - 문자열중 old를 new로 교체하려 반환
        - ```
          String s1 = "hello"
          String s2 = s1.replace('o','l');  // s2 = "helll"
          ``` 
    - hashcode()
        - 리터럴의 해시코드를 반환
    - toString()
        - 문자열 반환
    - split()
        - 문자얄 사이에 구분자 넣어서 분해
    - join()
        - 문자열 사이에 구분자 넣어서 결합

- StringBuffer 클래스
    - 멀티쓰레드에 안전하도록 동기화(thread safe)
    - 동기화 기능이 들어가므로 StringBuffer의 성능이 떨어짐
    - 문자열 내부 변경이 가능한 문자열 클래스
    - 문자열간 결합이나 추출 등 문자열을 다루는 작업이 많이 필요한 경우 사용

- StringBuilder 클래스
    - StringBuffer와는 다르게 쓰레드 동기화 기능이 없음, 나머지는 같음

- C에서는 문자열 끝에 널문자, Java에서는 길이정보 따로 보관(널문자 사용 X)

- 보편적인 초기화
    - String str = null (X) -> String str = "";
    - char ch = '\u0000'(X) -> char ch = '';

- 문자 인코딩 변환
    - getBytes(String charset)

- 기본값을 String으로 변환
    - 숫자 + ""
    - String.valueOf(int i)     // 성능 우위

- String으 기본값으로 변환
    - int i = Integer.parseInt("100")   // parse 시리즈가 성능 우위
    - int j = Integer.valueOf("100")    // 

- 기본값2String / String2기본값 변환에 대한 ref : p474

- Math 클래스
    - sqrt()
        - 제곱근 계산
    - pow()
        - n제곱 계산

- StaticMath 클래스 
    - Math는 OS의존적 계산(OS따라 성능차이 및 결과차이 발생)
    - StaticMath는 성능을 포기하고 OS독립적으로 실행 = 같은 성능 및 결과

- Wrapper 클래스
    - 기본형 변수를 객체로 다뤄야할 때 사용되는 클래스
        - 매개변수로 객체를 요구할 때
        - 기본형 값이 아닌 객체로 저장해야할 때
        - 객체간 비교할 때
        - ...
    - 종류
        - Boolean
        - Character
        - Byte
        - Short
        - Integer
        - Long
        - Float
        - Double

- Number 클래스
    - Boolean, Character 를 제외한 wrapper 클래스의 부모 클래스

- 오토박싱 & 언박싱
    - 오토박식 : 기본형 값을 래퍼 클래스의 객체로 자동 변환해 주는 것
    - 언박싱 : 래퍼 클래스의 객체를 기본형 값으로 자동 변환해 주는 것

