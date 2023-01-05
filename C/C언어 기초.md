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



