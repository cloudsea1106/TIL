# ๐Java ๋ฌธ๋ฒ 1 - ๊ธฐ๋ณธ๋ฌธ๋ฒ, ์ ์ด๋ฌธ

์ถ๋ ฅ, ๋ฐ์ดํฐ, ์ฐ์ฐ, ์กฐ๊ฑด, ๋ฐ๋ณต

--------------------------------------------------------------



### โจ๋ฉ๋ชจ๋ฆฌ์ ๋จ์

- bit
  - 0, 1
- 1byte = 8bit





### โจ์ถ๋ ฅ๋ฌธ

- print
  - ์ค๋ฐ๊ฟ X
- println
  - ์ค๋ฐ๊ฟ O
- printf
  - %d: ์ ์
  - %f: ์ค์
  - %s: ๋ฌธ์์ด

- ์์

  ```java
  System.out.print("Hello World\n");
  System.out.println("Welcome");
  System.out.println("\\");
  // Hello World
  // Welcome
  // \
  ```

  ```java
  // ํ์ค ์ฃผ์์๋๋ค.
  /* ์ฌ๋ฌ์ค ์ฃผ์์๋๋ค.
  * ์ผ์ชฝ ๋ณ์ ์์ด๋ ๋๊ณ  ์์ด๋ ๋จ! ์ฃผ์์์ ํ์
  * ๋๋ ๋๋ ์์ด์ผํจ
  * ์ฃผ์ ๋จ์ถํค ctrl shift c
  */
  ```

  ```java
  // ์คํ ๋จ์ถํค๋ ctrl F11
  // ctrl shift f ๋ ์ ๋ ฌ
  // ctrl space ์๋์์ฑ๊ธฐ๋ฅ
  ```

  ```java
  System.out.printf("์ค๋์ %d์ผ์๋๋ค.\n", 26); //์ ์(10์ง์)
  System.out.printf("%o\n", 10);  //์ ์(8์ง์)
  System.out.printf("%x\n", 10);  //์ ์(16์ง์)
  System.out.printf("%4d\n", 10);  //4์นธํ๋ณด ํ ์ค๋ฅธ์ชฝ๋ถํฐ ์ฐจ์ง
  System.out.printf("%-4d\n", 10);  //4์นธํ๋ณด ํ ์ผ์ชฝ๋ถํฐ ์ฐจ์ง
  System.out.printf("%04d\n", 10);  //4์นธํ๋ณด ํ ์ค๋ฅธ์ชฝ๋ถํฐ ์ฐจ์ง, ๋น๊ณต๊ฐ์ 0
  System.out.printf("%f\n", 10.1);  //์ค์(์์์ ์ฌ์ฏ์งธ์๋ฆฌ๊น์ง)
  System.out.printf("%.2f\n", 10.1);  //์ค์(์์์ ๋์งธ์๋ฆฌ๊น์ง)
  System.out.printf("%s\n", "ํ๊ธธ๋");  //๋ฌธ์์ด
  System.out.printf("%s์ ๋์ด๋ %d์๋๋ค.\n", "ํ๊ธธ๋", 15);
  
  // ์ค๋์ 26์ผ์๋๋ค.
  // 12
  // a
  //   10
  // 10  
  // 0010
  // 10.100000
  // 10.10
  // ํ๊ธธ๋
  // ํ๊ธธ๋์ ๋์ด๋ 15์๋๋ค.
  ```





### โจ๋ณ์

- ๋ฐ์ดํฐ๋ฅผ ์ ์ฅํ  ๋ฉ๋ชจ๋ฆฌ์ ์์น๋ฅผ ๋ํ๋ด๋ ์ด๋ฆ

- ๋ณ์ ์ ์ธ+์ด๊ธฐํ

  - ์๋ฃํ ๋ณ์๋ช; (์ ์ธ)
    - `int age;`
  - ๋ณ์๋ช = ๊ฐ; (์ด๊ธฐํ)
    - `age = 15;`

- ๋ณ์ ์ ์ธ๊ณผ ์ด๊ธฐํ๋ฅผ ๋์์

  - ์๋ฃํ ๋ณ์๋ช = ๊ฐ;

    `int age = 15;`

- ๋ณ์๋ช ๊ท์น

  - ๋์๋ฌธ์ ๊ตฌ๋ถ
  - ๊ณต๋ฐฑX
  - ๋ฌธ์์ ์ซ์, '$', '_' ์ฌ์ฉ ๊ฐ๋ฅ
  - ์ฒซ ๋ฒ์งธ ๋ฌธ์๋ ์ซ์๋ก ์์ํ  ์ ์์
  - ์์ฝ์ด ์ฌ์ฉX

- ๋ณ์๋ช ๊ด๋ก

  - ์ฒซ ๋ฒ์งธ ๋ฌธ์๋ ์๋ฌธ์์ธ ๋ช์ฌ
  - ์ฌ๋ฌ ๋จ์ด๋ก ๊ตฌ์ฑ๋ ๋ณ์๋ ๋ ๋ฒ์งธ ๋จ์ด๋ถํฐ ์ฒซ๊ธ์๋ฅผ ๋๋ฌธ์๋ก ์ฌ์ฉ (์นด๋ฉ์ผ์ด์ค)
    - `javaName`





### โจ์๋ฃํ ํ์

- ๊ธฐ๋ณธ์๋ฃํ๊ณผ ์ฐธ์กฐ์๋ฃํ
- ๊ธฐ๋ณธ์๋ฃํ

|  ํ์  | ์ธ๋ถํ์ | ๋ฐ์ดํฐํ | ํฌ๊ธฐ  |    ๊ธฐ๋ณธ๊ฐ    |
| :----: | :------: | :------: | :---: | :----------: |
| ๋ผ๋ฆฌํ |          | boolean  | 1byte |    false     |
| ๋ฌธ์ํ |          |   char   | 2byte | null(\u0000) |
| ์ซ์ํ |  ์ ์ํ  |   byte   | 1byte |   (byte)0    |
|        |          |  short   | 2byte |   (short)0   |
|        |          |   int    | 4byte |      0       |
|        |          |   long   | 8byte |      0L      |
|        |  ์ค์ํ  |  float   | 4byte |     0.0f     |
|        |          |  double  | 8byte |     0.0d     |





### โจ๋ฐ์ดํฐ ํ๋ณํ

- ๋ฌต์์ (์๋ฌต์ ): Implicit Casting
  - ๋ฒ์๊ฐ ๋์ ๋ฐ์ดํฐ ํ์ ๋ฒ์๊ฐ ์ข์ ๋ฐ์ดํฐ ํ์ ๋์
  - `byte a = 10;` `int b = a;`

- ๋ช์์ : Explicit Casting
  - ๋ฒ์๊ฐ ์ข์ ๋ฐ์ดํฐ ํ์ ๋์ ๋ฐ์ดํฐ ํ์ ๋์
  - ํ๋ณํ ์ฐ์ฐ์ ์ฌ์ฉ `(ํ์) ๊ฐ;`
  - `int a = 10;` `byte b = a;` (X)
  - `int a = 10;` `byte b = (byte) a;` (O)





### โจ์ฐ์ฐ์

- ์ฆ๊ฐ ์ฐ์ฐ์

  - ++op (์ ํ์ฒ๋ฆฌ), op++ (ํํ์ฒ๋ฆฌ)

    - 1์ฆ๊ฐ

      ```java
      int num = 10;
      System.out.println(++num);
      // num = num + 1
      // System.out.println(num);
      // num์ num+1 ํ ๋นํ๊ณ  num ์ถ๋ ฅ
      ---------------------------------
      int num = 10;
      System.out.println(num++);
      // System.out.println(num);
      // num = num + 1
      // num์ ์ถ๋ ฅํ๊ณ  num์ num+1 ํ ๋น
      ```

  - --op (์ ํ์ฒ๋ฆฌ), op--(ํํ์ฒ๋ฆฌ)

    - 1๊ฐ์

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



- ์ฐ์  ์ฐ์ฐ์
  - +, -, *, /, %
  - / ๋ ๋ชซ, % ๋ ๋๋จธ์ง



- ์ฌํํธ ์ฐ์ฐ์

  - `>>`

    - ์์ ํผ์ฐ์ฐ์ ๋นํธ ์ด์ ๋ค ํผ์ฐ์ฐ์๋งํผ ์ค๋ฅธ์ชฝ์ผ๋ก ์ด๋
    - ์ด๋์ ๋ฐ๋ฅธ ๋น ๊ณต๊ฐ์ ์์๋ 1, ์์๋ 0์ผ๋ก ์ฑ์

  - <<

    - ์์ ํผ์ฐ์ฐ์ ๋นํธ ์ด์ ๋ค ํผ์ฐ์ฐ์๋งํผ ์ผ์ชฝ์ผ๋ก ์ด๋
    - ์ด๋์ ๋ฐ๋ฅธ ๋น ๊ณต๊ฐ์ 0์ผ๋ก ์ฑ์

  - `>>>`

    - ์์ ํผ์ฐ์ฐ์ ๋นํธ ์ด์ ๋ค ํผ์ฐ์ฐ์๋งํผ ์ค๋ฅธ์ชฝ์ผ๋ก ์ด๋
    - ์ด๋์ ๋ฐ๋ฅธ ๋น ๊ณต๊ฐ์ 0์ผ๋ก ์ฑ์

  - ์์

    ```java
    int a = 10;
    // 2์ง์ a: 1010
    // 10์ง์ a: (2**3)*1 + (2**2)*0 + (2**1)*1 + (2**0)*0 = 8 + 2 = 10
    
    int b = a<<1;
    // 2์ง์ b: 10100
    // 10์ง์ b: (2**4)*1 + (2**3)*0 + (2**2)*1 + (2**1)*0 + (2**0)*0 = 16 + 4 = 20
    // *2 ์ ๋์ผ
    
    int c = a>>1;
    // 2์ง์ c: 0101
    // 10์ง์ c: ๋ถํธ๋นํธ(์์) (2**2)*1 + (2**1)*0 + (2**0)*1 = 4 + 1 = 5
    // /2 ์ ๋์ผ
    
    // *2, /2 ์ ๋นํด ์๋๊ฐ ๋น ๋ฆ
    ```



- ๋น๊ต ์ฐ์ฐ์

  - true / false ๋ก ๋ต์ด ๋์ด

  - `>, >=, <, <=`

  - ==

    ```java
    boolean a = ((10 % 2) == 0);
    System.out.println(a);  // true
    ```

  - !=

  - instanceof

    - ๊ฐ์ฒด์ ํ์์ ๋น๊ต



- ๋นํธ ์ฐ์ฐ์

  - &

    - AND

    - ๋ ํผ์ฐ์ฐ์ ๋นํธ๊ฐ์ด ๋ชจ๋ 1์ธ ๊ฒฝ์ฐ๋ง 1, ๋๋จธ์ง๋ 0

  - |

    - OR

    - ๋ ํผ์ฐ์ฐ์ ๋นํธ๊ฐ์ด ๋ชจ๋ 0์ธ ๊ฒฝ์ฐ๋ง 0, ๋๋จธ์ง๋ 1

  - ^

    - XOR
    - ๋ ํผ์ฐ์ฐ์ ๋นํธ๊ฐ์ด ์๋ก ๋ค๋ฅด๋ฉด 1, ๊ฐ์ผ๋ฉด 0

  - ~
    - ๋นํธ ๋ฐ์  โ 1์ ๋ณด์



- ๋ผ๋ฆฌ์ฐ์ฐ์

  - ํผ์ฐ์ฐ์์ ๊ฒฐ๊ณผ ๋ชจ๋ boolean

  - &

    - `A & B`

    - A์ B๊ฐ ์ฐธ์ผ ๊ฒฝ์ฐ๋ง ์ฐธ ๋ฐํ

  - |

    - `A | B`
    - A ๋๋ B ๋ ์ค ํ๋๊ฐ ์ฐธ์ผ ๊ฒฝ์ฐ ์ฐธ ๋ฐํ

  - ^

    - `true ^ false` โ `true`
    - `true ^ true` โ `false`
    - ๋ ํผ์ฐ์ฐ์๊ฐ ์๋ก ๋ค๋ฅผ ๊ฒฝ์ฐ๋ง ์ฐธ, ๊ฐ์ผ๋ฉด ๊ฑฐ์ง ๋ฐํ

  - !

    - `!A`

    - A๊ฐ ์ฐธ์ด๋ฉด ๊ฑฐ์ง, A๊ฐ ๊ฑฐ์ง์ด๋ฉด ์ฐธ ๋ฐํ

  - &&

    - `A && B`
    - A์ B๊ฐ ์ฐธ์ผ ๊ฒฝ์ฐ๋ง ์ฐธ ๋ฐํ
    - A๊ฐ ๊ฑฐ์ง์ผ ๊ฒฝ์ฐ B๋ ์คํX

  - ||

    - `A || B`
    - A ๋๋ B ๋ ์ค ํ๋๊ฐ ์ฐธ์ผ ๊ฒฝ์ฐ ์ฐธ ๋ฐํ
    - A๊ฐ ์ฐธ์ผ ๊ฒฝ์ฐ B๋ ์คํ X



- ์ผํญ ์ฐ์ฐ์ (์กฐ๊ฑด ์ฐ์ฐ์)
  - ์กฐ๊ฑด์ ? ์์1 : ์์2;
  - ์์1: ์กฐ๊ฑด์์ ๊ฒฐ๊ณผ๊ฐ ์ฐธ์ผ ๋ ์ํ
  - ์์2: ์กฐ๊ฑด์์ ๊ฒฐ๊ณผ๊ฐ ๊ฑฐ์ง์ผ ๋ ์ํ



- ๋ฐฐ์  ์ฐ์ฐ์ (๋์ ์ฐ์ฐ์, ํ ๋น ์ฐ์ฐ์)
  - *=, /=, %=, +=, -=





### โจ์กฐ๊ฑด๋ฌธ

- if
  - ์คํ ๋ฌธ์ฅ์ด 2๊ฐ ์ด์์ด๋ฉด {} ๋ธ๋ก์ผ๋ก ์ฒ๋ฆฌ	
  
  - {} ๋ธ๋ก ์์ ๋ if๋ฌธ์ด ๋ค์ด๊ฐ ์ ์์
  
  - ์์
  
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

  - ์์

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

  - break๋ฌธ ์์ด ์ฌ์ฉ๊ฐ๋ฅ, ์์ ๊ฒฝ์ฐ break๋ฅผ ์ฐพ์ ๋๊น์ง ์ ํ๋ case๋ฌธ ์๋์ ๋ชจ๋  ๋ฌธ์ฅ ์คํ





### โจ๋ฐ๋ณต๋ฌธ

- while

  - ์กฐ๊ฑด์ ๋ง์กฑํ๋ ๋์ ๋ช๋ น๋ฌธ ์คํ

  - ์์

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

  - ์กฐ๊ฑด์ ๋ง์กฑํ๋ ๋์ ๋ช๋ น๋ฌธ ์คํ

  - ์์

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

  - ์กฐ๊ฑด์ ๋์ค์ ํ๊ฐ

  - while ๋ธ๋ก์ด ์ ์ด๋ ํ ๋ฒ์ ๋ฐ๋์ ์คํ๋จ

  - ์์

    ```java
    public class Test {
    	public static void main(String[] args) {
    		int a = 1, b = 2;
    		do {
    			System.out.println("๋ฐ๋์ ์คํ");
    		} while (a > b);
    	}
    }
    
    // ๋ฐ๋์ ์คํ  โ while ์กฐ๊ฑด์ด ๊ฑฐ์ง์ด๋ฏ๋ก ํ ๋ฒ๋ง ์คํ๋๊ณ  ์ค๋จ
    ```

