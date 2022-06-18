# 📌Django SECRET_KEY 분리하기

[settings.py]-[SECRET_KEY] 숨김

프로젝트 생성시 잊지말고 바로 분리하도록 하자!

-------------



### ✨SECRET_KEY란?

- `django-admin startproject <프로젝트이름>` 명령어를 통해 프로젝트 생성시 기본으로 작성되는 `settings.py` 파일에 설정된 값
- 장고 보안 기능에 활용
- 반드시 외부에 노출되지 않도록 해야 함
- 분리를 통해 코드에 직접적 노출이 되지 않도록 할 수 있음





### ✨SECRET_KEY가 사용되는 경우

[Django 공식문서](https://docs.djangoproject.com/en/1.11/ref/settings/#std:setting-SECRET_KEY)

```
The secret key is used for:

• All sessions if you are using any other session backend than django.contrib.sessions.backends.cache, or are using the default get_session_auth_hash().

• All messages if you are using CookieStorage or FallbackStorage.

• All PasswordResetView tokens.

• Any usage of cryptographic signing, unless a different key is provided.

If you rotate your secret key, all of the above will be invalidated. Secret keys are not used for passwords of users and key rotation will not affect them.
```

- `django.contrib.sessions.backends.cache`외 다른 `session backend`를 사용하거나 기본 `get_session_auth_hash()`를 사용하는 모든 세션
- `CookieStorage` 또는 `FallbackStorage`를 사용하는 모든 메시지
- 모든 `PasswordResetView` 토큰
- 다른 키가 제공되지 않는 암호화 서명의 사용

- 시크릿키가 변경되면 위에 해당하는 모든 것에 영향을 줄 수 있음, 유저 비밀번호에는 영향을 주지 않음
  - 실제로 유저를 생성한 뒤, 시크릿키를 변경한 후에도 로그인이 잘 되는 것을 확인 할 수 있었다!
- 이미 배포된 상태여도 시크릿키 변경 가능. 다만 마찬가지로 위 사항들에 대해 영향을 줄 수 있음





### ✨새로운 SECRET_KEY 생성하기

- 만약 시크릿키가 노출된 상태로 이미 공개된 원격저장소에 올렸다면, 새로운 키를 생성하여 변경할 수 있음
- [Django Secret Key Generator](http://www.miniwebtool.com/django-secret-key-generator/) 를 이용하면 손쉽게 생성 가능





### ✨SECRET_KEY 분리하기

- JSON 파일에 시크릿키를 입력하고 `settings.py`에서 이를 참조하도록 설정

- 최상단 디렉토리인 `BASE_DIR`에 `secrets.json`파일 생성

  ```json
  # secrets.json
  
  {
      "SECRET_KEY": "<참조할 시크릿키>"
  }

- `.gitignore`에 `secrets.json` 추가

- `settings.py` 설정 [코드출처](https://wayhome25.github.io/django/2017/07/11/django-settings-secret-key/)

  ```python
  # settings.py
  
  import os, json
  from django.core.exceptions import ImproperlyConfigured
  
  
  secret_file = os.path.join(BASE_DIR, 'secrets.json') # secrets.json 파일 위치를 명시
  
  with open(secret_file) as f:
      secrets = json.loads(f.read())
  
  def get_secret(setting, secrets=secrets):
      """비밀 변수를 가져오거나 명시적 예외를 반환한다."""
      try:
          return secrets[setting]
      except KeyError:
          error_msg = "Set the {} environment variable".format(setting)
          raise ImproperlyConfigured(error_msg)
  
  SECRET_KEY = get_secret("SECRET_KEY")
  ```

  - 오타 등과 같은 이유로 변수 `SECRET_KEY`를 찾을 수 없다면 `Set the SECRET_KEY environment variable` 과 같은 오류 메시지를 터미널에서 확인할 수 있음





### ✨SECRET_KEY를 변경하지 않고 분리만 하는 경우

#### 강제 push를 하기 때문에 개인 프로젝트에서만 사용

- 노출이 발생했을 때는 시크릿키를 변경하고 분리하여 참조하도록 하고,  `add-commit-push`를 진행하면 됨

- 만약 변경하지 않고 분리만 하여 숨김처리를 한다면, 위의 분리하는 과정을 그대로 진행한 다음

  `.gitignore`에 `secrets.json`을 추가하고

  먼저 모든 커밋 기록을 삭제하기 위해 첫 커밋 상태로 이동

  - 프로젝트 생성이 첫 커밋이라면 `모든`커밋을 지워야한다! 시크릿키는 프로젝트 생성시 함께 생성되기 때문!

  ```bash
  # 로그 확인, 가장 아래에 있는 첫 커밋ID 복사
  $ git log --oneline --all
  
  $ git reset <커밋ID>
  
  # 로그를 확인해보면 HEAD가 첫 커밋을 가리키고 있음
  $ git log --oneline --all
  ```

  ```bash
  # 첫 커밋 되돌리기
  $ git update-ref -d HEAD
  
  # 이 상태에서 로그를 확인하면 커밋이 존재하지 않는다
  
  # 원격저장소에 있는 파일 삭제
  $ git rm -r --cached .
  ```

  위 명령어를 입력하면 추적기록을 삭제할 수 있음 (커밋이 삭제된다!)

  그 이후 다시 `add-commit-push`를 진행하는데, 여기서 원격저장소와 로컬저장소간에 차이가 있어 `push`에 오류 발생

  ```bash
  $ git push origin master
  To https://github.com/cloudsea1106/test.git
   ! [rejected]        master -> master (non-fast-forward)
  error: failed to push some refs to 'https://github.com/cloudsea1106/test.git'
  hint: Updates were rejected because the tip of your current branch is behind
  hint: its remote counterpart. Integrate the remote changes (e.g.
  hint: 'git pull ...') before pushing again.
  hint: See the 'Note about fast-forwards' in 'git push --help' for details.
  ```

  ```bash
  $ git push -f origin master
  ```

  강제 push를 이용하여 해결

  - 모든 커밋 기록을 지우기 위해 강제 push 사용

  - 여럿이 함께 하는 공동 프로젝트의 경우 충돌이 발생할 수 있다!!
  - 반드시 주의해서 사용해야함

  
