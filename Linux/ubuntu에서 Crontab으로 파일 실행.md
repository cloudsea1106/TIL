# 📌ubuntu에서 Crontab으로 파일 실행

특정 시간/날짜에 자동으로 파일 실행하기

-----------------------------------

[TOC]



### ✨Crontab 명령어

- crontab 새로 작성 또는 편집 (nano)

  ```bash
  $ crontab -e
  ```

- 작성된 crontab 확인

  ```bash
  $ crontab -l
  ```

- crontab 모두 삭제

  ```bash
  $ crontab -r
  ```





### ✨Crontab 규칙

- `분 시 일 월 요일 {명령어}` 순서로 작성
- 분: 0 ~ 59
- 시: 0 ~ 23
- 일: 1 ~ 31
- 월: 1 ~ 12
- 요일: 0 ~ 6 (0: 일요일, 6: 토요일)





### ✨Crontab 작성 (예시)

- 현재경로: `/home/ubuntu/`

- 등록

  ```bash
  $ crontab -e
  ```

- 주석 맨 아래에 추가

  ```
  분 시간 일 달 요일 {파이썬 절대경로} {실행파일 절대경로}
  또는
  분 시간 일 달 요일 {파이썬 절대경로} {실행파일 절대경로} >> {로그 생성할 절대경로}
  
  * * * * * /usr/local/bin/python3.9 /home/ubuntu/test.py >> /home/ubuntu/test.log
  ```

  - `test.py`는 간단한 `print()` 함수만 있는 테스트 파일
  - 실행 파일은 해당 위치에 있어야 함
  - 로그 파일은 실행되면서 생성됨
  - `>>`: 로그 뒤에 덧붙이기

  - `>`: 로그 갱신하기(덮어쓰기)
  - 파이썬 위치: `which python3` 또는 `which python3.9` 등 `which {설치한 파이썬}`으로 찾을 수 있음

- 저장: `ctrl + x` 누른 다음`y(yes)`, `enter`

- 확인

  ```bash
  $ grep CRON /var/log/syslog
  ```

  또는 직접 로그 파일 확인 가능

  ```bash
  $ cd {로그 파일이 위치한 경로}
  $ cat {로그 파일 이름}
  
  $ cd home/ubuntu/
  $ cat test.log
  ```





### ✨Crontab 작성 (실제)

- 매일 0시 0분에 mysql 업데이트 파일 실행, 매일 0시 5분에 redis 업데이트 파일 실행
- ubuntu에 먼저 실행 파일에서 사용할 라이브러리들을 설치

```
sudo apt-get install python3-pip
sudo pip3 install python-dateutil
sudo pip3 install pymysql
sudo pip3 install requests
sudo pip3 install redis
```

- crontab 등록

```
# 매일 0시 0분에 mysql 업데이트 파일 실행
0 0 * * * /usr/local/bin/python3.9 /home/ubuntu/mysql_info.py >> /home/ubuntu/mysql_info.log

# 매일 0시 5분에 redis 업데이트 파일 실행
5 0 * * * /usr/local/bin/python3.9 /home/ubuntu/redis_info.py >> /home/ubuntu/redis_info.log
```





