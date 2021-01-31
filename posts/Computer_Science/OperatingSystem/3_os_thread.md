---
sort: 3
title: 스레드
tags: [ os ]
---

## 스레드

### 프로세스와 스레드

##### 스레드의 정의와 구조

스레드는 프로세스 안에 있는 실행흐름이며, 디스패치의 단위이다. 그래서 스레드가 한개 있으면, 한순간에 하나의 코어에 의해서만 수행될 수 있다.

스레드는 실행흐름인 만큼, 수행을 하기 위해선 함수를 호출해야 해서 지역변수와 매개변수를 저장하고 복귀주소를 저장해야 한다. 그래서 각각의 스레드는 자신만의 스택을 가져야 한다. 다만 스레드는 프로세스 안에서 사는 존재라서, 프로세스의 스택을 이용한다. 만약 프로세스가 생성되어서 스레드를 하나 만든다면, 두 스레드는 같은 프로세스의 스택영역을 반으로 나눠서 쓰게 된다. 하지만 데이터 영역과 힙 영역은 공유해서 사용한다.

##### 유저레벨스레드와 커널레벨스레드

스레드는 유저레벨스레드(ULT)와 커널레벨스레드(KLT)로 나뉜다. ULT는 스레드 라이브러리에서 관리하는 스레드이고, KLT는 커널이 직접 관리하는 스레드이다. 그렇다보니 커널은 KLT의 존재는 알아도, ULT의 존재는 알지못한다. 

스레드 라이브러리가 ULT를 관리한다건, ULT의 제어가 사용자공간과 프로세스 내에서 이루어짐을 말한다. 스레드라이브러리로 제어가 넘어가서 ULT를 위한 자료구조가 만들어지고, 라이브러리에 있는 스케줄러를 써서 그 프로세스에서 준비상태에 있는 ULT로 제어를 넘겨서 실행시킨다. 

그렇다보니 커널은 이런 스레드가 있다는걸 모른다. 디스패치할때도 프로세스 단위로 한다. 커널이 보기엔 스레드가 하나만 있는 걸로 보이기 때문이다. 그렇다보니, ULT중 하나가 블록상태로 전이시키는 시스템콜을 하면, 그 프로세스 안의 죄없는 ULT도 다 같이 블록상태가 되는 것이다. 

그럼 ULT는 왜 쓸까? 일단 스레드를 관리하는데 시스템콜이 필요없다. 전부 사용자공간에서 이뤄지기 때문에, 스레드를 관리한다고 모드스위칭이 발생하지 않는다.  그만큼 오버헤드가 적다. 또한 스레드의 스케줄링이 스레드 라이브러리에 의해 이루어지기 때문에, 내 프로그램에 맞는 방법으로 스케줄링해서 최적화할 수 있다.

단점으로는 같은 프로세스에 있는 ULT가 블록을 유발하는 작업(대부분의 시스템 콜)을 하면, 그 안의 죄없는 다른 스레드도 다 같이 블록상태가 되버린다는 점이 있다. 그리고, 순수한 ULT기반의 스레드라이브러리를 쓰는 멀티 유저레벨 스레드 프로그램은 멀티코어의 장점을 살리기 어렵다. 커널은 모르는 스레드라서 따로 디스패치되지 못하고, 결국 그 프로세스 단위로 디스패치된다. 결국 코어가 여러개 있어도 한 시점에 하나의 ULT만 처리된다. 그래서 멀티 프로세싱의 장점을 살리기 힘들다.

#### 멀티스레딩

병렬처리를 위해 하나의 프로세스 안에 여러개의 스레드를 만들어서 처리하는 방법을 말한다. 스레드 대신 프로세스를 여러개 만들어서 처리하면 멀티프로세스(프로세싱아님)라고 한다.

멀티스레딩은 멀티프로세스보다 컨택스트 스위칭이 빠르다. 근데 컨택스트스위칭은 프로그램이 실행되면서 빈번하게 계속 발생한다. 그래서 컨택스트 스위칭이 프로세스보다 빠르다는 장점은, 멀티스레드가 멀티프로세스보다 나은 성능을 내는데 도움을 준다.

또한 스레드는 스택만 별도로 갖지, 힙과 데이터영역은 공유한다. 스레드 간 협력을 위해 데이터를 주고받거나 공유자원을 쓰는 경우, 간편하고 빠르게 힙이나 데이터 영역을 이용해서 통신하면 된다. 반면 멀티프로세스 방식으로 하면 이게 안된다. 각각의 프로세스는 분리된 메모리 영역을 갖기 때문에, 함부로 서로의 메모리에 접근할 수 없다. 그래서 프로세스 간 통신기법인 IPC(Inter process Communication)을 써야 한다. 물론 힙과 데이터영역으로 통신하는것보다 불편하다.  

#### 멀티 스레드 스케줄링 방식에 대해 학습하고 정리 :  [출처](https://coding-factory.tistory.com/569)

스레드 스케줄링 : 멀티스레드의 순서를 정하는 것을 말한다.
우선순위 방식 : 우선순위가 높은 스레드가 더 많이 실행되도록 스케줄링하는 것을 말한다.
순환 할당 방식 : 시간할당량(time slice)를 정해서 하나의 스레드를 정해진 시간만큼 실행하고 다시 다른 스레드를 실행하는 방식이다.

#### 멀티 스레드가 공용 리소스에 접근할 때 임계구역을 다루는 방식에 대해 학습하고, 어떤 경우에 사용해야 하는가?

뮤텍스

뮤텍스를 쓰면 한 순간에 하나의 스레드만 공유자원에 접근해서 쓸 수 있게 해준다. 뮤텍스로 보호된 영역을 임계영역이라고 부르는데, 이 영역은 크면 클수록 병렬성을 저하시키기 때문에, 필요한 만큼 최소화하는게 좋다.

세마포어

뮤텍스와 다르게 세마포어는 임계영역에 여러개의 스레드가 접근할 수 있게 통제할 수 있다. 세마포어는 정수값을 가지고 이걸 가지고 임계영역에 들여보낼지 말지를 판단한다. wait할때마다 -1하고, signal할때마다 +1해준다. 0일때 wait하면, 그 스레드는 블로킹되어, 나중에 누가 signal해줘야 깨어나서 임계영역에 접근할 수 있다. 

언제 써야 하는가

여러 스레드가 공유자원에 동시접근하는 경우, 서로가 서로의 작업을 덮어쓸 수 있다. 예를들면, 스레드A가 분명히 어떤 값으로 업데이트했다고 치자. 그런데 다른 스레드B가 업데이트 이전값을 가져갔던 상황이고, 그걸로 작업했단다. 그리고 A가 업데이트한 다음에 B가 업데이트했다면? A의 작업은 없던일이 되버린다.
이런식의 문제때문에 공유자원에 대한 접근을 통제해주어야 한다. 