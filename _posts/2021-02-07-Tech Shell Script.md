---
layout: post
title:  "Shell Script 정리"
categories: Bash shellscript
---
주제: Shell Script

# Shell Script 기초 문법 정리

## Shebang?
- 어떤 인터프리터 프로그램을 사용할 것인가 선언해주는 부분.

Ex)
```bash
#!/bin/bash
#!/usr/bin/env python
```

<br>

## Script 만들어 문자열 출력 해보기
- echo나 printf 사용

```bash
#!/bin/bash

echo "Welcome"
printf "Enjoy.\n"
```

<br>

## Command Line Arguments And Exit Status
- $#: Command Line 인자 갯수.
- $1, $2 ...: 1번 인자 값, 2번 인자 값 ...
- $?: Exit Status

Function의 매개변수, 리턴값 동일하게 처리

<br>

## 주석 처리
- #붙여주면 주석 처리

```bash
#!/bin/bash

#주석
#echo "Welcome"
printf "Enjoy.\n"
```

<br>

## 변수
- 보통 소문자를 사용함
- '=' 앞뒤로 공백 없어야 함( 공백 시 오류 발생 )
- 변수 참조 시 $ 사용
- 변수 값 대입 시 $ 사용 X

```bash
#!/bin/bash

#주석
echo "Welcome"

var1=1
var2 = 2 #해당 구문 에러 발생 공백 있으면 안됨

echo $var1  #출력: 1

$var1=10 #해당 구문 에러 발생 변수 값 변경할 때 $ 사용 금지
var1=20
echo $var1  #출력: 20
```

#### Full Quotation
- 리터럴로 작은 따옴표 사용

```bash
#!/bin/bash

x="java"; echo '$x is noun'
```

#### Partial Quotation
- 변수 대체로 큰 따옴표 사용

```bash
#!/bin/bash

x="java"; echo "$x is noun"
```

<br>

## 명령 문자열을 실행하기
- eval 명령문자열

```bash
#!/bin/bash

cmd="ls -alF”; eval $cmd
```

<br>

## if문
### 형태
```bash
if [ 조건 ]; then
    실행문
elif [ 조건 ]; then
    실행문
fi
```
- test 명령과 if문 사용.
- Boolean Expression: &&, `||`, !, -a(and), -o(or)
- Integer Expression: -eq(Equal), -ne(Not Equal), -gt(>), -ge(>=), -lt(<), –le(<=)
- String Expression: <, <=, =>, >, ==, !=, -z, -n
- File Test: -e(exist), -s(size not zero), -f(파일이 있고 정규파일이면...),<br>
                -p(pipe), -d(디렉토리이면 참), -L(심볼릭 링크이면 참), <br>
                -r, -w, -x, -u, -g, -k, (Permission) <br>
                 -nt(newer than), -ot(older than)

<br>

## 반복문
### while문 형태
```bash
while [ 조건 ]; do
    실행문
done
```

### for문 형태
```bash
for 변수명 in 범위(배열, 리스트 등); do
    실행문
done
```

<br>
예시

```bash
for liststr in "list1" "list2" "list3" "list4"; do
    echo $liststr
done
```

<br>

## getopt 사용하기
예시
```bash
#!/bin/bash
while getopts c:f: opt
do
   case $opt in
        c)
            COMMAND=$OPTARG
            ;;      
        f)
            FILE=$OPTARG
            ;; 
        *)
            printusage exit -1
            ;;
esac done
```

<br>

## 함수
### 형태
```bash
함수명()
{
	구문
	return 값
}
```
- 함수 내 변수 선언 시 기본적으로 전역
- 함수 내에서만 변수 사용하려면 local로 지정해야 함

<br>

## 출처
- Basecamp 3주차 류희태 강사님의 bash tutorial 교육자료
- https://wiki.kldp.org/wiki.php/ShellProgrammingTutorial
