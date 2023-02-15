# 📌MySQL error

---------------

### 목차

1. [1175](#1175-you-are-using-safe-update-mode)
1. [1248](#1248-Every-derived-table-must-have-its-own-alias)



### 1175. you are using safe update mode

- 다수의 데이터를 키값을 사용하지 않고 삭제 또는 수정하려고 시도했을 때 발생

- 오류 내용

  ```
  error code: 1175. you are using safe update mode and you tried to update a table without a where that uses a key column. to disable safe mode, toggle the option in preferences -> sql editor and reconnect.
  ```

- 해결 방법 1

  ```sql
  set sql_safe_updates=0;
  ...
  set sql_safe_updates=1;
  ```

  - 일시적 safe mode 해제
  - 쿼리 실행 후 다시 safe mode 설정

- 해결 방법 2

  - `Edit > Preferences` 선택
  - `SQL Editor > Safe Updates` 체크박스 해제, `OK` 
  - 워크벤치 재시작 필요


![1175-1](MySQL_error.assets/1175-1.png)

`Edit > Preferences` 선택

![1175-2](MySQL_error.assets/1175-2.png)

`SQL Editor > Safe Updates` 체크박스 해제, `OK` 





### 1248. Every derived table must have its own alias

- 서브쿼리에서 alias를 주지 않았을 경우 발생

![1248-1](MySQL_error.assets/1248-1.png)

- 해결 방법

  ![1248-2](MySQL_error.assets/1248-2.png)

  - 서브쿼리에 alias 지정



