# C언어 기초

[코드업 100제](https://codeup.kr/problemsetsol.php?psid=23)



### 목차

- [출력](#출력)
  - [문장 출력하기](#문장-출력하기)
  - [공백을 둔 문장 출력하기](#공백을-둔-문장-출력하기)
  - [줄 바꿔 출력하기](#줄-바꿔-출력하기)
  - [따옴표 출력하기](#따옴표-출력하기)
  - [특수문자 출력하기](#특수문자-출력하기)
  - [파일 경로 출력하기](#파일-경로-출력하기)
  - [특수문자 출력 연습](#특수문자-출력-연습)
- [입출력](#입출력)
  - [정수 1개 입력받아 그대로 출력하기](#정수-1개-입력받아-그대로-출력하기)
  - [문자 1개 입력받아 그대로 출력하기](#문자-1개-입력받아-그대로-출력하기)
  - [실수 1개 입력받아 그대로 출력하기](#실수-1개-입력받아-그대로-출력하기)
  - [정수 2개 입력받아 그대로 출력하기](#정수-2개-입력받아-그대로-출력하기)
  - [문자 2개 입력받아 순서 바꿔 출력하기](#문자-2개-입력받아-순서-바꿔-출력하기)
  - [실수 입력받아 둘째 자리까지 출력하기](#실수-입력받아-둘째-자리까지-출력하기)
  - [정수 1개 입력받아 3번 출력하기](#정수-1개-입력받아-3번-출력하기)
  - [시간 입력받아 그대로 출력하기](#시간-입력받아-그대로-출력하기)
  - [연월일 입력받아 그대로 출력하기](#연월일-입력받아-그대로-출력하기)
  - [주민번호 입력받아 형태 바꿔 출력하기](#주민번호-입력받아-형태-바꿔-출력하기)
  - [단어 1개 입력받아 그대로 출력하기](#단어-1개-입력받아-그대로-출력하기)
  - [문장 1개 입력받아 그대로 출력하기](#문장-1개-입력받아-그대로-출력하기)
  - [실수 1개 입력받아 부분별로 출력하기](#실수-1개-입력받아-부분별로-출력하기)
  - [단어 1개 입력받아 나누어 출력하기](#단어-1개-입력받아-나누어-출력하기)
  - [정수 1개 입력받아 나누어 출력하기](#정수-1개-입력받아-나누어-출력하기)
  - [시분초 입력받아 분만 출력하기](#시분초-입력받아-분만-출력하기)
  - [년월일 입력받아 형식 바꿔 출력하기](#년월일-입력받아-형식-바꿔-출력하기)
- [데이터형](#데이터형)
  - [정수 1개 입력받아 그대로 출력하기2](#정수-1개-입력받아-그대로-출력하기2)
  - [실수 1개 입력받아 그대로 출력하기2](#실수-1개-입력받아-그대로-출력하기2)
  - [정수 1개 입력받아 그대로 출력하기3](#정수-1개-입력받아-그대로-출력하기3)
- [출력변환](#출력변환)
  - [10진 정수 1개 입력받아 8진수로 출력하기](#10진-정수-1개-입력받아-8진수로-출력하기)
  - [10진 정수 입력받아 16진수로 출력하기1](#10진-정수-입력받아-16진수로-출력하기1)
  - [10진 정수 입력받아 16진수로 출력하기2](#10진-정수-입력받아-16진수로-출력하기2)
  - [8진 정수 1개 입력받아 10진수로 출력하기](#8진-정수-1개-입력받아-10진수로-출력하기)
  - [16진 정수 1개 입력받아 8진수로 출력하기](#16진-정수-1개-입력받아-8진수로-출력하기)
  - [영문자 1개 입력받아 10진수로 출력하기](#영문자-1개-입력받아-10진수로-출력하기)
  - [정수 입력받아 아스키 문자로 출력하기](#정수-입력받아-아스키-문자로-출력하기)
- [산술연산](#산술연산)
  - [정수 2개 입력받아 합 출력하기1 2](#정수-2개-입력받아-합-출력하기1-2)
  - [정수 1개 입력받아 부호 바꿔 출력하기](#정수-1개-입력받아-부호-바꿔-출력하기)
  - [정수 2개 입력받아 나눈 몫 출력하기](#정수-2개-입력받아-나눈-몫-출력하기)
  - [정수 2개 입력받아 나눈 나머지 출력하기](#정수-2개-입력받아-나눈-나머지-출력하기)
  - [정수 1개 입력받아 1 더해 출력하기](#정수-1개-입력받아-1-더해-출력하기)
  - [정수 2개 입력받아 자동 계산하기](#정수-2개-입력받아-자동-계산하기)
  - [정수 3개 입력받아 합과 평균 출력하기](#정수-3개-입력받아-합과-평균-출력하기)
- [비트시프트연산](#비트시프트연산)
  - [정수 1개 입력받아 2배 곱해 출력하기](#정수-1개-입력받아-2배-곱해-출력하기)
  - [한 번에 2의 거듭제곱 배로 출력하기](#한-번에-2의-거듭제곱-배로-출력하기)
- [비교연산](#비교연산)
  - [두 정수 입력받아 비교하기1](#두-정수-입력받아-비교하기1)
  - [두 정수 입력받아 비교하기2](#두-정수-입력받아-비교하기2)
  - [두 정수 입력받아 비교하기3](#두-정수-입력받아-비교하기3)
  - [두 정수 입력받아 비교하기4](#두-정수-입력받아-비교하기4)
- [논리연산](#논리연산)
  - [참 거짓 바꾸기](#참-거짓-바꾸기)
  - [둘 다 참일 경우만 참 출력하기](#둘-다-참일-경우만-참-출력하기)
  - [하나라도 참이면 참 출력하기](#하나라도-참이면-참-출력하기)
  - [참/거짓이 서로 다를 때에만 참 출력하기](#참거짓이-서로-다를-때에만-참-출력하기)
  - [참/거짓이 서로 같을 때에만 참 출력하기](#참거짓이-서로-같을-때에만-참-출력하기)
  - [둘 다 거짓일 경우만 참 출력하기](#둘-다-거짓일-경우만-참-출력하기)
- [비트단위논리연산](#비트단위논리연산)
  - [비트단위로 NOT 하여 출력하기](#비트단위로-NOT-하여-출력하기)
  - [비트단위로 AND 하여 출력하기](#비트단위로-AND-하여-출력하기)
  - [비트단위로 OR 하여 출력하기](#비트단위로-OR-하여-출력하기)
  - [비트단위로 XOR 하여 출력하기](#비트단위로-XOR-하여-출력하기)
- [삼항연산](#삼항연산)
  - [두 정수 입력받아 큰 수 출력하기](#두-정수-입력받아-큰-수-출력하기)
  - [정수 3개 입력받아 가장 작은 수 출력하기](#정수-3개-입력받아-가장-작은-수-출력하기)
- [조건/선택실행구조](#조건선택실행구조)
  - [정수 3개 입력받아 짝수만 출력하기](#정수-3개-입력받아-짝수만-출력하기)
  - [정수 3개 입력받아 짝/홀 출력하기](#정수-3개-입력받아-짝홀-출력하기)
  - [정수 1개 입력받아 분석하기](#정수-1개-입력받아-분석하기)
  - [정수 1개 입력받아 평가 출력하기](#정수-1개-입력받아-평가-출력하기)
  - [평가 입력받아 다르게 출력하기](#평가-입력받아-다르게-출력하기)
  - [월 입력받아 계절 출력하기](#월-입력받아-계절-출력하기)
- [반복실행구조](#반복실행구조)
  - [0 입력될 때까지 무한 출력하기1](#0-입력될-때까지-무한-출력하기1)
  - [정수 입력받아 계속 출력하기](#정수-입력받아-계속-출력하기)
  - [0 입력될 때까지 무한 출력하기2](#0-입력될-때까지-무한-출력하기2)
  - [정수 1개 입력받아 카운트다운 출력하기1](#정수-1개-입력받아-카운트다운-출력하기1)
  - [정수 1개 입력받아 카운트다운 출력하기2](#정수-1개-입력받아-카운트다운-출력하기2)
  - [문자 1개 입력받아 알파벳 출력하기](#문자-1개-입력받아-알파벳-출력하기)
  - [정수 1개 입력받아 그 수까지 출력하기](#정수-1개-입력받아-그-수까지-출력하기)
- [종합](#종합)
  - [짝수 합 구하기](#짝수-합-구하기)
  - [원하는 문자가 입력될 때까지 반복 출력하기](#원하는-문자가-입력될-때까지-반복-출력하기)
  - [언제까지 더해야 할까?](#언제까지-더해야-할까)
  - [주사위를 2개 던지면?](#주사위를-2개-던지면)
  - [16진수 구구단?](#16진수-구구단)
  - [3 6 9 게임의 왕이 되자!](#3-6-9-게임의-왕이-되자)
  - [빛 섞어 색 만들기](#빛-섞어-색-만들기)
  - [소리 파일 저장용량 계산하기](#소리-파일-저장용량-계산하기)
  - [그림 파일 저장용량 계산하기](#그림-파일-저장용량-계산하기)
  - [여기까지! 이제 그만~](#여기까지-이제-그만)
  - [3의 배수는 통과?](#3의-배수는-통과)
  - [수 나열하기1](#수-나열하기1)
  - [수 나열하기2](#수-나열하기2)
  - [수 나열하기3](#수-나열하기3)
  - [함께 문제 푸는 날](#함께-문제-푸는-날)
- [1차원배열](#1차원배열)
  - [이상한 출석 번호 부르기1](#이상한-출석-번호-부르기1)
  - [이상한 출석 번호 부르기2](#이상한-출석-번호-부르기2)
  - [이상한 출석 번호 부르기3](#이상한-출석-번호-부르기3)
- [2차원배열](#2차원배열)
  - [바둑판에 흰 돌 놓기](#바둑판에-흰-돌-놓기)
  - [바둑알 십자 뒤집기](#바둑알-십자-뒤집기)
  - [설탕과자 뽑기](#설탕과자-뽑기)
  - [성실한 개미](#성실한-개미)



### 출력

##### 문장 출력하기

- `printf("문장")`

```c
#include <stdio.h>

int main()
{
    printf("Hello");
    return 0;
}
```



##### 공백을 둔 문장 출력하기

- `printf("문장1 문장2")`

```c
#include <stdio.h>

int main()
{
    printf("Hello World");
    return 0;
}
```



##### 줄 바꿔 출력하기

- `printf("문장1\n문장2")`

```c
#include <stdio.h>

int main()
{
    printf("Hello\nWorld");
    return 0;
}
```



##### 따옴표 출력하기

- `\'` 또는 `\"` 

```c
#include <stdio.h>

int main()
{
    printf("\'Hello\'");
    return 0;
}
```

```c
#include <stdio.h>

int main()
{
    printf("\"Hello World\"");
    return 0;
}
```



##### 특수문자 출력하기

- `%` 출력은 `%%`

```c
#include <stdio.h>

int main()
{
    printf("\"!@#$%%^&*()\"");
    return 0;
}
```



##### 파일 경로 출력하기

- `\` 출력은 `\\`

```c
#include <stdio.h>

int main()
{
    printf("\"C:\\Download\\hello.cpp\"");
    return 0;
}
```



##### 특수문자 출력 연습

- 유니코드 특수문자 출력은 `\u코드`

```
다음과 같은 모양 출력하기
┌┬┐
├┼┤
└┴┘
```

```c
#include <stdio.h>

int main()
{
    printf("\u250C\u252C\u2510\n\u251C\u253C\u2524\n\u2514\u2534\u2518");
    return 0;
}
```



### 입출력

##### 정수 1개 입력받아 그대로 출력하기

- 정수형(int)으로 변수 선언 `int n`
- 변수에 정수값 저장한 후 `scanf("%d", &n)` 저장된 정수값 출력 `printf("%d", n)`

```c
#include <stdio.h>

int main()
{
    int n;
    scanf("%d", &n);
    printf("%d", n);
    
    return 0;
}
```



##### 문자 1개 입력받아 그대로 출력하기

- 문자형(char)으로 변수 선언 `char x`
- 변수에 문자 저장한 후 `scanf("%c", &x)` 저장된 문자 출력 `printf("%c", x)`

```c
#include <stdio.h>

int main()
{
    char x;
    scanf("%c", &x);
    printf("%c", x);
    
    return 0;
}
```



##### 실수 1개 입력받아 그대로 출력하기

- 실수형(float)으로 변수 선언 `float x`
- 변수에 실수값 저장한 후 `scanf("%f", &x)` 저장된 실수값 출력 `printf("%f", x)`

```c
#include <stdio.h>

int main()
{
    float x;
    scanf("%f", &x);
    printf("%f", x);
    
    return 0;
}
```



##### 정수 2개 입력받아 그대로 출력하기

- 정수형(int)으로 변수 두개 선언 `int a, b`
- 공백으로 데이터를 구분하여 입력

```c
#include <stdio.h>

int main()
{
    int a, b;
    scanf("%d %d", &a, &b);
    printf("%d %d", a, b);
    
    return 0;
}
```



##### 문자 2개 입력받아 순서 바꿔 출력하기

- x, y 입력 y, x 출력
- 공백으로 데이터를 구분하여 입력

```c
#include <stdio.h>

int main()
{
    char x, y;
    scanf("%c %c", &x, &y);
    printf("%c %c", y, x);
    
    return 0;
}
```



##### 실수 입력받아 둘째 자리까지 출력하기

- `%.3f`: 소수점 이하 넷째 자리에서 반올림하여 소수점 이하 셋째 자리까지 출력
- `%.2f`: 소수점 이하 셋째 자리에서 반올림하여 소수점 이하 둘째 자리까지 출력

```c
#include <stdio.h>

int main()
{
    float x;
    scanf("%f", &x);
    printf("%.2f", x);
    
    return 0;
}
```



##### 정수 1개 입력받아 3번 출력하기

- 출력문 `%d`와 `%d` 사이에 공백을 넣어 숫자를 공백으로 구분하여 출력

```c
#include <stdio.h>

int main()
{
    int n;
    scanf("%d", &n);
    printf("%d %d %d", n, n, n);
    
    return 0;
}
```



##### 시간 입력받아 그대로 출력하기

- `scanf("%d:%d", &h, &m)`: 콜론을 기준으로 두 수가 각 변수에 저장됨
- `3:16`과 같이 `:`을 포함하여 입력

```c
#include <stdio.h>

int main()
{
    int h, m;
    scanf("%d:%d", &h, &m);
    printf("%d:%d", h, m);
    
    return 0;
}
```



##### 연월일 입력받아 그대로 출력하기

- `2023.1.4`과 같이 `.`으로 구분하여 입력
- `2023.01.04`와 같이 yyyy.mm.dd 형식으로 출력
- `%02d`: 2칸을 사용하여 출력, 한 자리 수인 경우 앞에 0을 붙여 출력

```c
#include <stdio.h>

int main()
{
    int y, m, d;
    scanf("%d.%d.%d", &y, &m, &d);
    printf("%04d.%02d.%02d", y, m, d);
    
    return 0;
}
```



##### 주민번호 입력받아 형태 바꿔 출력하기

- `123456-1234567` 형태를 `1234561234567` 형태로 출력

```c
#include <stdio.h>

int main()
{
    int a, b;
    scanf("%d-%d", &a, &b);
    printf("%06d%07d", a, b);
    
    return 0;
}
```



##### 단어 1개 입력받아 그대로 출력하기

- 50자 이하의 단어 char 선언시 `char data[51]`
- 입출력시 `%c`가 아닌 `%s`

```c
#include <stdio.h>

int main()
{
    char data[51]="";
    scanf("%s", data);
    printf("%s", data);
    
    return 0;
}
```



##### 문장 1개 입력받아 그대로 출력하기

- 공백 문자가 포함된 문장
- `fgets(data, 2000, stdin)`: 공백이 포함된 문장을 키보드(stdin)로 입력받아, 최대 2000자까지 data[] 공간에 저장, 엔터가 입력될 때까지 저장
- `scanf("%[^\n]", data)`: 엔터가 입력될 때까지 저장

```c
#include <stdio.h>

int main()
{
    char data[2001];
    fgets(data, 2000, stdin);
    printf("%s", data);
    
    return 0;
}
```

```c
#include <stdio.h>

int main()
{
    char data[2001];
    scanf("%[^\n]", data);
    printf("%s", data);
    
    return 0;
}
```



##### 실수 1개 입력받아 부분별로 출력하기

- 실수 1개를 입력받아 정수 부분과 실수 부분으로 나누어 출력

```c
#include <stdio.h>

int main()
{
    int a, b;
    scanf("%d.%d", &a, &b);
    printf("%d\n%d", a, b);
    
    return 0;
}
```



##### 단어 1개 입력받아 나누어 출력하기

- for 반복문에서 i 선언시 자료형 명시 `int i=0`
- 문자열 마지막에 `NULL` 을 넣어 문장 또는 단어의 마지막임을 나타냄
- 문자로는 `'\0'`, 정수값은 `0`, `NULL`로 사용 가능

```c
#include <stdio.h>

int main()
{
    char data[21];
    scanf("%s", data);
    for (int i=0; data[i]!='\0'; i++)
    {
        printf("\'%c\'\n", data[i]);
    }
    
    return 0;
}
```



##### 정수 1개 입력받아 나누어 출력하기

- 다섯 자리의 정수 1개를 입력받아 각 자리별로 나누어 출력
- 입력시 칸 수를 지정
- `[70000]`과 같이 출력하기 위해 `printf("\[%d\]", a*10000)`처럼 `\` 사용에 주의

```c
#include <stdio.h>

int main()
{
    int a, b, c, d, e;
    scanf("%1d%1d%1d%1d%1d", &a, &b, &c, &d, &e);
    printf("\[%d\]\n\[%d\]\n\[%d\]\n\[%d\]\n\[%d\]", a*10000, b*1000, c*100, d*10, e);
    
    return 0;
}
```



##### 시분초 입력받아 분만 출력하기

- 시:분:초 형식으로 입력하면 분만 출력

```c
#include <stdio.h>

int main()
{
    int h, m, s;
    scanf("%d:%d:%d", &h, &m, &s);
    printf("%d", m);
    
    return 0;
}
```



##### 년월일 입력받아 형식 바꿔 출력하기

- 년월일을 `.`으로 구분하여 입력하면 일월년으로 바꾸어 `-`로 구분하여 출력

```c
#include <stdio.h>

int main()
{
    int y, m, d;
    scanf("%d.%d.%d", &y, &m, &d);
    printf("%02d-%02d-%04d", d, m, y);
    
    return 0;
}
```



### 데이터형

##### 정수 1개 입력받아 그대로 출력하기2

- 입력되는 정수의 범위는 0 ~ 4,294,967,295
- `int`: -2,147,483,648 ~ +2,147,483,647
- `unsigned int`: 0 ~ 4,294,967,295
- `%d`가 아닌 `%u`임에 주의

```c
#include <stdio.h>

int main()
{
    unsigned int n;
    scanf("%u", &n);
    printf("%u", n);
    
    return 0;
}
```



##### 실수 1개 입력받아 그대로 출력하기2

- 입력되는 실수의 범위는 `+- 1.7*(10**(-308)) ~ +- 1.7*(10**308)`
- 소수점 아래 12자리에서 반올림하여 소수점 아래 11자리까지 출력

- `float`: `+- 3.4*(10**(-38)) ~ +- 3.4*(10**38)`
- `double`: `+- 1.7*(10**(-308)) ~ +- 1.7*(10**308)`

- `double`은 `float`보다 더 정확하게 저장할 수 있지만, 2배의 저장 공간이 필요
- `%f`가 아닌 `%lf`임에 주의

```c
#include <stdio.h>

int main()
{
    double d;
    scanf("%lf", &d);
    printf("%.11lf", d);
    
    return 0;
}
```



##### 정수 1개 입력받아 그대로 출력하기3

- 입력되는 정수의 범위는 -9,223,372,036,854,775,808 ~ +9,223,372,036,854,775,807
- `int`: -2,147,483,648 ~ +2,147,483,647
- `long long int`: -9,223,372,036,854,775,808 ~ +9,223,372,036,854,775,807
- `%d`가 아닌 `%lld`임에 주의

```c
#include <stdio.h>

int main()
{
    long long int n;
    scanf("%lld", &n);
    printf("%lld", n);
    
    return 0;
}
```



### 출력변환

##### 10진 정수 1개 입력받아 8진수로 출력하기

- `%d`: 10진수
- `%o`: 8진수

```c
#include <stdio.h>

int main()
{
    int n;
    scanf("%d", &n);
    printf("%o", n);
    
    return 0;
}
```



##### 10진 정수 입력받아 16진수로 출력하기1

- `%d`: 10진수
- `%x`: 16진수 소문자

```c
#include <stdio.h>

int main()
{
    int n;
    scanf("%d", &n);
    printf("%x", n);
    
    return 0;
}
```



##### 10진 정수 입력받아 16진수로 출력하기2

- `%x`: 16진수 소문자
- `%X`: 16진수 대문자

```c
#include <stdio.h>

int main()
{
    int n;
    scanf("%d", &n);
    printf("%X", n);
    
    return 0;
}
```



##### 8진 정수 1개 입력받아 10진수로 출력하기

```c
#include <stdio.h>

int main()
{
    int n;
    scanf("%o", &n);
    printf("%d", n);
    
    return 0;
}
```



##### 16진 정수 1개 입력받아 8진수로 출력하기

```c
#include <stdio.h>

int main()
{
    int n;
    scanf("%x", &n);
    printf("%o", n);
    
    return 0;
}
```



##### 영문자 1개 입력받아 10진수로 출력하기

```c
#include <stdio.h>

int main()
{
    char x;
    scanf("%c", &x);
    printf("%d", x);
    
    return 0;
}
```



##### 정수 입력받아 아스키 문자로 출력하기

```c
#include <stdio.h>

int main()
{
    int n;
    scanf("%d", &n);
    printf("%c", n);
    
    return 0;
}
```



### 산술연산

##### 정수 2개 입력받아 합 출력하기1 2

```c
#include <stdio.h>

int main()
{
    long long int a, b;
    scanf("%lld %lld", &a, &b);
    printf("%lld", a+b);
    
    return 0;
}
```



##### 정수 1개 입력받아 부호 바꿔 출력하기

```c
#include <stdio.h>

int main()
{
    int n;
    scanf("%d", &n);
    printf("%d", n*(-1));
    
    return 0;
}
```



##### 문자 1개 입력받아 다음 문자 출력하기

```c
#include <stdio.h>

int main()
{
    char x;
    scanf("%c", &x);
    printf("%c", x+1);
    
    return 0;
}
```



##### 정수 2개 입력받아 나눈 몫 출력하기

```c
#include <stdio.h>

int main()
{
    int a, b;
    scanf("%d %d", &a, &b);
    printf("%d", a/b);
    
    return 0;
}
```



##### 정수 2개 입력받아 나눈 나머지 출력하기

```c
#include <stdio.h>

int main()
{
    int a, b;
    scanf("%d %d", &a, &b);
    printf("%d", a%b);
    
    return 0;
}
```



##### 정수 1개 입력받아 1 더해 출력하기

- `++n`과 `n++` 차이 주의
- `printf("%lld", ++n)`: 기존 변수 값에 1을 더한 후 출력
- `printf("%lld", n++)`: 기존 변수 값을 출력한 후 1을 더함

```c
#include <stdio.h>

int main()
{
    long long int n;
    scanf("%lld", &n);
    printf("%lld", ++n);
    
    return 0;
}
```



##### 정수 2개 입력받아 자동 계산하기

```c
#include <stdio.h>

int main()
{
    long long int a, b;
    scanf("%lld %lld", &a, &b);
    printf("%lld\n%lld\n%lld\n%lld\n%lld\n%.2f", a+b, a-b, a*b, a/b, a%b, (float)a/b);
    
    return 0;
}
```



##### 정수 3개 입력받아 합과 평균 출력하기

```c
#include <stdio.h>

int main()
{
    long long int a, b, c;
    scanf("%lld %lld %lld", &a, &b, &c);
    printf("%lld\n%.1f", a+b+c, (float)(a+b+c)/3);
    
    return 0;
}
```



### 비트시프트연산

##### 정수 1개 입력받아 2배 곱해 출력하기

- `<<`: 2진수 형태로 저장된 값에서 지정한 비트 수만큼 오른쪽에 0 추가
- `>>`: 2진수 형태로 저장된 값에서 지정한 비트 수만큼 왼쪽에 0(0또는 양의 정수인 경우)이나 1(음의 정수인 경우) 추가

```c
#include <stdio.h>

int main()
{
    int n;
    scanf("%d", &n);
    printf("%d", n<<1);
    
    return 0;
}
```



##### 한 번에 2의 거듭제곱 배로 출력하기

```c
#include <stdio.h>

int main()
{
    int a, b;
    scanf("%d %d", &a, &b);
    printf("%d", a<<b);
    
    return 0;
}
```



### 비교연산

##### 두 정수 입력받아 비교하기1

- `a`가 `b`보다 크면 `1`, `a`가 `b`보다 작거나 같으면 `0`을 출력

```c
#include <stdio.h>

int main()
{
    int a, b;
    scanf("%d %d", &a, &b);
    printf("%d", a>b);
    
    return 0;
}
```



##### 두 정수 입력받아 비교하기2

```c
#include <stdio.h>

int main()
{
    int a, b;
    scanf("%d %d", &a, &b);
    printf("%d", a==b);
    
    return 0;
}
```



##### 두 정수 입력받아 비교하기3

```c
#include <stdio.h>

int main()
{
    long long int a, b;
    scanf("%lld %lld", &a, &b);
    printf("%d", b>=a);
    
    return 0;
}
```



##### 두 정수 입력받아 비교하기4

```c
#include <stdio.h>

int main()
{
    long long int a, b;
    scanf("%lld %lld", &a, &b);
    printf("%d", a!=b);
    
    return 0;
}
```



### 논리연산

##### 참 거짓 바꾸기

```c
#include <stdio.h>

int main()
{
    int a;
    scanf("%d", &a);
    printf("%d", !a);
    
    return 0;
}
```



##### 둘 다 참일 경우만 참 출력하기

```c
#include <stdio.h>

int main()
{
    int a, b;
    scanf("%d %d", &a, &b);
    printf("%d", a&&b);
    
    return 0;
}
```



##### 하나라도 참이면 참 출력하기

```c
#include <stdio.h>

int main()
{
    int a, b;
    scanf("%d %d", &a, &b);
    printf("%d", a||b);
    
    return 0;
}
```



##### 참/거짓이 서로 다를 때에만 참 출력하기

```c
#include <stdio.h>

int main()
{
    int a, b;
    scanf("%d %d", &a, &b);
    printf("%d", (a&&!b)||(!a&&b));
    
    return 0;
}
```



##### 참/거짓이 서로 같을 때에만 참 출력하기

```c
#include <stdio.h>

int main()
{
    int a, b;
    scanf("%d %d", &a, &b);
    printf("%d", (a&&b)||(!a&&!b));
    
    return 0;
}
```



##### 둘 다 거짓일 경우만 참 출력하기

```c
#include <stdio.h>

int main()
{
    int a, b;
    scanf("%d %d", &a, &b);
    printf("%d", (!a&&!b));
    
    return 0;
}
```



### 비트단위논리연산

##### 비트단위로 NOT 하여 출력하기

```c
#include <stdio.h>

int main()
{
    int a;
    scanf("%d", &a);
    printf("%d", ~a);
    
    return 0;
}
```



##### 비트단위로 AND 하여 출력하기

```c
#include <stdio.h>

int main()
{
    int a, b;
    scanf("%d %d", &a, &b);
    printf("%d", a&b);
    
    return 0;
}
```



##### 비트단위로 OR 하여 출력하기

```c
#include <stdio.h>

int main()
{
    int a, b;
    scanf("%d %d", &a, &b);
    printf("%d", a|b);
    
    return 0;
}
```



##### 비트단위로 XOR 하여 출력하기

```c
#include <stdio.h>

int main()
{
    int a, b;
    scanf("%d %d", &a, &b);
    printf("%d", a^b);
    
    return 0;
}
```



### 삼항연산

##### 두 정수 입력받아 큰 수 출력하기

- 3항 연산자: `조건식 ? (참일 때의 값) : (거짓일 때의 값)`

```c
#include <stdio.h>

int main()
{
    int a, b;
    scanf("%d %d", &a, &b);
    printf("%d", a>b?a:b);
    
    return 0;
}
```



##### 정수 3개 입력받아 가장 작은 수 출력하기

```c
#include <stdio.h>

int main()
{
    int a, b, c;
    scanf("%d %d %d", &a, &b, &c);
    printf("%d", (a<b?a:b)<c?(a<b?a:b):c);
    
    return 0;
}
```



### 조건/선택실행구조

##### 정수 3개 입력받아 짝수만 출력하기

```c
#include <stdio.h>

int main()
{
    int a, b, c;
    scanf("%d %d %d", &a, &b, &c);
    if (a%2==0)
    {
        printf("%d\n", a);
    }
    
    if (b%2==0)
    {
        printf("%d\n", b);
    }
    
    if (c%2==0)
    {
        printf("%d", c);
    }
    
    return 0;
}
```



##### 정수 3개 입력받아 짝/홀 출력하기

```c
#include <stdio.h>

int main()
{
    int a, b, c;
    scanf("%d %d %d", &a, &b, &c);
    
    if (a%2==1)
    {
        printf("odd\n");
    }
    
    else
    {
        printf("even\n");
    }
    
    if (b%2==1)
    {
        printf("odd\n");
    }
    
    else
    {
        printf("even\n");
    }
    
    if (c%2==1)
    {
        printf("odd\n");
    }
    
    else
    {
        printf("even");
    }
    
    return 0;
}
```



##### 정수 1개 입력받아 분석하기

```c
#include <stdio.h>

int main()
{
    int a;
    scanf("%d", &a);
    
    if (a<0)
    {
        if (a%2==0)
        {
            printf("minus\neven");
        }
        
        else
        {
            printf("minus\nodd");
        }
    }
    
    else
    {
        if (a%2==1)
        {
            printf("plus\nodd");
        }
        
        else
        {
            printf("plus\neven");
        }
    }
    
    return 0;
}
```



##### 정수 1개 입력받아 평가 출력하기

```c
#include <stdio.h>

int main()
{
    int a;
    scanf("%d", &a);
    
    if (a>=90&&a<=100)
    {
        printf("A");
    }
    
    else if (a>=70)
    {
        printf("B");
    }
    
    else if (a>=40)
    {
        printf("C");
    }
    
    else
    {
        printf("D");
    }
    
    return 0;
}
```



##### 평가 입력받아 다르게 출력하기

- `switch()`에 주어지는 값은 정수값만 가능 (문자도 아스키코드 정수값이기 때문에 가능)
- `break`를 쓰지 않으면 이후의 명령들도 계속 실행
- `default`는 제시된 case를 제외한 나머지 모든 경우에 실행

```c
#include <stdio.h>

int main()
{
    char x;
    scanf("%c", &x);
    
    switch(x)
    {
        case 'A':
            printf("best!!!");
            break;
        case 'B':
            printf("good!!");
            break;
        case 'C':
            printf("run!");
            break;
        case 'D':
            printf("slowly~");
            break;
        default:
            printf("what?");
    }
    
    return 0;
}
```



##### 월 입력받아 계절 출력하기

```c
#include <stdio.h>

int main()
{
    int a;
    scanf("%d", &a);
    
    switch(a)
    {
        case 1:
        case 2:
        case 12:
            printf("winter");
            break;
        case 3:
        case 4:
        case 5:
            printf("spring");
            break;
        case 6:
        case 7:
        case 8:
            printf("summer");
            break;
        case 9:
        case 10:
        case 11:
            printf("fall");
            break;
    }
    
    return 0;
}
```



### 반복실행구조

##### 0 입력될 때까지 무한 출력하기1

```c
#include <stdio.h>

int main()
{
    int a;
reload:  // 레이블
    scanf("%d", &a);
    if (a!=0)
    {
        printf("%d\n", a);
        goto reload;  // 레이블이 작성된 곳으로 프로그램의 실행을 바꿈
    }
    
    return 0;
}
```



##### 정수 입력받아 계속 출력하기

```c
#include <stdio.h>

int main()
{
    int n;
    scanf("%d", &n);
    
    int m;
reload:
    scanf("%d", &m);
    printf("%d\n", m);
    n = n - 1;
    if (n>0)
    {
        goto reload;
    }
    
    return 0;
}
```



##### 0 입력될 때까지 무한 출력하기2

- c언어에서는 1을 True(또는 true)로 바꿔 사용할 수 없음에 주의

```c
#include <stdio.h>

int main()
{
    int a;
    
    while (1)
    {
        scanf("%d", &a);
        if (a==0)
        {
            break;
        }
        
        else
        {
            printf("%d\n", a);
        }
    }
    
    return 0;
}
```



##### 정수 1개 입력받아 카운트다운 출력하기1

```c
#include <stdio.h>

int main()
{
    int a;
    scanf("%d", &a);
    
    while (a!=0)
    {
        printf("%d\n", a);
        a = a - 1;
    }
    
    return 0;
}
```



##### 정수 1개 입력받아 카운트다운 출력하기2

```c
#include <stdio.h>

int main()
{
    int a;
    scanf("%d", &a);
    
    while (a!=0)
    {
        a = a - 1;
        printf("%d\n", a);
    }
    
    return 0;
}
```



##### 문자 1개 입력받아 알파벳 출력하기

- `int`가 아닌 `char`임에 주의
- `do ~ while`은 `while (조건)` 뒤에 반드시 `;`을 붙여야 함
- `while(조건) {...}`과의 차이점은 무조건 한 번은 실행된다는 것

```c
#include <stdio.h>

int main()
{
    char x;
    char y='a';
    scanf("%c", &x);
    
    do
    {
        printf("%c ", y);
        y += 1;
    }
    while (y<=x);
    
    return 0;
}
```



##### 정수 1개 입력받아 그 수까지 출력하기

```c
#include <stdio.h>

int main()
{
    int a;
    scanf("%d", &a);
    
    for (int i=0; i<=a; i++)
    {
        printf("%d\n", i);
    }
    
    return 0;
}
```



### 종합

##### 짝수 합 구하기

```c
#include <stdio.h>

int main()
{
    int a, sum;
    sum = 0;
    scanf("%d", &a);
    
    for (int i=1; i<=a; i++)
    {
        if (i%2 == 0)
        {
            sum += i;
        }
    }
    
    printf("%d", sum);
    
    return 0;
}
```



##### 원하는 문자가 입력될 때까지 반복 출력하기

```c
#include <stdio.h>

int main()
{
    char x;
    scanf("%c", &x);
    
    while (x!='q')
    {
        if (x!=' ')
        {
            printf("%c\n", x);
        }
        scanf("%c", &x);
    }
    
    printf("%c", x);
    
    return 0;
}
```



##### 언제까지 더해야 할까?

```c
#include <stdio.h>

int main()
{
    int a, b;
    int cnt=0;
    b=0;
    scanf("%d", &a);
    
    while (cnt < a)
    {
        cnt = cnt + b + 1;
        b = b + 1;
    }
    
    printf("%d", b);
    
    return 0;
}
```



##### 주사위를 2개 던지면?

```c
#include <stdio.h>

int main()
{
    int n, m;
    scanf("%d %d", &n, &m);
    
    for (int i=1; i<=n; i++)
    {
        for (int j=1; j<=m; j++)
        {
            printf("%d %d\n", i, j);
        }
    }
    
    return 0;
}
```



##### 16진수 구구단?

```c
#include <stdio.h>

int main()
{
    int a;
    scanf("%X", &a);
    for (int i=1; i <=15; i++)
    {
        printf("%X*%X=%X\n", a, i, a*i);
    }
    
    return 0;
}
```



##### 3 6 9 게임의 왕이 되자!

```c
#include <stdio.h>

int main()
{
    int a;
    scanf("%d", &a);
    for (int i=1; i<=a; i++)
    {
        if (i%3==0)
        {
            printf("X ");
        }
        
        else
        {
            printf("%d ", i);
        }
    }
    
    return 0;
}
```



##### 빛 섞어 색 만들기

```c
#include <stdio.h>

int main()
{
    int r, g, b;
    scanf("%d %d %d", &r, &g, &b);
    for (int i=0; i<r; i++)
    {
        for (int j=0; j<g; j++)
        {
            for (int k=0; k<b; k++)
            {
                printf("%d %d %d\n", i, j, k);
            }
        }
    }
    printf("%d", r*g*b);
    
    return 0;
}
```



##### 소리 파일 저장용량 계산하기

```c
#include <stdio.h>

int main()
{
    int h, b, c, s;
    scanf("%d %d %d %d", &h, &b, &c, &s);
    printf("%.1f MB", (float)h*b*c*s/8/1024/1024);
    
    return 0;
}
```



##### 그림 파일 저장용량 계산하기

```c
#include <stdio.h>

int main()
{
    int w, h, b;
    scanf("%d %d %d", &w, &h, &b);
    printf("%.2f MB", (float)w*h*b/8/1024/1024);
    
    return 0;
}
```



##### 여기까지! 이제 그만~

```c
#include <stdio.h>

int main()
{
    int a, b;
    scanf("%d", &a);
    b=0;
    for (int i=1; b<a; i++)
    {
        b += i;
    }
    printf("%d", b);
    
    return 0;
}
```



##### 3의 배수는 통과?

```c
#include <stdio.h>

int main()
{
    int a;
    scanf("%d", &a);
    for (int i=1; i<=a; i++)
    {
        if (i%3==0)
        {
            continue;
        }
        
        else
        {
            printf("%d ", i);
        }
    }
    
    return 0;
}
```



##### 수 나열하기1

```c
#include <stdio.h>

int main()
{
    int a, d, n;
    scanf("%d %d %d", &a, &d, &n);
    
    if (n==1)
    {
        printf("%d",  a);
    }
    
    else
    {
        for (int i=2; i<=n; i++)
        {
            a += d;
        }
        printf("%d", a);
    }
    
    return 0;
}
```



##### 수 나열하기2

```c
#include <stdio.h>

int main()
{
    long long int a;
    int r, n;
    scanf("%lld %d %d", &a, &r, &n);
    if (n==1)
    {
        printf("%lld", a);
    }
    
    else
    {
        for (int i=2; i<=n; i++)
        {
            a *= r;
        }
        printf("%lld", a);
    }
    
    return 0;
}
```



##### 수 나열하기3

```c
#include <stdio.h>

int main()
{
    long long int a;
    int m, d, n;
    
    scanf("%lld %d %d %d", &a, &m, &d, &n);
    if (n==1)
    {
        printf("%lld", a);
    }
    
    else
    {
        for (int i=2; i<=n; i++)
        {
            a = a*m + d;
        }
        printf("%lld", a);
    }
    
    return 0;
}
```



##### 함께 문제 푸는 날

```c
#include <stdio.h>

int main()
{
    int a, b, c;
    scanf("%d %d %d", &a, &b, &c);
    
    int d=1;
    while (d%a!=0 || d%b!=0 || d%c!=0)
    {
        d += 1;
    }
    printf("%d", d);
    
    return 0;
}
```



### 1차원배열

##### 이상한 출석 번호 부르기1

- 배열 값 0으로 초기화 `int a[24]={}`

```c
#include <stdio.h>

int main()
{
    int n, m;
    scanf("%d", &n);
    int a[24]={};
    for (int i=1; i<=n; i++)
    {
        scanf("%d ", &m);
        a[m] += 1;
    }
    
    for (int j=1; j<=23; j++)
    {
        printf("%d ", a[j]);
    }
    
    return 0;
}
```



##### 이상한 출석 번호 부르기2

- 배열 크기가 가변적일 때는 배열 값을 0으로 초기화할 수 없음 `int a[n]={}` (X)

```c
#include <stdio.h>

int main()
{
    int n, m;
    scanf("%d", &n);
    int a[n];
    for (int i=1; i<=n; i++)
    {
        scanf("%d ", &m);
        a[i-1] = m;
    }
    
    for (int j=n-1; j>=0; j--)
    {
        printf("%d ", a[j]);
    }
    
    return 0;
}
```



##### 이상한 출석 번호 부르기3

```c
#include <stdio.h>

int main()
{
    int n, m;
    scanf("%d", &n);
    int a[24]={};
    for (int i=1; i<=n; i++)
    {
        scanf("%d ", &m);
        a[m] = 1;
    }
    
    for (int j=1; j<=23; j++)
    {
        if (a[j]==1)
        {
            printf("%d", j);
            break;
        }
    }
    
    return 0;
}
```



### 2차원배열

##### 바둑판에 흰 돌 놓기

```c
#include <stdio.h>

int main()
{
    int n;
    int x, y;
    int a[20][20]={};
    scanf("%d", &n);
    
    for (int i=1; i<=n; i++)
    {
        scanf("%d %d", &x, &y);
        a[x][y] = 1;
    }
    
    for (int j=1; j<20; j++)
    {
        for (int k=1; k<20; k++)
        {
            printf("%d ", a[j][k]);
        }
        printf("\n");
    }
    
    return 0;
}
```



##### 바둑알 십자 뒤집기

```c
#include <stdio.h>

int main()
{
    int a[20][20]={};
    for (int i=1; i<20; i++)
    {
        for (int j=1; j<20; j++)
        {
            scanf("%d", &a[i][j]);
        }
    }
    
    int n;
    scanf("%d", &n);
    for (int k=1; k<=n; k++)
    {
        int x, y;
        scanf("%d %d", &x, &y);
        int m;
        for (m=1; m<20; m++)
        {
            if (a[x][m]==0)
            {
                a[x][m] = 1;
            }
            else
            {
                a[x][m] = 0;
            }
        }
        for (m=1; m<20; m++)
        {
            if (a[m][y]==0)
            {
                a[m][y] = 1;
            }
            else
            {
                a[m][y] = 0;
            }
        }
    }
    
    for (int i=1; i<20; i++)
    {
        for (int j=1; j<20; j++)
        {
            printf("%d ", a[i][j]);
        }
        printf("\n");
    }
    
    return 0;
}
```



##### 설탕과자 뽑기

```c
#include <stdio.h>

int main()
{
    int h, w, n, l, d, x, y;
    scanf("%d %d", &h, &w);
    scanf("%d", &n);
    int a[h][w];
    for (int i=0; i<h; i++)
    {
        for (int j=0; j<w; j++)
        {
            a[i][j] = 0;
        }
    }
    
    for (int i=1; i<=n; i++)
    {
        scanf("%d %d %d %d", &l, &d, &x, &y);
        if (d==0)
        {
            for (int j=0; j<l; j++)
            {
                a[x-1][y-1+j] = 1;
            }
        }
        else
        {
            for (int j=0; j<l; j++)
            {
                a[x-1+j][y-1] = 1;
            }
        }
    }
    
    for (int i=0; i<h; i++)
    {
        for (int j=0; j<w; j++)
        {
            printf("%d ", a[i][j]);
        }
        printf("\n");
    }
    
    return 0;
}
```



##### 성실한 개미

```c
#include <stdio.h>

int main()
{
    int a[10][10]={};
    int n;
    for (int i=0; i<10; i++)
    {
        for (int j=0; j<10; j++)
        {
            scanf("%d", &n);
            a[i][j] = n;
        }
    }
    
    int x=1, y=1;
    
    while (1)
    {
        if (a[x][y] == 2)
        {
            a[x][y] = 9;
            break;
        }
        
        else if (a[x][y] == 0)
        {
            a[x][y] = 9;
        }
        
        if (a[x][y+1] == 1 && a[x+1][y] == 1)
        {
            break;
        }
        
        if (y+1 <= 9)
        {
            if (a[x][y+1] == 0 || a[x][y+1] == 2)
            {
                y += 1;
            }
            else
            {
                x += 1;
            }
        }
    }
    
    for (int i=0; i<10; i++)
    {
        for (int j=0; j<10; j++)
        {
            printf("%d ", a[i][j]);
        }
        printf("\n");
    }
    
    return 0;
}
```

