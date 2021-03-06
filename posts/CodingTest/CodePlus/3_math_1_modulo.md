---
sort: 3
title: 알고리즘 기초 1/2 수학 - 1 나머지 연산
tags: [ 알고리즘, 백준 ]
---

## CodePlus 알고리즘 기초 1/2 수학 1-1

### 나머지연산(Modulo, MOD)

문제의 정답이 엄청 커서 나머지연산한 결과만 내놓으라고 하는 경우가 많다.

[예시 : 2Xn 타일링 문제](https://www.acmicpc.net/problem/11726)

정답구하는게 중요하지, 긴자리 연산하는게 중요한게 아니다. 그리고, 굳이 실제 숫자에다 대고 나머지연산을 안해도 어느정도는 알 수 있다. 

이걸 어떻게 하냐면, 정답을 갱신할때마다 나머지연산을 해주면 된다.

##### (A + B)%M = (A % M + B % M) % M

이 식이 성립하기 때문에, 큰 숫자에 직접 나머지연산을 하지 않아도 구할 수 있다.

아래는 2xn문제를 풀 때, 모듈로를 이용해서 값이 너무 커지는 일을 방지할 수 있다.

```java
for (int i = 3; i <= n; i++) {
    res = n2 % 10007 + n1 % 10007;
    n1 = n2;
    n2 = res;
}
return res % 10007;
```



##### 뺄셈에 대해 조심할게 있다.

(6 - 5) % 3 = 1 % 3 = 1인데, 이것도 위처럼 해도 될까?

(6%3 - 5%3) % 3 = ( 0 - 2 ) % 3 =  1이어야하는데, 과연 프로그램도 그렇게 될까?

c++이랑 자바는 저 식대로 돌리면 -2, 파이썬은 1이 나온다. 그래서 조심해서 계산해야 한다.

이걸 방지하려면 어떻게 해야할까?

-c < (a%c -  b%c) < c 를 만족한다. 어떤 수를 c로 나머지연산하면, 그 결과는 반드시 0 ~ c-1이기 때문에, 

이런 부등식이 성립한다. 여튼간에 괄호안에 + c를 넣어주자. 어차피 c % c가 되기때문에, 0이 되니까 더해줘도 문제없다. 자기 자신으로 나눴는데 나머지가 생길리가 없지 않은가.

```java
int a = 6, b = 5, c = 3;
int tmp1 = (a-b) % c;
int tmp2 = (a % c - b % c) % c;
int tmp3 = (a % c - b % c + c) % c;
System.out.printf("(a-b) %% c : %d\n", tmp1);
System.out.printf("(a %% c - b %% c) %% c : %d\n", tmp2);
System.out.printf("(a %% c - b %% c + c) %% c : %d\n", tmp3);
/*Output
    (a-b) % c : 1
    (a % c - b % c) % c : -2
    (a % c - b % c + c) % c : 1
*/
```
