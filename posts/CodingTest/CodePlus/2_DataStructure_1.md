---
sort: 2
title: 알고리즘 기초 1/2 자료구조 큐와 스택
tags: [ 알고리즘, 백준 ]
---

## CodePlus 알고리즘 기초 1/2 자료구조 - 스택과 큐

### 스택

#### 선입후출, 후입선출

먼저 넣은게 나중에 나온다. 다시말해, 가장 마지막(최근)에 넣은게 가장 먼저 나온다.

#### 스택써서 풀 수 있는 문제

##### 단어뒤집기

순서대로 스택에 집어넣고 꺼내면 거꾸로 나오는 성질을 이용해서 푼다.

asdf 순으로 넣으면 fdsa순으로 나오기 때문이다.

##### 괄호처리문제

()(()()(()))이런 괄호가 주어진다고 치자.

닫는 괄호를 만났을 때, 가장 최근에 만난 열린 괄호는 어디일까? 찾기 참 힘들다

괄호문자열의 앞부터 시작해서 여는 괄호를 만날때마다 스택에 넣었다면 간단하다. 닫는괄호를 만났을 때, 스택에서 pop하면, 가장 최근에 만난 여는괄호가 나온다. 즉 현재의 닫는괄호의 쌍이다. 왜 가능할까? 스택은 가장 마지막(최근)에 넣은게 가장 먼저 나오기 때문이다.

##### 스택수열

스택의 성질을 이용해서 수열을 만들 수 있는지 판단하면 된다.

##### 에디터 문제

커서를 기준으로 문자열을 비교하고, 잘라붙이고 하면 정말 골치아픈데다가 성능도 좋지 않다.

근데 잘 보자. 커서 기준으로, 왼쪽과 오른쪽은 어떤 성질을 가질까?

커서의 왼쪽으로 이동할때마다, 문자열이 abc 나왔다고 치자. 그러면 |abc 일케 있다.

다시 오른쪽으로 이동했다고 치자. 이때 문자가 나오는 순서를 보자. a, b, c 이다.

다시 왼쪽으로 가면? c b a이다. 가장 마지막에 들어간게 가장 먼저 나오지 않는가?

이걸 스택으로 구현해보자. 왼쪽으로 갈때마다 pop한다. c b a 튀어나온다.

오른쪽으로 간다. a b c 나온다. ㅇㅇ 커서의 양 끝을 스택으로 표현하면 쉽게 풀 수 있다.
