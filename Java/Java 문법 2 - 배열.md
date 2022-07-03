# 📌Java 문법 2 - 배열

1차원배열, 2차원 배열

---------------------------



### ✨배열

- 같은 자료형의 데이터들의 모임

- 크기가 고정되어 있어 한 번 생성된 배열은 크기를 바꿀 수 없음

- 배열로 선언된 변수들은 연속된 데이터 공간에 할당됨

- 배열의 요소값은 배열 이름과 인덱스를 이용하여 접근

- 배열을 객체로 취급

- `배열유형 배열이름[]` 또는 `배열유형[] 배열이름`

  - 예) `int prime[]`, `int[] prime`

- 배열유형은 기본형과 참조형 모두 가능

- 배열이 생성되면 자동적으로 배열요소는 기본값으로 초기화됨

  | int     | 0        |
  | ------- | -------- |
  | boolean | false    |
  | char    | '\u0000' |
  | 참조형  | null     |

- 예시

  ```java
  public class Test {
      public static void main(String[] args) {
          int[] score = new int[100];
          score[0] = 90;
          score[1] = 95;
          // ...
          score[99] = 100;
      }
  }
  
  // int[]: int배열의 주소를 담을 수 있음
  // 100명의 학생 점수를 담는 int[]
  // 첫 번째 학생의 점수가 90 → score[0] = 90;
  // 백 번째 학생의 점수가 100 → score[99] = 100;
  ```

  ```java
  package Test;
  
  import java.util.Arrays;
  
  public class Test {
      public static void main(String[] args) {
          int[] score = new int[5];
          score[0] = 10;
          score[1] = 12;
          score[2] = 17;
          score[3] = 20;
          score[4] = 1;
          
          // score에 들어있는 데이터 중 가장 큰 데이터를 찾고
          // 해당 데이터를 첫 번째(인덱스 0) 데이터와 교환하기
          
          int max = score[0];
          int maxIdx = 0;
          for (int i = 0; i < score.length; i++) {
              if (max < score[i]) {
                  max = score[i];
                  maxIdx = i;
              }
          }
          
          int tmp = score[0];
          score[0] = max;  // 또는 score[0] = score[maxIdx];
          score[maxIdx] = tmp; 
          
          System.out.println(score[0]);  // 20
          System.out.println(score[3]);  // 10
          
          
          // for
          for (int j = 0; j < score.length; j++) {
          	System.out.println(score[j]);
          }
          // 20
          // 12
          // 17
          // 10
          // 1
          
          
          // for-each
          for (int n : score) {
          	System.out.println(n);
          }
          // 20
          // 12
          // 17
          // 10
          // 1
          
          
          // Arrays 배열값 확인
          System.out.println(Arrays.toString(score));  // [20, 12, 17, 10, 1]
      }
  }
  ```





### ✨2차원 배열

- `[]`의 개수가 배열의 차원 수를 나타냄

  - `[]`일 경우 1차원, `[][]`일 경우 2차원

- `배열유형 배열이름[][]` 또는 `배열유형[][] 배열이름`

  - 예) `int prime[][]`, `int[][] prime`

- `배열유형[][] 배열이름 = new 배열유형[1차원배열개수][1차원배열크기];`

  또는 `배열유형[][] 배열이름 = new 배열유형[1차원배열개수][];`

- 예시

  ```java
  package Test;
  
  import java.util.Arrays;
  
  public class Test {
  	public static void main(String[] args) {
  //		int[][] arr = new int[3][];
  //		arr[0] = new int[2];
  //		arr[1] = new int[2];
  //		arr[2] = new int[2];
  
  		int[][] arr = new int[3][2];  // 위와 같음
          
  		arr[0][1] = 10;  // [[0, 10], [0, 0], [0, 0]]
  	}
  }
  ```





### ✨초기화

- `{}`를 활용: 배열 선언시에만 설정 가능
  - 1차원 배열: `배열유형[] 배열이름 = {값, ..., 값};`
    - 예) `int[] prime = {1, 2, 3};`
  - 2차원 배열: `배열유형[][] 배열이름 = {{값1, 값2}, {값3, 값4}};`
    - 예) `int[][] arr = {{1, 2}, {3, 4}};`
- `new 배열타입[] {값, ...};`
  - 예) `int[] prime = new int[] {1, 2};`
