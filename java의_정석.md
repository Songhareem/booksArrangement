
## Chapter 04 조건문 반복문

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

## Chapter 05 배열

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

## Chapter 06 객체지향 프로그래밍 I

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
    
