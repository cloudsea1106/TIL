# 📌Django DB MySQL로 설정하기

SQLite3에서 MySQL로 바꾸기

-------------------------------------------



### ✨MySQL 설정

- Workbench를 사용해서 설정 또는 직접 쿼리 작성

- 유저 생성

  - root가 아닌 새로운 유저 생성

  ```
  # 사용자 이름 username, 내부에서만 접속 가능, 비밀번호 1234
  CREATE USER 'username'@'localhost' IDENTIFIED BY '1234';
  
  # 외부에서도 접속 가능
  CREATE USER 'username'@'%' IDENTIFIED BY '1234';
  ```

- DB 생성

  ```
  # DB이름 dbname
  CREATE DATABASE dbname;
  ```

- 유저 권한 설정

  ```
  GRANT ALL ON dbname.* TO 'username'@'localhost';
  ```

- 설정 적용

  ```
  # 환경 설정 변경 적용
  FLUSH PREVILEGES;
  ```





### ✨Django 설정

- vscode를 실행하고 가상환경 설정

  ```python
  python -m venv venv
  source venv/Scripts/activate
  ```

- 패키지 설치

  ```python
  pip install -r requirements.txt
  ```

- manage.py 파일과 동일한 레벨에서 `my_settings.py` 파일 생성

  ```python
  DATABASES = {
      'default': {
          'ENGINE': 'django.db.backends.mysql',
          'NAME': '연동할 MySQL의 데이터베이스 이름',
          'USER': '유저이름',
          'PASSWORD': '비밀번호',
          'HOST': '127.0.0.1',
          'PORT': '3306',
      }
  }
  
  SECRET_KEY = '시크릿키'
  ```

- 프로젝트 `settings.py` 파일 설정

  ```python
  import my_settings
  
  SECRET_KEY = my_settings.SECRET_KEY
  
  DATABASES = my_settings.DATABASES
  ```

- 연결한 DB에 테이블 생성

  ```python
  python manage.py makemigrations
  python manage.py migrate
  ```

  