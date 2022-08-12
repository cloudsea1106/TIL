# 📌Django 배포 오류 해결

배포를 하며 발생한 오류들과 해결 방법

-------------------------------------------

[TOC]



### ✨400 Bad Request

- ALLOWED_HOSTS

  ```python
  # 로컬호스트에서만 접속 허용
  ALLOWED_HOSTS = []
  ALLOWED_HOSTS = ['localhost', '127.0.0.1', '[::1]']
  
  # 모든 곳에서의 접속 허용
  ALLOWED_HOSTS = ['*']
  
  # 특정 호스트에서 접속 허용
  ALLOWED_HOSTS = ['서비스를 제공할 도메인 주소']
  ```





### ✨500 Internal Server Error

- 프론트에서 백엔드로 보내는 요청 주소 설정

  ```js
  # 기존 설정값
  const HOST = 'http://127.0.0.1:8000/api/v1/'
  
  # 배포시 설정값
  # 포트번호 넣지 않기
  const HOST = 'http://<배포주소>/api/v1/'
  ```

- django uwsgi ini 설정

  - 경로 정확히 작성

  ```
  [uwsgi]
  # django 프로젝트 폴더 경로
  chdir = /home/ubuntu/back/
  # wsgi가 존재하는 경로
  module = <프로젝트이름>.wsgi:application
  # 가상환경 경로
  home = /home/ubuntu/venv/
  ...

- 코드 수정 후 reload, restart

  ```bash
  $ sudo systemctl restart uwsgi
  $ sudo systemctl restart nginx
  ```





### ✨도메인 연결 오류

- 도메인 구매 후, DNS 연결

  - 레코드 추가
  - 타입: `A`, 호스트: `@`, 값: IP주소 `xxx.xxx.xxx.xxx`, TTL: `600`

- IP 찾는 방법

  - CMD 실행
  - tracert <주소>
    - 주소 첫 부분에 `http://` 입력하지 않음, 마지막 부분에 `/` 입력하지 않음
    - 예) `tracert naver.com`

- nginx 설정

  ```bash
  # 경로
  $ /etc/nginx/site-available/dafault
  ```

  ```bash
  # defalut
  server {
          listen 80 default_server;
          listen [::]:80 default_server;
  		server_name <도메인주소> <www.도메인주소>
  		...
  }
  
  # 예시
  server {
          listen 80 default_server;
          listen [::]:80 default_server;
  		server_name abc.com www.abc.com
  		...
  }
  ```

- 재시작

  ```bash
  $ sudo systemctl daemon-reload
  $ sudo systemctl restart uwsgi
  $ sudo systemctl restart nginx
  ```

  