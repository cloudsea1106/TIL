# ๐Django SECRET_KEY ๋ถ๋ฆฌํ๊ธฐ

[settings.py]-[SECRET_KEY] ์จ๊น

ํ๋ก์ ํธ ์์ฑ์ ์์ง๋ง๊ณ  ๋ฐ๋ก ๋ถ๋ฆฌํ๋๋ก ํ์!

-------------



### โจSECRET_KEY๋?

- `django-admin startproject <ํ๋ก์ ํธ์ด๋ฆ>` ๋ช๋ น์ด๋ฅผ ํตํด ํ๋ก์ ํธ ์์ฑ์ ๊ธฐ๋ณธ์ผ๋ก ์์ฑ๋๋ `settings.py` ํ์ผ์ ์ค์ ๋ ๊ฐ
- ์ฅ๊ณ  ๋ณด์ ๊ธฐ๋ฅ์ ํ์ฉ
- ๋ฐ๋์ ์ธ๋ถ์ ๋ธ์ถ๋์ง ์๋๋ก ํด์ผ ํจ
- ๋ถ๋ฆฌ๋ฅผ ํตํด ์ฝ๋์ ์ง์ ์  ๋ธ์ถ์ด ๋์ง ์๋๋ก ํ  ์ ์์





### โจSECRET_KEY๊ฐ ์ฌ์ฉ๋๋ ๊ฒฝ์ฐ

[Django ๊ณต์๋ฌธ์](https://docs.djangoproject.com/en/1.11/ref/settings/#std:setting-SECRET_KEY)

```
The secret key is used for:

โข All sessions if you are using any other session backend than django.contrib.sessions.backends.cache, or are using the default get_session_auth_hash().

โข All messages if you are using CookieStorage or FallbackStorage.

โข All PasswordResetView tokens.

โข Any usage of cryptographic signing, unless a different key is provided.

If you rotate your secret key, all of the above will be invalidated. Secret keys are not used for passwords of users and key rotation will not affect them.
```

- `django.contrib.sessions.backends.cache`์ธ ๋ค๋ฅธ `session backend`๋ฅผ ์ฌ์ฉํ๊ฑฐ๋ ๊ธฐ๋ณธ `get_session_auth_hash()`๋ฅผ ์ฌ์ฉํ๋ ๋ชจ๋  ์ธ์
- `CookieStorage` ๋๋ `FallbackStorage`๋ฅผ ์ฌ์ฉํ๋ ๋ชจ๋  ๋ฉ์์ง
- ๋ชจ๋  `PasswordResetView` ํ ํฐ
- ๋ค๋ฅธ ํค๊ฐ ์ ๊ณต๋์ง ์๋ ์ํธํ ์๋ช์ ์ฌ์ฉ

- ์ํฌ๋ฆฟํค๊ฐ ๋ณ๊ฒฝ๋๋ฉด ์์ ํด๋นํ๋ ๋ชจ๋  ๊ฒ์ ์ํฅ์ ์ค ์ ์์, ์ ์  ๋น๋ฐ๋ฒํธ์๋ ์ํฅ์ ์ฃผ์ง ์์
  - ์ค์ ๋ก ์ ์ ๋ฅผ ์์ฑํ ๋ค, ์ํฌ๋ฆฟํค๋ฅผ ๋ณ๊ฒฝํ ํ์๋ ๋ก๊ทธ์ธ์ด ์ ๋๋ ๊ฒ์ ํ์ธ ํ  ์ ์์๋ค!
- ์ด๋ฏธ ๋ฐฐํฌ๋ ์ํ์ฌ๋ ์ํฌ๋ฆฟํค ๋ณ๊ฒฝ ๊ฐ๋ฅ. ๋ค๋ง ๋ง์ฐฌ๊ฐ์ง๋ก ์ ์ฌํญ๋ค์ ๋ํด ์ํฅ์ ์ค ์ ์์





### โจ์๋ก์ด SECRET_KEY ์์ฑํ๊ธฐ

- ๋ง์ฝ ์ํฌ๋ฆฟํค๊ฐ ๋ธ์ถ๋ ์ํ๋ก ์ด๋ฏธ ๊ณต๊ฐ๋ ์๊ฒฉ์ ์ฅ์์ ์ฌ๋ ธ๋ค๋ฉด, ์๋ก์ด ํค๋ฅผ ์์ฑํ์ฌ ๋ณ๊ฒฝํ  ์ ์์
- [Django Secret Key Generator](http://www.miniwebtool.com/django-secret-key-generator/) ๋ฅผ ์ด์ฉํ๋ฉด ์์ฝ๊ฒ ์์ฑ ๊ฐ๋ฅ





### โจSECRET_KEY ๋ถ๋ฆฌํ๊ธฐ

- JSON ํ์ผ์ ์ํฌ๋ฆฟํค๋ฅผ ์๋ ฅํ๊ณ  `settings.py`์์ ์ด๋ฅผ ์ฐธ์กฐํ๋๋ก ์ค์ 

- ์ต์๋จ ๋๋ ํ ๋ฆฌ์ธ `BASE_DIR`์ `secrets.json`ํ์ผ ์์ฑ

  ```json
  # secrets.json
  
  {
      "SECRET_KEY": "<์ฐธ์กฐํ  ์ํฌ๋ฆฟํค>"
  }

- `.gitignore`์ `secrets.json` ์ถ๊ฐ

- `settings.py` ์ค์  [์ฝ๋์ถ์ฒ](https://wayhome25.github.io/django/2017/07/11/django-settings-secret-key/)

  ```python
  # settings.py
  
  import os, json
  from django.core.exceptions import ImproperlyConfigured
  
  
  secret_file = os.path.join(BASE_DIR, 'secrets.json') # secrets.json ํ์ผ ์์น๋ฅผ ๋ช์
  
  with open(secret_file) as f:
      secrets = json.loads(f.read())
  
  def get_secret(setting, secrets=secrets):
      """๋น๋ฐ ๋ณ์๋ฅผ ๊ฐ์ ธ์ค๊ฑฐ๋ ๋ช์์  ์์ธ๋ฅผ ๋ฐํํ๋ค."""
      try:
          return secrets[setting]
      except KeyError:
          error_msg = "Set the {} environment variable".format(setting)
          raise ImproperlyConfigured(error_msg)
  
  SECRET_KEY = get_secret("SECRET_KEY")
  ```

  - ์คํ ๋ฑ๊ณผ ๊ฐ์ ์ด์ ๋ก ๋ณ์ `SECRET_KEY`๋ฅผ ์ฐพ์ ์ ์๋ค๋ฉด `Set the SECRET_KEY environment variable` ๊ณผ ๊ฐ์ ์ค๋ฅ ๋ฉ์์ง๋ฅผ ํฐ๋ฏธ๋์์ ํ์ธํ  ์ ์์





### โจSECRET_KEY๋ฅผ ๋ณ๊ฒฝํ์ง ์๊ณ  ๋ถ๋ฆฌ๋ง ํ๋ ๊ฒฝ์ฐ

#### ๊ฐ์  push๋ฅผ ํ๊ธฐ ๋๋ฌธ์ ๊ฐ์ธ ํ๋ก์ ํธ์์๋ง ์ฌ์ฉ

- ๋ธ์ถ์ด ๋ฐ์ํ์ ๋๋ ์ํฌ๋ฆฟํค๋ฅผ ๋ณ๊ฒฝํ๊ณ  ๋ถ๋ฆฌํ์ฌ ์ฐธ์กฐํ๋๋ก ํ๊ณ ,  `add-commit-push`๋ฅผ ์งํํ๋ฉด ๋จ

- ๋ง์ฝ ๋ณ๊ฒฝํ์ง ์๊ณ  ๋ถ๋ฆฌ๋ง ํ์ฌ ์จ๊น์ฒ๋ฆฌ๋ฅผ ํ๋ค๋ฉด, ์์ ๋ถ๋ฆฌํ๋ ๊ณผ์ ์ ๊ทธ๋๋ก ์งํํ ๋ค์

  `.gitignore`์ `secrets.json`์ ์ถ๊ฐํ๊ณ 

  ๋จผ์  ๋ชจ๋  ์ปค๋ฐ ๊ธฐ๋ก์ ์ญ์ ํ๊ธฐ ์ํด ์ฒซ ์ปค๋ฐ ์ํ๋ก ์ด๋

  - ํ๋ก์ ํธ ์์ฑ์ด ์ฒซ ์ปค๋ฐ์ด๋ผ๋ฉด `๋ชจ๋ `์ปค๋ฐ์ ์ง์์ผํ๋ค! ์ํฌ๋ฆฟํค๋ ํ๋ก์ ํธ ์์ฑ์ ํจ๊ป ์์ฑ๋๊ธฐ ๋๋ฌธ!

  ```bash
  # ๋ก๊ทธ ํ์ธ, ๊ฐ์ฅ ์๋์ ์๋ ์ฒซ ์ปค๋ฐID ๋ณต์ฌ
  $ git log --oneline --all
  
  $ git reset <์ปค๋ฐID>
  
  # ๋ก๊ทธ๋ฅผ ํ์ธํด๋ณด๋ฉด HEAD๊ฐ ์ฒซ ์ปค๋ฐ์ ๊ฐ๋ฆฌํค๊ณ  ์์
  $ git log --oneline --all
  ```

  ```bash
  # ์ฒซ ์ปค๋ฐ ๋๋๋ฆฌ๊ธฐ
  $ git update-ref -d HEAD
  
  # ์ด ์ํ์์ ๋ก๊ทธ๋ฅผ ํ์ธํ๋ฉด ์ปค๋ฐ์ด ์กด์ฌํ์ง ์๋๋ค
  
  # ์๊ฒฉ์ ์ฅ์์ ์๋ ํ์ผ ์ญ์ 
  $ git rm -r --cached .
  ```

  ์ ๋ช๋ น์ด๋ฅผ ์๋ ฅํ๋ฉด ์ถ์ ๊ธฐ๋ก์ ์ญ์ ํ  ์ ์์ (์ปค๋ฐ์ด ์ญ์ ๋๋ค!)

  ๊ทธ ์ดํ ๋ค์ `add-commit-push`๋ฅผ ์งํํ๋๋ฐ, ์ฌ๊ธฐ์ ์๊ฒฉ์ ์ฅ์์ ๋ก์ปฌ์ ์ฅ์๊ฐ์ ์ฐจ์ด๊ฐ ์์ด `push`์ ์ค๋ฅ ๋ฐ์

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

  ๊ฐ์  push๋ฅผ ์ด์ฉํ์ฌ ํด๊ฒฐ

  - ๋ชจ๋  ์ปค๋ฐ ๊ธฐ๋ก์ ์ง์ฐ๊ธฐ ์ํด ๊ฐ์  push ์ฌ์ฉ

  - ์ฌ๋ฟ์ด ํจ๊ป ํ๋ ๊ณต๋ ํ๋ก์ ํธ์ ๊ฒฝ์ฐ ์ถฉ๋์ด ๋ฐ์ํ  ์ ์๋ค!!
  - ๋ฐ๋์ ์ฃผ์ํด์ ์ฌ์ฉํด์ผํจ

  
