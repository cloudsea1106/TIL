# 📌SQL WHERE HAVING 조건

WHERE와 HAVING의 차이

-------------------------



### ✨WHERE

```sql
SELECT * FROM 테이블명 WHERE 조건;
```

```sql
-- 사원테이블에서 이름이 홍길동인 사원의 데이터 조회
SELECT * FROM 사원 WHERE name='홍길동';
```





### ✨HAVING

```sql
SELECT * FROM 테이블명 GROUP BY 필드명 HAVING 조건;
```

```sql
-- 사원 테이블에서 이름과 수를 조회

SELECT name, count(*) FROM 사원 WHERE name!='홍길동' GROUP BY name;
-- WHERE 조건에 맞는 데이터를 먼저 가져온 다음 그룹화
-- 이름이 홍길동이 아닌 사원을 이름으로 묶어 이름과 수 조회

SELECT name, count(*) FROM 사원 GROUP BY name HAVING count(*) >= 2;
-- 그룹화 한 다음 HAVING 조건에 맞는 데이터 조회. HAVING 조건절에 이용하는 컬럼은 SELECT에 반드시 명시되어야 함
-- 사원을 이름으로 묶어서 동명이인이 2명 이상인 이름과 수 조회
```

