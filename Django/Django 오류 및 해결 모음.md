# 📌Django 오류 및 해결 모음

문법, 오타 등으로 인한 사소한 오류 및 해결

----------------------------------------

[TOC]



### ✨serializer 오류

```bash
AttributeError: 'tuple' object has no attribute 'values'
```

- 튜플 데이터를 사용하지 않았는데 튜플 오류가 발생

- serializer를 정의할 때 `class Meta:`를 작성했는지 확인하기

- 오류가 발생한 코드

  ```python
  class 상위Serializer(serializers.ModelSerializer):
      
      class 하위Serializer(serializers.ModelSerializer):
  
          model = 하위모델
          fields = '__all__'
  
      n-model_set = 하위Serializer(many=True, read_only=True)
  
      class Meta:
  
          model = 상위모델
          fields = '__all__'
  ```

- 오류를 해결한 코드

  ```python
  class 상위Serializer(serializers.ModelSerializer):
      
      class 하위Serializer(serializers.ModelSerializer):
  
          class Meta:
          	model = 하위모델
          	fields = '__all__'
  
      n-model_set = 하위Serializer(many=True, read_only=True)
  
      class Meta:
  
          model = 상위모델
          fields = '__all__'
  ```

  