# 📌Django QuerySet Method - filter

쿼리셋을 반환하는 메서드 filter의 lookup

----------------------------------

[TOC]



### ✨filter

- [공식문서](https://docs.djangoproject.com/en/4.1/ref/models/querysets/#filter)
- 주어진 lookup 파라미터에 매치하는 오브젝트를 포함하는 새로운 쿼리셋을 반환
- lookup 파라미터는 반드시 정해진 형식으로 사용해야하며 복수의 파라미터는 SQL문의 AND로 조인
  - [공식문서](https://docs.djangoproject.com/en/4.1/ref/models/querysets/#field-lookups)





### ✨exact

- 정확히 값이 일치하는 데이터
- None을 찾는 것은 SQL NULL을 찾는 것과 같음 (isnull)

```python
Entry.objects.get(id__exact=14)
# get은 쿼리셋이 아닌 객체 반환
# Entry.objects.filter(id__exact=14).get()
Entry.objects.get(id__exact=None)
```





### ✨iexact

- 대소문자 구분 없이 값이 일치하는 데이터
- None을 찾는 것은 SQL NULL을 찾는 것과 같음 (isnull)
- `sqlite`를 사용하고 `non-ASCII strings`(ASCII코드가 아닌 Unicode, EBCDIC 등)을 사용한다면 `exact`로 동작
  - [공식문서](https://docs.djangoproject.com/en/4.1/ref/databases/#substring-matching-and-case-sensitivity)

```py
Blog.objects.filter(name__iexact='beatles blog')

# 'Beatles Blog', 'beatles blog', 'BeAtLes BLoG' 등
```





### ✨contains

- 정확히 일치하는 값을 포함하는 데이터
- `sqlite`를 사용한다면 `icontains`로 동작
  - [공식문서](https://docs.djangoproject.com/en/4.1/ref/databases/#substring-matching-and-case-sensitivity)

```python
Entry.objects.filter(headline__contains='Lennon')

# 'Lennon honored today'는 매치되지만 'lennon honored today'는 매치되지 않음
```





### ✨icontains

- 대소문자 구분 없이 일치하는 값을 포함하는 데이터

```python
Entry.objects.filter(headline__icontains='Lennon')

# 'Lennon honored today', 'lennon honored today' 모두 매치
```





### ✨in

- list, tuple, queryset, string과 같이 iterable한 대상의 원소를 조회

```python
Entry.objects.filter(id__in=[1, 3, 4])
Entry.objects.filter(headline__in='abc')

SELECT ... WHERE id IN (1, 3, 4);
SELECT ... WHERE headline IN ('a', 'b', 'c');
```

- 쿼리셋 사용 가능

```python
inner_qs = Blog.objects.filter(name__contains='Cheddar')
entries = Entry.objects.filter(blog__in=inner_qs)

SELECT ... WHERE blog.id IN (SELECT id FROM ... WHERE NAME LIKE '%Cheddar%')
```

- `values()` 또는 `values_list()`를 사용하여 반환되는 쿼리셋을 in lookup에 사용한다면, 반드시 하나의 필드값만 사용

```python
# 정상적으로 작동
inner_qs = Blog.objects.filter(name__contains='Ch').values('name')
entries = Entry.objects.filter(blog__name__in=inner_qs)

# TypeError 발생
inner_qs = Blog.objects.filter(name__contains='Ch').values('name', 'id')
entries = Entry.objects.filter(blog__name__in=inner_qs)
```





### ✨gt, gte, lt, lte

- 더 큰, 크거가 같은, 더 작은, 작거나 같은 데이터

```python
Entry.objects.filter(id__gt=4)
```





### ✨startswith

- 정확히 일치하는 값으로 시작하는 데이터
- `sqlite`를 사용한다면 `istartswith`로 동작

```python
Entry.objects.filter(headline__startswith='Lennon')

SELECT ... WHERE headline LIKE 'Lennon%';
```





### ✨istartswith

- 대소문자 구분 없이 일치하는 값으로 시작하는 데이터

```python
Entry.objects.filter(headline__istartswith='Lennon')

SELECT ... WHERE headline ILIKE 'Lennon%';
```





### ✨endswith

- 정확히 일치하는 값으로 끝나는 데이터
- `sqlite`를 사용한다면 `iendswith`로 동작

```python
Entry.objects.filter(headline__endswith='Lennon')

SELECT ... WHERE headline LIKE '%Lennon';
```





### ✨iendswith

- 대소문자 구분 없이 일치하는 값으로 끝나는 데이터

```python
Entry.objects.filter(headline__iendswith='Lennon')

SELECT ... WHERE headline ILIKE '%Lennon'
```





### ✨range

- 시작과 끝을 포함하여 범위에 해당하는 데이터
- SQL BETWEEN을 사용하는 모든 곳에 사용 가능
  - 날짜, 숫자, 문자

```python
import datetime
start_date = datetime.date(2005, 1, 1)
end_date = datetime.date(2005, 3, 31)
Entry.objects.filter(pub_date__range=(start_date, end_date))

SELECT ... WHERE pub_date BETWEEN '2005-01-01' and '2005-03-31';
```

- DateTimeField를 사용한다면 마지막 날은 포함하지 않음
- DateTimeField는 주어진 날의 0시를 기준으로 함
- 위 예시에서 pub_date가 DateTimeField라면 다음 SQL문과 같음

```
SELECT ... WHERE pub_date BETWEEN '2005-01-01 00:00:00' and '2005-03-31 00:00:00';
```

