---
sort: 1
title: 데이터베이스
tags: [ OOP, SQL첫걸음 ]
---

#### 주의, 해당 포스트는 책의 내용을 그대로 담은것이 아닌, 책을 읽고 나서 느낀 제 생각을 정리한 것 입니다. 따라서 책의 저자가 전달하고자 한 내용과 다소 차이가 있거나 잘못된 내용이 있을 수 있습니다.
#### 잘못된 내용이 있다면 이메일을 남겨주세요. : scra1028@gmail.com

## 1장 데이터베이스와 SQL

### 1강 데이터베이스

#### 데이터와 데이터베이스

먼저, 데이터란 datum의 복수형으로, 자료뭉치라는 의미를 가진다. 애는 그냥 어떤 자료의 뭉치라서,  이것 자체가 정보를 의미하지는 않는다.

컴퓨터에서 말하는 데이터는, 컴퓨터에 기록되어 있는 숫자를 말한다.(0101101001)

그리고 데이터베이스는 이러한 데이터의 집합을 말한다. 보통 데이터베이스는 어떤 데이터를 간단하게 찾을 수 있도록 정리되어 저장될 수 있다. 또한 전원이 꺼져도 데이터가 손실되지 않도록 비휘발성 저장장치에 저장된다.

#### 시스템 내의 데이터베이스

데이터베이스는 다양한 곳에서 쓰인다. 데이터센터에 있는것도 데이터베이스고, 스마트폰에 있는 전화번호부도 데이터베이스이다. 데이터베이스는 다양한 시스템에서 사용되고 있다.

#### DB와 DBMS

앞서도 설명했지만, 데이터베이스는 컴퓨터에 정리되어 저장된 데이터의 집합일 뿐이다. 이러한 데이터베이스스를 관리해주는 프로그램이 있는데, 이걸 DBMS라고 한다. DBMS는 이름 그대로 DB를 관리해주는 시스템이다.

근데 DB를 관리해주는 프로그램이 왜 필요할까? 첫번째 이유로 생산성을 들 수 있다. 데이터는 입력과 출력으로 나뉜다. 또, 입력은 3가지로 다시 나뉠 수 있다. 그러면 총 4가지이고 이걸 CRUD라고 한다. Create, Read, Update, Delete. 이런 4가지 작업을 할 수 있어야 데이터를 관리할 수 있다. 근데 프로그램을 짤때마다, 데이터베이스에서 데이터를 저장하고 읽고 수정하고 삭제하는 기능을 구현하는건 너무 힘들다. 근데 DBMS를 이용하면 CRUD를 데이터베이스가 대신 해주기 때문에, 우리가 만든 프로그램은 원하는 요청을 데이터베이스한테 보내고, 데베로부터 결과만 잘 받으면 된다.

그 다음은 기능성이다. 우리는 데이터의 집합에 대해 바라는게 정말 많다. 데이터베이스를 여러 사용자가 공유해서 쓰고 싶다. 또한 어떤 데이터를 정말 빠르게 찾고 싶다. 이런 기능을 DBMS가 제공해줄 수 있다. 그래서 우리가 구현하지 않고, DBMS의 서비스를 받아서 원하는 일을 할 수 있다.

마지막으로 신뢰성이 있다. 데이터베이스에 대한 부하를 분산시키거나, 아니면 백업하고 복구하는 기능을 제공한다.

```note
근데 로드밸런싱이랑 백업,복구기능이랑 신뢰성이랑 어떤 관계가 있는걸까? 왜 이 기능이 신뢰성인걸까?
나중에 더 공부해보거나 질문해보자. 일단 그다지 중요한 부분은 아닌 것 같으니 넘어가자.
```

여하튼 DBMS는 DB를 관리해주는 프로그램이고, 얘 덕분에 개발자는 개발의 생산성과 기능성이 높아지고, 신뢰성을 확보할 수 있다.

다음은 27페이지 SQL부터 읽도록 하자.