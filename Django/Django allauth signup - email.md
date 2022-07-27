# 📌Django allauth signup

 회원가입시 email 등록하기

------------------------------



### ✨allauth를 통한 signup시 오류 발생

- User model

  ```python
  # accounts/models.py
  from django.contrib.auth.models import AbstractUser
  from django.db import models
  
  
  class User(AbstractUser):
      pass
  ```

  - `settings.py`에 `AUTH_USER_MODEL = 'accounts.User'` 등록 완료한 상태

- signup에 요청을 보낼 때 body에 필수값인 `username`, `password1`, `password2`를 기본으로 작성하고, 선택값인 `email`까지 작성하면 예상하지 못한 오류 발생

- 발생한 오류

  ```python
  ConnectionRefusedError: [WinError 10061] 대상 컴퓨터에서 연결을 거부했으므로 연결하지 못했습니다
  ```

  - 예상 결과는 로그인 상태로 전환되어 토큰 리턴, DB에 email을 포함하여 데이터 저장
  - 실제 결과는 비로그인 상태로 토큰 발행 X, DB에 email을 포함하여 데이터 저장, 500 상태와 함께 에러 발생





### ✨해결방안

- 참고문서
  - [공식문서](https://django-allauth.readthedocs.io/en/latest/configuration.html)
  - [깃허브](https://github.com/pennersr/django-allauth/blob/master/allauth/account/app_settings.py#L7)

- 코드 (`settings.py`)

  ```python
  ACCOUNT_EMAIL_VERIFICATION = 'none'
  ```

  또는

  ```python
  # 개발단계에서 사용
  EMAIL_BACKEND = 'django.core.mail.backends.console.EmailBackend'
  ```

- `ACCOUNT_EMAIL_VERIFICATION = 'none'`

  ```
  ACCOUNT_EMAIL_VERIFICATION (=”optional”)
  Determines the e-mail verification method during signup – choose one of "mandatory", "optional", or "none".
  
  Setting this to “mandatory” requires ACCOUNT_EMAIL_REQUIRED to be True
  
  When set to “mandatory” the user is blocked from logging in until the email address is verified. Choose “optional” or “none” to allow logins with an unverified e-mail address. In case of “optional”, the e-mail verification mail is still sent, whereas in case of “none” no e-mail verification mails are sent.
  ```

  - email verification이 기본 설정으로 `'optional'`이 적용되었기 때문에 회원가입시 email을 작성하면 인증 이메일이 보내짐
  - `'none'`으로 설정을 변경하면 메일이 보내지지 않고 바로 회원가입이 완료되며 로그인 상태로 전환됨

- `EMAIL_BACKEND = 'django.core.mail.backends.console.EmailBackend'`
  - 실제로 회원가입 확인 인증 메일을 보내는 대신에, 터미널창에 이메일 내용을 보여줌
  - 터미널에 이메일 내용을 보여주기 때문에 개발단계에서 사용
- 두 가지 방법 모두 오류 발생 X