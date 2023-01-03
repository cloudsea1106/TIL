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



