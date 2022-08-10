# 📌Django 한국어, 한국시간 설정

한국어, 한국시간 설정

auto_now_add, auto_now

------------------------------------

[TOC]



### ✨문제상황

- 모델 설계 중 `created_at = models.DateTimeField(auto_now_add=True)`를 작성하면 한국 시간이 아니라 국제 표준 시간으로 저장됨
- 시간을 저장할 때 한국 시간으로 저장하고자 함





### ✨해결방안

- 기본 설정

  ```python
  # project/settings.py
  
  LANGUAGE_CODE = 'en-us'
  TIME_ZONE = 'UTC'
  USE_I18N = True
  USE_L10N = True
  USE_TZ = True
  ```

- 한국어, 한국시간 설정

  - 반드시 `USE_TZ = False` 설정

  ```python
  # project/settings.py
  
  LANGUAGE_CODE = 'ko-kr'
  TIME_ZONE = 'Asia/Seoul'
  USE_I18N = True
  USE_L10N = True
  USE_TZ = False
  ```





### ✨`auto_now_add`와 `auto_now`

- `auto_now_add`
  - 데이터 최초 저장 시 현재 날짜와 시간을 저장
  - 생성 당시의 날짜와 시간
- `auto_now`
  - 데이터가 저장될 때마다 현재 날짜와 시간을 저장
  - 수정 당시의 날짜와 시간

