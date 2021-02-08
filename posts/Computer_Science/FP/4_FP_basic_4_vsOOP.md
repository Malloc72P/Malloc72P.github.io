---
sort: 4
title: 객체지향과 함수형 프로그래밍
tags: [ FP ]
---

## 객체지향과 함수형 프로그래밍

#### 프로그래밍 패러다임

프로그래밍 패러다임은 프로그래머에게 프로그래밍의 관점을 갖게 해준다. 만약 프로그래밍 패러다임이 객체지향프로그래밍이라면, 프로그래머는 프로그래밍을 객체들의 협력을 통한 문제해결로 볼 것이다. 함수형 프로그래밍이 패러다임이면, 프로그래밍을 수학적 함수의 조합으로 문제해결로 볼 것이다. 따라서 어떤 관점을 가지느냐에 따라 프로그래밍을 하는 방법이 달라지는 것 같다.

#### 객체지향 프로그래밍과 함수형 프로그래밍

함수형 패러다임
수학적 함수인 순수함수의 조합으로 프로그램을 작성하는 것. 어떤 순서의 일을 프로그래밍 하고 싶을 때, 각 단계의 일을 순수함수로 작성하고, 이 함수들을 순차적으로 실행하는 파이프라인을 만드는데 좋은 프로그래밍 패러다임이다.

객체지향 패러다임
어떤 문제를 해결하기 위해, 문제를 작은 단위의 역할로 나누고, 이 책임을 객체들에게 하나씩 부여한 다음, 객체들이 협력해서 복잡하고 어려운 문제를 보다 쉽게 풀 수 있도록 하는 프로그래밍 방법이 객체지향 프로그래밍이다.

공통점
둘 다 공통적으로 코드 재사용성을 최대한 높이기 위해 노력한다. 객체지향의 경우, 작은 책임을 가진 객체간의 협력으로 어려운 문제를 해결하는데, 같은 일을 해야 하는 경우, 같은 객체한테 요청해서 일을 처리하게 된다. 즉 어떤 일을 처리하기 위해서 또 구현할 필요 없이, 그 일에 대한 책임이 있는 객체한테 요청하면 되니까 중복을 피할 수 있다.
함수형 프로그래밍도 마찬가지이다. 순수함수의 조합으로 문제를 해결하는 방식인 만큼, 함수에 확실하고 작은 일을 맡기면, 그 일을 처리해야 할 때, 해당하는 함수를 조합해서 문제를 해결할 수 있으니, 함수형도 중복을 피할 수 있다.
차이점
함수형 프로그래밍은 상태에 의존하거나 바꾸는 방식으로 프로그래밍하면 안되고, 오직 입력패러미터에 의존해야하고, SideEffect가 없어야 하는 만큼 외부의 상태를 바꿔서도 안되고, 함수의 결과를 오직 리턴으로만 전달해야 한다.
반면 객체지향에서의 객체는 상태와 행동으로 구성된 존재이다. 얘가 행동하기 위해선, 그 행동을 하는데 필요한 상태가 필요하다. 상태가 있고 없고가 객체지향과 함수형의 차이점인 것 같다.