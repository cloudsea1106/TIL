# MySQL CASE, IF



### 목차

1. [CASE](#CASE)
   - [switch문](#switch문)
   - [if문](#if문)
2. [IF](#IF)
   - [IF() 함수](#IF-함수)
   - [IFNULL() 함수](#IFNULL-함수)





### CASE

- switch 또는 if처럼 사용 가능

##### switch문

- value와 compare_value를 비교하여 값이 같다면 THEN 절을 리턴
- WHEN compare_value와 다르면 ELSE 절 리턴, ELSE 절이 없다면 NULL 리턴
- END로 끝맺음

```mysql
CASE value
	WHEN compare_value THEN 리턴값
	WHEN compare_value THEN 리턴값
	ELSE 만족하는 조건이 없을 경우 리턴값
END
```

```mysql
-- 예시
SELECT 1 AS NUMBER,
CASE 1
WHEN 1 THEN '1입니다'
WHEN 2 THEN '2입니다'
ELSE '1도 2도 아닙니다'
END AS RESULT;
```

| NUMBER | RESULT  |
| ------ | ------- |
| 1      | 1입니다 |

##### if문

- CASE 뒤 value가 없음, 바로 WHEN 조건절
- WHEN 조건절이 참이면 THEN 절 리턴
- WHEN 조건절이 거짓일 경우 ELSE 절 리턴, ELSE 절이 없다면 NULL 리턴

- END로 끝맺음

```mysql
CASE
	WHEN 조건 THEN 리턴값
	WHEN 조건 THEN 리턴값
	ELSE 만족하는 조건이 없을 경우 리턴값
END
```

```mysql
SELECT 1 AS NUMBER,
CASE
WHEN 1 = 1 THEN '1입니다'
WHEN 1 = 2 THEN '2입니다'
ELSE '1도 2도 아닙니다'
END AS RESULT;
```

| NUMBER | RESULT  |
| ------ | ------- |
| 1      | 1입니다 |





### IF

##### IF() 함수

- IF(조건, 참일 경우 리턴값, 거짓일 경우 리턴값)

```mysql
SELECT IF(1 > 2, 'TRUE', 'FALSE') AS RESULT;
```

| RESULT |
| ------ |
| FALSE  |

##### IFNULL() 함수

- 컬럼 값이 NULL일 때 값을 대체하여 리턴
- SELECT IFNULL(컬럼명, 대체값) FROM 테이블명;

```mysql
SELECT IFNULL(phone_number, '01012345678') AS phone_number FROM user;
```

| phone_number |
| ------------ |
| 01012345678  |

