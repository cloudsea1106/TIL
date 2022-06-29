# 📌Java 문법 1 - 기본문법, 제어문

출력, 데이터, 연산, 조건, 반복

--------------------------------------------------------------



### ✨메모리의 단위

- bit
  - 0, 1
- 1byte = 8bit





### ✨출력문

- print
  - 줄바꿈 X
- println
  - 줄바꿈 O
- printf
  - %d: 정수
  - %f: 실수
  - %s: 문자열

- 예시

  ```java
  System.out.print("Hello World\n");
  System.out.println("Welcome");
  System.out.println("\\");
  // Hello World
  // Welcome
  // \
  ```

  ```java
  // 한줄 주석입니다.
  /* 여러줄 주석입니다.
  * 왼쪽 별은 있어도 되고 없어도 됨! 주석임을 표시
  * 끝날때는 있어야함
  * 주석 단축키 ctrl shift c
  */
  ```

  ```java
  // 실행 단축키는 ctrl F11
  // ctrl shift f 는 정렬
  // ctrl space 자동완성기능
  ```

  ```java
  System.out.printf("오늘은 %d일입니다.\n", 26); //정수(10진수)
  System.out.printf("%o\n", 10);  //정수(8진수)
  System.out.printf("%x\n", 10);  //정수(16진수)
  System.out.printf("%4d\n", 10);  //4칸확보 후 오른쪽부터 차지
  System.out.printf("%-4d\n", 10);  //4칸확보 후 왼쪽부터 차지
  System.out.printf("%04d\n", 10);  //4칸확보 후 오른쪽부터 차지, 빈공간은 0
  System.out.printf("%f\n", 10.1);  //실수(소수점여섯째자리까지)
  System.out.printf("%.2f\n", 10.1);  //실수(소수점둘째자리까지)
  System.out.printf("%s\n", "홍길동");  //문자열
  System.out.printf("%s의 나이는 %d입니다.\n", "홍길동", 15);
  
  // 오늘은 26일입니다.
  // 12
  // a
  //   10
  // 10  
  // 0010
  // 10.100000
  // 10.10
  // 홍길동
  // 홍길동의 나이는 15입니다.
  ```





### ✨변수

- 데이터를 저장할 메모리의 위치를 나타내는 이름

- 변수 선언+초기화

  - 자료형 변수명; (선언)
    - `int age;`
  - 변수명 = 값; (초기화)
    - `age = 15;`

- 변수 선언과 초기화를 동시에

  - 자료형 변수명 = 값;

    `int age = 15;`

- 변수명 규칙

  - 대소문자 구분
  - 공백X
  - 문자와 숫자, '$', '_' 사용 가능
  - 첫 번째 문자는 숫자로 시작할 수 없음
  - 예약어 사용X

- 변수명 관례

  - 첫 번째 문자는 소문자인 명사
  - 여러 단어로 구성된 변수는 두 번째 단어부터 첫글자를 대문자로 사용 (카멜케이스)
    - `javaName`





### ✨자료형 타입

- 기본자료형과 참조자료형
- 기본자료형

|  타입  | 세부타입 | 데이터형 | 크기  |    기본값    |
| :----: | :------: | :------: | :---: | :----------: |
| 논리형 |          | boolean  | 1byte |    false     |
| 문자형 |          |   char   | 2byte | null(\u0000) |
| 숫자형 |  정수형  |   byte   | 1byte |   (byte)0    |
|        |          |  short   | 2byte |   (short)0   |
|        |          |   int    | 4byte |      0       |
|        |          |   long   | 8byte |      0L      |
|        |  실수형  |  float   | 4byte |     0.0f     |
|        |          |  double  | 8byte |     0.0d     |





### ✨데이터 형변환

- 묵시적(암묵적): Implicit Casting
  - 범위가 넓은 데이터 형에 범위가 좁은 데이터 형을 대입
  - `byte a = 10;` `int b = a;`

- 명시적: Explicit Casting
  - 범위가 좁은 데이터 형에 넓은 데이터 형을 대입
  - 형변환 연산자 사용 `(타입) 값;`
  - `int a = 10;` `byte b = a;` (X)
  - `int a = 10;` `byte b = (byte) a;` (O)





### ✨연산자

- 증감 연산자

  - ++op (선행처리), op++ (후행처리)

    - 1증가

      ```java
      int num = 10;
      System.out.println(++num);
      // num = num + 1
      // System.out.println(num);
      // num에 num+1 할당하고 num 출력
      ---------------------------------
      int num = 10;
      System.out.println(num++);
      // System.out.println(num);
      // num = num + 1
      // num을 출력하고 num에 num+1 할당
      ```

  - --op (선행처리), op--(후행처리)

    - 1감소

      ```java
      int a = 100;
      int b = --a;
      System.out.println(b);  // 99
      System.out.println(a);  // 99
      ---------------------------------
      int a = 100;
      int b = a--;
      System.out.println(b);  // 100
      System.out.println(a);  // 99
      ```



- 산술 연산자
  - +, -, *, /, %
  - / 는 몫, % 는 나머지



- 쉬프트 연산자

  - `>>`

    - 앞의 피연산자 비트 열을 뒤 피연산자만큼 오른쪽으로 이동
    - 이동에 따른 빈 공간은 음수는 1, 양수는 0으로 채움

  - <<

    - 앞의 피연산자 비트 열을 뒤 피연산자만큼 왼쪽으로 이동
    - 이동에 따른 빈 공간은 0으로 채움

  - `>>>`

    - 앞의 피연산자 비트 열을 뒤 피연산자만큼 오른쪽으로 이동
    - 이동에 따른 빈 공간은 0으로 채움

  - 예시

    ```java
    int a = 10;
    // 2진수 a: 1010
    // 10진수 a: (2**3)*1 + (2**2)*0 + (2**1)*1 + (2**0)*0 = 8 + 2 = 10
    
    int b = a<<1;
    // 2진수 b: 10100
    // 10진수 b: (2**4)*1 + (2**3)*0 + (2**2)*1 + (2**1)*0 + (2**0)*0 = 16 + 4 = 20
    // *2 와 동일
    
    int c = a>>1;
    // 2진수 c: 0101
    // 10진수 c: 부호비트(양수) (2**2)*1 + (2**1)*0 + (2**0)*1 = 4 + 1 = 5
    // /2 와 동일
    
    // *2, /2 에 비해 속도가 빠름
    ```



- 비교 연산자

  - true / false 로 답이 나옴

  - `>, >=, <, <=`

  - ==

    ```java
    boolean a = ((10 % 2) == 0);
    System.out.println(a);  // true
    ```

  - !=

  - instanceof

    - 객체의 타입을 비교



- 비트 연산자

  - &

    - AND

    - 두 피연산자 비트값이 모두 1인 경우만 1, 나머지는 0

  - |

    - OR

    - 두 피연산자 비트값이 모두 0인 경우만 0, 나머지는 1

  - ^

    - XOR
    - 두 피연산자 비트값이 서로 다르면 1, 같으면 0

  - ~
    - 비트 반전 → 1의 보수



- 논리연산자

  - 피연산자와 결과 모두 boolean

  - &

    - `A & B`

    - A와 B가 참일 경우만 참 반환

  - |

    - `A | B`
    - A 또는 B 둘 중 하나가 참일 경우 참 반환

  - ^

    - `true ^ false` → `true`
    - `true ^ true` → `false`
    - 두 피연산자가 서로 다를 경우만 참, 같으면 거짓 반환

  - !

    - `!A`

    - A가 참이면 거짓, A가 거짓이면 참 반환

  - &&

    - `A && B`
    - A와 B가 참일 경우만 참 반환
    - A가 거짓일 경우 B는 실행X

  - ||

    - `A || B`
    - A 또는 B 둘 중 하나가 참일 경우 참 반환
    - A가 참일 경우 B는 실행 X



- 삼항 연산자 (조건 연산자)
  - 조건식 ? 수식1 : 수식2;
  - 수식1: 조건식의 결과가 참일 때 수행
  - 수식2: 조건식의 결과가 거짓일 때 수행



- 배정 연산자 (대입 연산자, 할당 연산자)
  - *=, /=, %=, +=, -=





### ✨조건문

- if
  - 실행 문장이 2개 이상이면 {} 블록으로 처리	
  
  - {} 블록 안에 또 if문이 들어갈 수 있음
  
  - 예시
  
    ```java
    int score = 85;
    if (score > 90)
        System.out.println("A");
    else if (score > 80)
        System.out.println("B");
    else if (score > 70)
        System.out.println("C");
    else
        System.out.println("F");
    // B
    ```
  
- switch

  - 예시

    ```java
    int num = 1;
    switch (num) {
        case 1:
            System.out.println(1);
            break;
        case 2:
            System.out.println(2);
            break;
        default:
            System.out.println(3);
    }
    ```

  - break문 없이 사용가능, 없을 경우 break를 찾을 때까지 선택된 case문 아래의 모든 문장 실행





### ✨반복문

- while

  - 조건을 만족하는 동안 명령문 실행

  - 예시

    ```java
    public class Test {
    	public static void main(String[] args) {
    		int n = 5;
    		while (n < 10) {
    			System.out.println(n);
    			n++;
    		}
    	}
    }
    
    // 5
    // 6
    // 7
    // 8
    // 9
    ```

- for

  - 조건을 만족하는 동안 명령문 실행

  - 예시

    ```java
    public class Test {
    	public static void main(String[] args) {
    		for (int i = 5; i < 10; i++) {
    			System.out.println(i);
    		}
    	}
    }
    
    // 5
    // 6
    // 7
    // 8
    // 9
    ```

- do ~ while

  - 조건을 나중에 평가

  - while 블록이 적어도 한 번은 반드시 실행됨

  - 예시

    ```java
    public class Test {
    	public static void main(String[] args) {
    		int a = 1, b = 2;
    		do {
    			System.out.println("반드시 실행");
    		} while (a > b);
    	}
    }
    
    // 반드시 실행  ← while 조건이 거짓이므로 한 번만 실행되고 중단
    ```

