
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