# MySQL WITH, WITH RECURSIVE



### [목차]

- [WITH: Common Table Expressions (CTE)](#WITH-Common-Table-Expressions-CTE)
  - [WITH](#WITH)
  - [WITH RECURSIVE](#WITH-RECURSIVE)





### WITH: Common Table Expressions (CTE)

- [공식문서](https://dev.mysql.com/doc/refman/8.0/en/with.html)



##### WITH

- SQL문에서 존재하는 임시 테이블(결과 셋), 해당 SQL문에서 여러 번 참조될 수 있음
- 셀프참조(재귀-WITH RECURSIVE)가 가능하고, 다른 CTE를 참조할 수도 있음
- 테이블 생성 권한이 필요하지 않음

- 기본 구조

  ```mysql
  WITH [RECURSIVE] cte_name AS (
  	SELECT -
      [UNION ALL]
      [SELECT -]
      [WHERE]
  )
  ```

- 예시

  ```mysql
  # WITH절에서 CTE인 cte1과 cte2를 만들고, 이를 WITH절 다음의 SELECT문에서 참조함
  
  WITH
    cte1 AS (SELECT a, b FROM table1),
    cte2 AS (SELECT c, d FROM table2)
  SELECT b, d FROM cte1 JOIN cte2
  WHERE cte1.a = cte2.c;
  ```

  ```mysql
  WITH cte (n) AS
  (
    SELECT 1  -- 1을 한 번 출력
    UNION ALL
    SELECT 2 FROM db.table_name  -- 2를 table_name 테이블의 데이터 행 수만큼 출력
  )
  SELECT * FROM cte;
  ```

- 컬럼명

  - CTE명 다음에 괄호로 묶인 것이 컬럼명

    ```mysql
    WITH cte (col1, col2) AS
    (
      SELECT 1, 2
      UNION ALL
      SELECT 3, 4
    )
    SELECT col1, col2 FROM cte;
    ```

    | col1 | col2 |
    | ---- | ---- |
    | 1    | 2    |
    | 3    | 4    |

  - CTE명 뒤에 괄호로 컬럼명을 나타내지 않으면, 서브쿼리의 첫 번째 SELECT문으로 정함

    ```mysql
    WITH cte AS
    (
      SELECT 1 AS col1, 2 AS col2
      UNION ALL
      SELECT 3, 4
    )
    SELECT col1, col2 FROM cte;
    ```

    | col1 | col2 |
    | ---- | ---- |
    | 1    | 2    |
    | 3    | 4    |

    ```mysql
    WITH cte AS
    (
      SELECT 1, 2
      UNION ALL
      SELECT 3, 4
    )
    SELECT * FROM cte;
    ```

    | 1    | 2    |
    | ---- | ---- |
    | 1    | 2    |
    | 3    | 4    |

- 하나의 CTE는 같은 WITH절 내 앞서 정의된 CTE는 참조 가능, 뒤에 정의된 CTE는 참조 불가능

  ```mysql
  # 가능
  WITH
    cte1 AS (SELECT 1 AS col1, 2 AS col2),
    cte2 AS (SELECT col1 FROM cte1)
  
  select * from cte2;
  
  # 불가능
  WITH
    cte1 AS (SELECT col1 FROM cte2),
    cte2 AS (SELECT 1 AS col1, 2 AS col2)
  
  select * from cte1;
  ```

- 다음 상황에서 WITH절 사용 가능

  - SELECT, UPDATE, DELETE문의 시작

    ```mysql
    WITH ... SELECT ...
    WITH ... UPDATE ...
    WITH ... DELETE ...
    ```

  - 서브쿼리의 시작

    ```mysql
    SELECT ... WHERE id IN (WITH ... SELECT ...) ...
    SELECT * FROM (WITH ... SELECT ...) AS dt ...
    ```

  - SELECT문을 포함하는 SQL문의 SELECT 바로 앞

    ```mysql
    INSERT ... WITH ... SELECT ...
    REPLACE ... WITH ... SELECT ...
    CREATE TABLE ... WITH ... SELECT ...
    CREATE VIEW ... WITH ... SELECT ...
    DECLARE CURSOR ... WITH ... SELECT ...
    EXPLAIN ... WITH ... SELECT ...
    ```

- 같은 레벨에서는 하나의 WITH절만 사용 가능

  ```mysql
  # 가능 (하나의 WITH, 콤마로 CTE 구분)
  WITH cte1 AS (...), cte2 AS (...) SELECT ...
  
  # 불가능
  WITH cte1 AS (...) WITH cte2 AS (...) SELECT ...
  ```

- 다른 레벨에서는 여러 개의 WITH절 사용 가능

  ```mysql
  WITH cte1 AS (SELECT 1)
  SELECT * FROM (WITH cte2 AS (SELECT 2) SELECT * FROM cte2 JOIN cte1) AS dt;
  ```

- 하나의 WITH절에서는 하나 이상의 CTE를 정의할 수 있고, 각 CTE명은 유니크해야함

  ```mysql
  # 가능
  WITH cte1 AS (...), cte2 AS (...) SELECT ...
  
  # 불가능
  WITH cte1 AS (...), cte1 AS (...) SELECT ...
  ```



##### WITH RECURSIVE

- 자신을 참조(재귀)하는 서브쿼리를 가진 CTE

- 예시

  ```mysql
  WITH RECURSIVE cte (n) AS
  (
    SELECT 1  -- return initial row set
    UNION ALL
    SELECT n + 1 FROM cte  -- return additional row sets
    WHERE n < 5
  )
  SELECT * FROM cte;
  ```

  | n    |
  | ---- |
  | 1    |
  | 2    |
  | 3    |
  | 4    |
  | 5    |

- 첫 번째 SELECT 부분의 컬럼 타입으로 CTE 컬럼 타입이 정해지며, 컬럼은 NULL 허용

  - 재귀 부분이 재귀되지 않는 부분의 값보다 데이터 크기가 더 크다면 데이터 잘림이 발생하거나(nonstrict SQL mode), 에러 발생(strict SQL mode)

    ```mysql
    WITH RECURSIVE cte AS
    (
      SELECT 1 AS n, 'abc' AS str
      UNION ALL
      SELECT n + 1, CONCAT(str, str) FROM cte WHERE n < 3
    )
    SELECT * FROM cte;
    ```

    | n    | str  |
    | ---- | ---- |
    | 1    | abc  |
    | 2    | abc  |
    | 3    | abc  |

    ```mysql
    Error Code: 1406. Data too long for column 'str' at row 1
    ```

  - 이를 해결하기 위해서는 재귀되지 않는 SELECT 부분에 CAST()를 사용

    ```mysql
    WITH RECURSIVE cte AS
    (
      SELECT 1 AS n, CAST('abc' AS CHAR(20)) AS str
      UNION ALL
      SELECT n + 1, CONCAT(str, str) FROM cte WHERE n < 3
    )
    SELECT * FROM cte;
    ```

    | n    | str          |
    | ---- | ------------ |
    | 1    | abc          |
    | 2    | abcabc       |
    | 3    | abcabcabcabc |

- 재귀 SELECT 부분에는 다음의 구조를 포함하지 않아야 함

  - SUM()과 같은 집계함수
  - 윈도우 함수
  - GROUP BY
  - ORDER BY
  - DISTINCT (UNION DISTINCT는 가능)

- 재귀 SELECT 부분은 CTE를 한 번만 FROM 절에서 참조 가능

- [예제(프로그래머스 - 입양 시각 구하기(2))](https://school.programmers.co.kr/learn/courses/30/lessons/59413)

  ```mysql
  WITH RECURSIVE TEMP AS (
      SELECT 0 AS HOUR, 0 AS COUNT
      UNION ALL
      SELECT HOUR + 1, COUNT
      FROM TEMP
      WHERE HOUR < 23
  )
  , A AS (
      SELECT HOUR(DATETIME) AS HOUR, 
      COUNT(*) AS COUNT
      FROM ANIMAL_OUTS
      GROUP BY HOUR
  )
  
  SELECT T.HOUR, 
  CASE WHEN A.COUNT IS NOT NULL
  THEN (T.COUNT + A.COUNT) 
  ELSE T.COUNT
  END AS COUNT
  FROM TEMP AS T
  LEFT JOIN A
  ON T.HOUR = A.HOUR
  ORDER BY T.HOUR ASC;
  ```

  

