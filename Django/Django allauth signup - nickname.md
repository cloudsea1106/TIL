# ๐Django allauth signup

ํ์๊ฐ์์ ์๋์ผ๋ก ๋๋ค์ ์์ฑํ๊ธฐ

----------------------------------



### โจallauth๋ฅผ ํตํ signup์ ์ค๋ฅ ๋ฐ์

- ์๋์ผ๋ก ๋๋ค์์ ์ค๋ณต์์ด ์์ฑํ๋ ๊ธฐ๋ฅ์ ์ค๋ฅ ๋ฐ์

- ์ํฉ

  - DB๋ฅผ ์๋ก ๋ง๋ค๊ธฐ ์ํด ๊ธฐ์กด์ ์คํค๋ง๋ฅผ ์ญ์ ํ๊ณ  ์๋ก ์์ฑ
  - ๊ธฐ์กด์ migrations๋ค์ ๋ชจ๋ ์ญ์ ํ๊ณ  ์๋กญ๊ฒ ์์ฑํ๊ณ ์ ํจ
  - `python manage.py makemigrations`๋ฅผ ์คํํ๋ ค ํ์ผ๋ ์ค๋ฅ ๋ฐ์

  ```
  django.db.utils.ProgrammingError: (1146, "Table '<db์ด๋ฆ>.accounts_user' doesn't exist")
  ```

- ๊ธฐ์กด model

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

- ๊ธฐ์กด serializer

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
          nick1_lst = ['์ด์ดํ', '์ฑ์ฑํ', '๋ํธ๋ฅธ', '๊ฑด๊ฐํ', '์๋ด๊ธฐ']
          nick2_lst = ['์ฐธ๋๋ฌด', '์๋๋ฌด', '์ฌ๋ฆฌ๋ธ๋๋ฌด', '์ผ์๋๋ฌด', '๊ทค๋๋ฌด']
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

- ์ค๋ฅ ๋ฐ์ ์์ธ

  - ๋๋ค์ default ๊ฐ์ ์ค ๋ `if User.objects.filter(nickname=full_nickname).exists():` ์ฝ๋๋ฅผ ํตํด ์ด๋ฏธ ์กด์ฌํ๋ ๋๋ค์์ธ์ง ํ์ธํ๋ ค ํจ

    โ ์์ง ์กด์ฌํ์ง ์๋ User ํ์ด๋ธ์์ ์ฐพ์๋ณด๋ผ๋ ์ง์์๋ ๊ฒ

  - ์ด๋ฏธ db์ ํ์ด๋ธ์ด ์์ฑ๋ ๋ค์๋ ๋์ํ์์ผ๋ ์์ฑ๋๊ธฐ ์ ์๋ ์ค๋ฅ ๋ฐ์ 





### โจํด๊ฒฐ๋ฐฉ์

- ์์ ํ serializer

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
              nick1_lst = ['์ด์ดํ', '์ฑ์ฑํ', '๋ํธ๋ฅธ', '๊ฑด๊ฐํ', '์๋ด๊ธฐ']
              nick2_lst = ['์ฐธ๋๋ฌด', '์๋๋ฌด', '์ฌ๋ฆฌ๋ธ๋๋ฌด', '์ผ์๋๋ฌด', '๊ทค๋๋ฌด']
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

- nickname default ๊ฐ์ `data['nickname'] = self._validated_data.get('nickname', full_nickname)`์์ ์ค์ ํด์ผํจ

- `get_cleaned_data`ํจ์ ๋ฐ ํด๋์ค ๋ด์์ User ๋ชจ๋ธ์ ์ ๊ทผ์ User ํ์ด๋ธ์ด ์์ฑ๋๊ธฐ ์ ์ด๊ธฐ ๋๋ฌธ์ ์ธ์ ๋ถ๊ฐ๋ฅ
- ๊ธฐ์กด์ `nickname = serializers.CharField(max_length=15, default=full_nickname)` ์ฝ๋์์ `default=` ์ธ์๋ ์ค๋ฅ ๋ฐ์