---
sort: 1
title: 쉘프로그래밍 기초문법
tags: [ 쉘프로그래밍 ]
---

## 쉘 프로그래밍 기초문법

### 해시뱅. 쉘 스크립트의 첫번째 라인

```shell
#!/bin/bash
```

이걸로 유닉스한테 이 스크립트 파일은 /bin/bash쉘로 실행될 거라고 알려주는 거라고 한다.

없어도 돌아가긴 한다. 관례라고 한다. [참조](https://www.freecodecamp.org/news/linux-command-line-bash-tutorial/)

해시뱅이라고 부른데

### 변수선언

##### 변수 선언시 공백을 넣으면 안된다. 인터프리터가 이해못한다.

```shell
# 이렇게 하면 안된다!
myVar1 = "asdf"

# 이렇게 해야한다!
myVar2="asdf"

echo $myVar1
echo $myVar2

#***output
#$ ./MyShell.sh
#./MyShell.sh: line 2: myVar1: command not found
#
#asdf
```

##### 배열 선언

콤마가 아닌 공백문자로 구분하며, 괄호()로 감싼다.

```shell
myVar3=("a1" "a2" "a3")
```

### 반복문

* lua도 그렇고 얘도 그렇고 조건문이던 반복문이던 시작하는 절과 닫는절이 있다.

##### 1부터 3까지 반복하기.

```shell
for((i = 1; i <= 3; i++))do
    echo "${myVar1} test"
done
#asdf test
#asdf test
#asdf test
```

##### 배열에 있는 요소만큼 반복하기.

```shell
myVar3=("a1" "a2" "a3")
for index in ${myVar3[*]}; do
    echo ${index}
done
#a1
#a2
#a3
```

### 조건문

if, then, fi로 열고 닫는다. elseif는 elif then을 쓰면 된다

```shell
if(($myVar4 == 1));then
    echo "if!"
elif(($myVar4 == 2));then
    echo "elif!"
else
    echo "else!"
fi
```

* 보면 then 앞에 세미콜론을 썼다. 원래는 then을 줄 바꾸고 써야하는데, 보기 싫어서 이렇게 한것이다.
* else문은 then을 쓰지 않는다.

### 시간출력

```shell
$(date +%Y%m%d) 
# *** output
#$ ./MyShell.sh
#20210123
```

### 쉘 명령어 사용하기

백쿼터(``)는 명령어의 결과를 문자열로 사용하고 싶을 때 쓸 수 있다.

```shell
lsResult=`ls | wc -l`
echo $lsResult
# ***output
#$ ./MyShell.sh
#3
```

