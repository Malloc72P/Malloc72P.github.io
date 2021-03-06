---
sort: 1
title: 데이터와 정보, 그리고 지식
tags: [ DB ]
---



## 데이터와 데이터베이스, 그리고 DBMS

#### 데이터와 데이터베이스. 그리고 DBMS

data는 datum의 복수형인데, datum은 자료라는 뜻이라서, data는 그냥 자료뭉치이다.

데이터베이스는 여러 사람이 공유해서 쓸 수 있도록 체계화하고 관리해놓은 데이터의 집합이다.

DBMS는 데이터베이스를 관리하는 프로그램이다.

#### 데이터베이스가 필요한 이유

![DIKW pyramid](../../TIL/4144801329.jpg)

데이터는 그냥 자료뭉치라서, 이것만으로는 의미가 없다. 그렇지만 이걸 분석해서 유용한 정보를 뽑아낼 수 있다. 그래서 데이터랑 정보를 구분해서 말한다. 우리는 정보에서 어떤 지식을 만들어낼 수 있다. 예를 들면, 과일을 판매한 기록(데이터)이 잔뜩 쌓여있다고 치자. 이것자체는 의미가 없지만, 이걸 잘 분석해서 월별, 날짜별로 어떤 과일이 팔렸는지를 알게 되었다. 이렇게 정보를 얻었고, 이 정보를 가지고 보니까 특정 계절엔 특정 과일이 매우 잘 팔린다는 지식을 얻을 수 있다. 그럼 내년에도 이맘때쯤 되면 이 과일이 잘 팔리겠구나 라는 통찰력(insight)이나 지혜(wisdom)가 생길 수 있다. 이걸 잘 이용해서 판매전략을 잘 짜볼 수 있겠다.

한가지 문제가 있다면, 무질서하게 쌓여있는 데이터의 산에서, 어떻게 해야 유의미한 정보를 빨리 뽑아낼 수 있느냐가 문제다. 만약 데이터를 전기적인 정보로 컴퓨터에 저장하고, 이걸 잘 관리하고 빠르게 유의미한 정보나 지식을 만들어낼 수 있는 프로그램이 있다면 도움이 많이 될 것이다. 그리고 이 역할을 해줄 수 있는게 DB이다.