# MySQL 숫자, 날짜



### 목차

1. [숫자 반올림, 버림, 올림](#숫자-반올림-버림-올림)
2. [날짜 형식](#날짜-형식)
3. [날짜, 시간 계산](#날짜-시간-계산)





### 숫자 반올림, 버림, 올림

- ROUND

  - 반올림
  - ROUND(숫자, 자릿수)
  - 자릿수가 양수일 경우 소수점 아래 자릿수로 반올림
  - 자릿수가 0 또는 생략될 경우 가장 가까운 정수로 반올림
  - 자릿수가 음수일 경우 소수점 위 자릿수에서 반올림

  ```mysql
  SELECT ROUND(1234.5678);
  -- 1235
  SELECT ROUND(1234.5678, 0);
  -- 1235
  SELECT ROUND(1234.5678, 1);
  -- 1234.6
  SELECT ROUND(1234.5678, 2);
  -- 1234.57
  SELECT ROUND(1234.5678, -1);
  -- 1230
  SELECT ROUND(1234.5678, -2);
  -- 1200
  SELECT ROUND(1234.5678, -10);
  -- 0
  ```

- TRUNCATE

  - 버림
  - TRUNCATE(숫자, 자릿수)

  - 자릿수가 양수일 경우 소수점 아래 자릿수로 버림
  - 자릿수가 0일 경우 소수점 이하 버림
  - 자릿수가 음수일 경우 소수점 위 자릿수에서 버림

  - 자릿수 반드시 명시

  ```mysql
  SELECT TRUNCATE(1234.5678, 0);
  -- 1234
  SELECT TRUNCATE(1234.5678, 1);
  -- 1234.5
  SELECT TRUNCATE(1234.5678, 2);
  -- 1234.56
  SELECT TRUNCATE(1234.5678, -1);
  -- 1230
  SELECT TRUNCATE(1234.5678, -2);
  -- 1200
  SELECT TRUNCATE(1234.5678, -10);
  -- 0
  ```

- FLOOR

  - 버림
  - FLOOR(숫자)
  - 표기한 숫자보다 작거나 같은 정수 중 가장 큰 수 반환

  ```mysql
  SELECT FLOOR(1234.5678);
  -- 1234
  SELECT FLOOR(-1234.5678);
  -- -1235
  ```

- CEIL(CEILING)

  - 올림
  - CEIL(숫자) 또는 CEILING(숫자)
  - 표기한 숫자보다 크거나 같은 정수 중 가장 작은 수 반환

  ```mysql
  SELECT CEIL(1234.5678);
  -- 1235
  SELECT CEILING(1234.5678);
  -- 1235
  SELECT CEILING(-1234.5678);
  -- -1234
  ```





### 날짜 형식

- DATE_FORMAT

  - DATE_FORMAT(날짜, 형식)

  - 날짜를 지정한 형식으로 출력

  - 형식 종류 ([참고](https://www.w3schools.com/mysql/func_mysql_date_format.asp))

    - 2023년 2월 8일 수요일 오후 8시 30분 36초 기준

    | 형식 | 설명                     | 예시        |
    | ---- | ------------------------ | ----------- |
    | %Y   | 4자리 연도               | 2023        |
    | %m   | 2자리 월(숫자)           | 02          |
    | %d   | 2자리 일                 | 08          |
    | %y   | 2자리 연도               | 23          |
    | %M   | 긴 월(영문)              | February    |
    | %b   | 짧은 월(영문)            | Feb         |
    | %W   | 긴 요일(영문)            | Wednesday   |
    | %a   | 짧은 요일(영문)          | Wed         |
    | %c   | 1자리~2자리 월           | 2           |
    | %e   | 1자리~2자리 일           | 8           |
    | %l   | 1자리~2자리 시간(12시간) | 8           |
    | %H   | 2자리 시간(24시간)       | 20          |
    | %h   | 2자리 시간(12시간)       | 08          |
    | %i   | 2자리 분                 | 30          |
    | %s   | 2자리 초                 | 36          |
    | %T   | hh:mm:SS                 | 20:30:36    |
    | %r   | hh:mm:ss AM,PM           | 08:30:36 PM |





### 날짜, 시간 계산

- DATEDIFF

  - DATEDIFF(종료일, 시작일)
  - 종료일과 시작일에는 YYYY-MM-DD 또는 시간을 포함하여 YYYY-MM-DD HH:MM:SS 형식으로 입력
  - 시작일부터 종료일까지 두 기간 사이의 일 수를 계산
  - 시간이 포함된 경우 시간은 계산에 포함하지 않음
  - 시간, 날짜 범위에서 벗어나는 값을 입력하면 NULL 반환

  ```mysql
  SELECT DATEDIFF('2023-02-03', '2023-02-01');
  -- 2
  SELECT DATEDIFF('2023-02-03 12:00:00', '2023-02-01 15:00:00');
  -- 2
  SELECT DATEDIFF('2023-02-03 12:00:00', '2023-02-01 10:00:00');
  -- 2
  SELECT DATEDIFF('2023-02-29 12:00:00', '2023-02-01 10:00:00');
  -- NULL
  SELECT DATEDIFF('2023-02-03 25:00:00', '2023-02-01 10:00:00');
  -- NULL
  ```

- TIMEDIFF

  - TIMEDIFF(종료 시간, 시작 시간)
  - 종료 시간과 시작 시간에는 HH:MM:SS 또는 날짜를 포함하여 YYYY-MM-DD HH:MM:SS 형식으로 입력
  - 시작 시간부터 종료 시간 사이의 시간을 계산
  - 시간, 날짜 범위에서 벗어나는 값을 입력하면 NULL 반환

  ```mysql
  SELECT TIMEDIFF('15:00:00', '10:00:00');
  -- 05:00:00
  SELECT TIMEDIFF('2023-02-03 00:00:00', '2023-02-01 00:00:00');
  -- 48:00:00
  SELECT TIMEDIFF('2023-02-03 12:00:00', '2023-02-01 15:00:00');
  -- 45:00:00
  SELECT TIMEDIFF('2023-02-03 12:00:00', '2023-02-01 10:00:00');
  -- 50:00:00
  SELECT TIMEDIFF('2023-02-29 12:00:00', '2023-02-01 10:00:00');
  -- NULL
  SELECT TIMEDIFF('2023-02-03 25:00:00', '2023-02-01 00:00:00');
  -- NULL
  ```

- PERIOD_DIFF

  - PERIOD_DIFF(종료 연월, 시작 연월)
  - 종료 연월과 시작 연월은 YYYYMM 또는 YYMM 형식으로 입력
  - 시작 연월부터 종료 연월 사이의 개월 수를 계산
  - 날짜 범위에서 벗어나는 값을 입력하면 오류 발생
  - 형식에 주의

  ```mysql
  SELECT PERIOD_DIFF('202302', '202301');
  -- 1
  SELECT PERIOD_DIFF('2302', '2301');
  -- 1
  SELECT PERIOD_DIFF('2302', '2305');
  -- -3
  SELECT PERIOD_DIFF('202313', '202301');
  -- Error Code: 1210. Incorrect arguments to period_diff
  ```

- TIMESTAMPDIFF

  - TIMESTAMPDIFF(반환 값 형식, 시작일, 종료일)
  - 시작일과 종료일에는 YYYY-MM-DD 또는 시간을 포함하여 YYYY-MM-DD HH:MM:SS 형식으로 입력
  - 시작일부터 종료일까지 두 기간 사이의 개월 수, 일 수, 시간 등을 계산
  - 시간, 날짜 범위에서 벗어나는 값을 입력하면 NULL 반환
  - 시작일, 종료일 순서에 주의

  | 형식        | 설명       |
  | ----------- | ---------- |
  | YEAR        | 연         |
  | QUARTER     | 분기       |
  | MONTH       | 월         |
  | WEEK        | 주         |
  | DAY         | 일         |
  | HOUR        | 시         |
  | MINUTE      | 분         |
  | SECOND      | 초         |
  | MICROSECOND | 마이크로초 |

  ```mysql
  SELECT TIMESTAMPDIFF(MONTH, '2023-02-01', '2023-05-01');
  -- 3
  SELECT TIMESTAMPDIFF(MONTH, '2023-02-05', '2023-05-01');
  -- 2
  SELECT TIMESTAMPDIFF(DAY, '2023-02-01', '2023-02-03');
  -- 2
  SELECT TIMESTAMPDIFF(DAY, '2023-02-01 01:00:00', '2023-02-03 00:00:00');
  -- 1
  SELECT TIMESTAMPDIFF(HOUR, '2023-02-01', '2023-02-03');
  -- 48
  SELECT TIMESTAMPDIFF(HOUR, '2023-02-01 01:00:00', '2023-02-03 00:00:00');
  -- 47
  SELECT TIMESTAMPDIFF(MONTH, '2023-02-01', '2023-13-01');
  -- NULL
  SELECT TIMESTAMPDIFF(MONTH, '2023-02-01 00:00:00', '2023-12-01 25:00:00');
  -- NULL
  ```

