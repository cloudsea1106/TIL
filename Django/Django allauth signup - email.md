# ๐Django allauth signup

 ํ์๊ฐ์์ email ๋ฑ๋กํ๊ธฐ

------------------------------



### โจallauth๋ฅผ ํตํ signup์ ์ค๋ฅ ๋ฐ์

- User model

  ```python
  # accounts/models.py
  from django.contrib.auth.models import AbstractUser
  from django.db import models
  
  
  class User(AbstractUser):
      pass
  ```

  - `settings.py`์ `AUTH_USER_MODEL = 'accounts.User'` ๋ฑ๋ก ์๋ฃํ ์ํ

- signup์ ์์ฒญ์ ๋ณด๋ผ ๋ body์ ํ์๊ฐ์ธ `username`, `password1`, `password2`๋ฅผ ๊ธฐ๋ณธ์ผ๋ก ์์ฑํ๊ณ , ์ ํ๊ฐ์ธ `email`๊น์ง ์์ฑํ๋ฉด ์์ํ์ง ๋ชปํ ์ค๋ฅ ๋ฐ์

- ๋ฐ์ํ ์ค๋ฅ

  ```python
  ConnectionRefusedError: [WinError 10061] ๋์ ์ปดํจํฐ์์ ์ฐ๊ฒฐ์ ๊ฑฐ๋ถํ์ผ๋ฏ๋ก ์ฐ๊ฒฐํ์ง ๋ชปํ์ต๋๋ค
  ```

  - ์์ ๊ฒฐ๊ณผ๋ ๋ก๊ทธ์ธ ์ํ๋ก ์ ํ๋์ด ํ ํฐ ๋ฆฌํด, DB์ email์ ํฌํจํ์ฌ ๋ฐ์ดํฐ ์ ์ฅ
  - ์ค์  ๊ฒฐ๊ณผ๋ ๋น๋ก๊ทธ์ธ ์ํ๋ก ํ ํฐ ๋ฐํ X, DB์ email์ ํฌํจํ์ฌ ๋ฐ์ดํฐ ์ ์ฅ, 500 ์ํ์ ํจ๊ป ์๋ฌ ๋ฐ์





### โจํด๊ฒฐ๋ฐฉ์

- ์ฐธ๊ณ ๋ฌธ์
  - [๊ณต์๋ฌธ์](https://django-allauth.readthedocs.io/en/latest/configuration.html)
  - [๊นํ๋ธ](https://github.com/pennersr/django-allauth/blob/master/allauth/account/app_settings.py#L7)

- ์ฝ๋ (`settings.py`)

  ```python
  ACCOUNT_EMAIL_VERIFICATION = 'none'
  ```

  ๋๋

  ```python
  # ๊ฐ๋ฐ๋จ๊ณ์์ ์ฌ์ฉ
  EMAIL_BACKEND = 'django.core.mail.backends.console.EmailBackend'
  ```

- `ACCOUNT_EMAIL_VERIFICATION = 'none'`

  ```
  ACCOUNT_EMAIL_VERIFICATION (=โoptionalโ)
  Determines the e-mail verification method during signup โ choose one of "mandatory", "optional", or "none".
  
  Setting this to โmandatoryโ requires ACCOUNT_EMAIL_REQUIRED to be True
  
  When set to โmandatoryโ the user is blocked from logging in until the email address is verified. Choose โoptionalโ or โnoneโ to allow logins with an unverified e-mail address. In case of โoptionalโ, the e-mail verification mail is still sent, whereas in case of โnoneโ no e-mail verification mails are sent.
  ```

  - email verification์ด ๊ธฐ๋ณธ ์ค์ ์ผ๋ก `'optional'`์ด ์ ์ฉ๋์๊ธฐ ๋๋ฌธ์ ํ์๊ฐ์์ email์ ์์ฑํ๋ฉด ์ธ์ฆ ์ด๋ฉ์ผ์ด ๋ณด๋ด์ง
  - `'none'`์ผ๋ก ์ค์ ์ ๋ณ๊ฒฝํ๋ฉด ๋ฉ์ผ์ด ๋ณด๋ด์ง์ง ์๊ณ  ๋ฐ๋ก ํ์๊ฐ์์ด ์๋ฃ๋๋ฉฐ ๋ก๊ทธ์ธ ์ํ๋ก ์ ํ๋จ

- `EMAIL_BACKEND = 'django.core.mail.backends.console.EmailBackend'`
  - ์ค์ ๋ก ํ์๊ฐ์ ํ์ธ ์ธ์ฆ ๋ฉ์ผ์ ๋ณด๋ด๋ ๋์ ์, ํฐ๋ฏธ๋์ฐฝ์ ์ด๋ฉ์ผ ๋ด์ฉ์ ๋ณด์ฌ์ค
  - ํฐ๋ฏธ๋์ ์ด๋ฉ์ผ ๋ด์ฉ์ ๋ณด์ฌ์ฃผ๊ธฐ ๋๋ฌธ์ ๊ฐ๋ฐ๋จ๊ณ์์ ์ฌ์ฉ
- ๋ ๊ฐ์ง ๋ฐฉ๋ฒ ๋ชจ๋ ์ค๋ฅ ๋ฐ์ X