# ๐Django DB MySQL๋ก ์ค์ ํ๊ธฐ

SQLite3์์ MySQL๋ก ๋ฐ๊พธ๊ธฐ

-------------------------------------------



### โจMySQL ์ค์ 

- Workbench๋ฅผ ์ฌ์ฉํด์ ์ค์  ๋๋ ์ง์  ์ฟผ๋ฆฌ ์์ฑ

- ์ ์  ์์ฑ

  - root๊ฐ ์๋ ์๋ก์ด ์ ์  ์์ฑ

  ```
  # ์ฌ์ฉ์ ์ด๋ฆ username, ๋ด๋ถ์์๋ง ์ ์ ๊ฐ๋ฅ, ๋น๋ฐ๋ฒํธ 1234
  CREATE USER 'username'@'localhost' IDENTIFIED BY '1234';
  
  # ์ธ๋ถ์์๋ ์ ์ ๊ฐ๋ฅ
  CREATE USER 'username'@'%' IDENTIFIED BY '1234';
  ```

- DB ์์ฑ

  ```
  # DB์ด๋ฆ dbname
  CREATE DATABASE dbname;
  ```

- ์ ์  ๊ถํ ์ค์ 

  ```
  GRANT ALL ON dbname.* TO 'username'@'localhost';
  ```

- ์ค์  ์ ์ฉ

  ```
  # ํ๊ฒฝ ์ค์  ๋ณ๊ฒฝ ์ ์ฉ
  FLUSH PREVILEGES;
  ```





### โจDjango ์ค์ 

- vscode๋ฅผ ์คํํ๊ณ  ๊ฐ์ํ๊ฒฝ ์ค์ 

  ```python
  python -m venv venv
  source venv/Scripts/activate
  ```

- ํจํค์ง ์ค์น

  ```python
  pip install -r requirements.txt
  ```

- manage.py ํ์ผ๊ณผ ๋์ผํ ๋ ๋ฒจ์์ `my_settings.py` ํ์ผ ์์ฑ

  ```python
  DATABASES = {
      'default': {
          'ENGINE': 'django.db.backends.mysql',
          'NAME': '์ฐ๋ํ  MySQL์ ๋ฐ์ดํฐ๋ฒ ์ด์ค ์ด๋ฆ',
          'USER': '์ ์ ์ด๋ฆ',
          'PASSWORD': '๋น๋ฐ๋ฒํธ',
          'HOST': '127.0.0.1',
          'PORT': '3306',
      }
  }
  
  SECRET_KEY = '์ํฌ๋ฆฟํค'
  ```

- ํ๋ก์ ํธ `settings.py` ํ์ผ ์ค์ 

  ```python
  import my_settings
  
  SECRET_KEY = my_settings.SECRET_KEY
  
  DATABASES = my_settings.DATABASES
  ```

- ์ฐ๊ฒฐํ DB์ ํ์ด๋ธ ์์ฑ

  ```python
  python manage.py makemigrations
  python manage.py migrate
  ```

  