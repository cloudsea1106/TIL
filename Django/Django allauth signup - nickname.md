# 📌Django allauth signup

회원가입시 자동으로 닉네임 생성하기

----------------------------------



### ✨allauth를 통한 signup시 오류 발생

- 자동으로 닉네임을 중복없이 생성하는 기능에 오류 발생

- 상황

  - DB를 새로 만들기 위해 기존의 스키마를 삭제하고 새로 생성
  - 기존의 migrations들을 모두 삭제하고 새롭게 생성하고자 함
  - `python manage.py makemigrations`를 실행하려 했으나 오류 발생

  ```
  django.db.utils.ProgrammingError: (1146, "Table '<db이름>.accounts_user' doesn't exist")
  ```

- 기존 model

  ```python
  # accounts/models.py
  from django.contrib.auth.models import AbstractUser
  from django.db import models
  
  
  class User(AbstractUser):
      
      phone_number = models.CharField(max_length=11, blank=True)
      addr = models.CharField(max_length=100, blank=True)
      zip_code = models.CharField(max_length=5, blank=True)
      nickname = models.CharField(max_length=15, unique=True)
  ```

- 기존 serializer

  ```python
  # accounts/serializers.py
  from rest_framework import serializers
  from dj_rest_auth.registration.serializers import RegisterSerializer
  import random
  from django.contrib.auth import get_user_model
  
  
  User = get_user_model()
  
  
  class CustomRegisterSerializer(RegisterSerializer):
  
      full_nickname = ''
  
      while full_nickname == '':
          nick1_lst = ['촉촉한', '싱싱한', '늘푸른', '건강한', '새내기']
          nick2_lst = ['참나무', '소나무', '올리브나무', '야자나무', '귤나무']
          nick1 = random.choice(nick1_lst)
          nick2 = random.choice(nick2_lst)
          nick3 = str(random.randint(0, 9999))
      
          full_nickname = nick1+nick2+nick3
  
          if User.objects.filter(nickname=full_nickname).exists():
              full_nickname = ''
  
      nickname = serializers.CharField(max_length=15, default=full_nickname)
      email = serializers.EmailField()
  
      def get_cleaned_data(self):
          data = super().get_cleaned_data()
          data['nickname'] = self._validated_data.get('nickname', '')
          data['email'] = self._validated_data.get('email', '')
          return data
  ```

- 오류 발생 원인

  - 닉네임 default 값을 줄 때 `if User.objects.filter(nickname=full_nickname).exists():` 코드를 통해 이미 존재하는 닉네임인지 확인하려 함

    → 아직 존재하지 않는 User 테이블에서 찾아보라는 지시였던 것

  - 이미 db와 테이블이 생성된 뒤에는 동작하였으나 생성되기 전에는 오류 발생 





### ✨해결방안

- 수정한 serializer

  ```python
  from rest_framework import serializers
  from dj_rest_auth.registration.serializers import RegisterSerializer
  import random
  from django.contrib.auth import get_user_model
  
  
  User = get_user_model()
  
  
  class CustomRegisterSerializer(RegisterSerializer):
  
      email = serializers.EmailField()
  
      def get_cleaned_data(self):
          full_nickname = ''
  
          while full_nickname == '':
              nick1_lst = ['촉촉한', '싱싱한', '늘푸른', '건강한', '새내기']
              nick2_lst = ['참나무', '소나무', '올리브나무', '야자나무', '귤나무']
              nick1 = random.choice(nick1_lst)
              nick2 = random.choice(nick2_lst)
              nick3 = str(random.randint(0, 9999))
          
              full_nickname = nick1+nick2+nick3
              if User.objects.filter(nickname=full_nickname).exists():
                  full_nickname = ''
  
          data = super().get_cleaned_data()
          data['nickname'] = self._validated_data.get('nickname', full_nickname)
          data['email'] = self._validated_data.get('email', '')
          return data
  ```

- nickname default 값을 `data['nickname'] = self._validated_data.get('nickname', full_nickname)`에서 설정해야함

- `get_cleaned_data`함수 밖 클래스 내에서 User 모델에 접근시 User 테이블이 생성되기 전이기 때문에 인식 불가능
- 기존의 `nickname = serializers.CharField(max_length=15, default=full_nickname)` 코드에서 `default=` 인자는 오류 발생