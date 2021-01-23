---
sort: 2
title: 쉘스크립트에서 파일에 접근하기
tags: [ 쉘프로그래밍 ]
---

## 쉘스크립트에서 파일에 접근하기

### 파일 순회

```shell
for d in ./*; do
    echo $d
done
# *** output
#$ ./MyShell.sh
#./asdf
#./MyShell.sh
#./tasd.txt
```

### 파일 찾기, 찾은 파일개수 구하기

##### 파일찾기

```shell
myVar5=`find -name "test*"`
for d in $myVar5; do
    echo "${d}"
done

# *** output
#$ ./MyShell.sh
#./test1
#./test2
#./test3
```
##### 찾은 파일 개수 구하기

```shell
myVar6=`find -name "test*" | wc -l`
echo $myVar6
# *** output
#$ ./MyShell.sh
#3
```
