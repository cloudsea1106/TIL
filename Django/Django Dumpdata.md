# 📌Django Dumpdata

한글 데이터 깨짐 없이 저장하기

--------------------------------------------------



### ✨문제상황

- `python manage.py dumpdata`를 통해 `fixtures`를 만들고자 함

  ```python
  python manage.py dumpdata --indent 4 accounts.user > user.json
  ```

- 한글이 깨지는 현상 발생

  ```json
  [
  {
      "model": "accounts.user",
      "pk": 1,
      "fields": {
          "password": "___",
          "username": "test1",
          "nickname": "������������4979",
      }
  },
  {
      "model": "accounts.user",
      "pk": 2,
      "fields": {
          "password": "___",
          "username": "test2",
          "nickname": "�̽��ѿø��곪��6759",
      }
  }
  ]
  ```





### ✨해결방안

- [공식문서](https://docs.python.org/3/using/cmdline.html#cmdoption-X)

- Python UTF-8 Mode 활성화

- 코드

  ```python
  python -Xutf8 manage.py dumpdata --indent 4 <앱이름>.<모델이름> > <파일이름>.json
  
  # 예시: accounts 앱의 User 모델 데이터를 user.json 파일로 저장
  # python -Xutf8 manage.py dumpdata --indent 4 accounts.user > user.json

- 결과

  ```json
  [
  {
      "model": "accounts.user",
      "pk": 1,
      "fields": {
          "password": "___",
          "username": "test1",
          "nickname": "새내기참나무4979",
      }
  },
  {
      "model": "accounts.user",
      "pk": 2,
      "fields": {
          "password": "___",
          "username": "test2",
          "nickname": "싱싱한올리브나무6759",
      }
  }
  ]
  ```

  