---
sort: 1
title: 운영체제의 발전
tags: [ os ]
---

## 운영체제의 역할

#### 만약 운영체제가 없다면?

컴퓨터는 여러개의 하드웨어로 구성된다. 근데 이 위에서 운영체제 없이 응용프로그램을 만들면 어떤 일이 생길까? 프로그램이 동작하려면 공통적으로 메모리에 값을 저장하고 CPU를 써서 명령어를 수행해야 한다. 응용마다 이게 필요하니까 각자 알아서 하드웨어를 이용하는 기능을 구현할 것이다.  그러면 다음과 같은 문제가 생긴다.

##### 비효율성 = 떨어지는 재사용성

응용프로그램 하나 만드는데 하드웨어를 이용하고 관리하는 코드도 작성해야 한다. 시간이 엄청 걸리겠다. 

##### 비일관성

물론 표준을 만들고 이걸 지켜가면서 하드웨어를 이용하는 코드를 짠다면 괜찮을 수도 있겠지만, 모든 프로그램이 다 완벽하게 표준을 지킬 것이라는 보장이 없지 않은가. 그래서 일관성이 떨어질 수 밖에 없다.

#### 운영체제의 발전과 멀티프로그래밍의 등장

예전의 컴퓨터는 단순 일괄처리 시스템(Simple Batch System)으로 동작했다. 처리하고 싶은 작업들을 전체 작업묶음(batch)으로 만들고 입력장치에 넣는다. 그러면 모니터라는 프로그램이 작업묶음을 일괄처리한다. 어떤 프로그램의 실행이 끝나면, 제어가 모니터 프로그램으로 다시 넘어온다. 그러면 모니터는 다음 프로그램을 적재하고 실행하는 식이다. 이런 방식을 단일 프로그래밍이라고 한다.

단일 프로그래밍 방식을 쓰면, 주메모리에 하나의 프로그램만 적재해서 수행한다. 그렇다 보니, 입출력 요청을 하고, 그 결과가 반환될때까지 CPU는 아무것도 안하고 놀게 된다. 문제는 CPU에 비해 입출력장치가 너무 느려서, 아래 그림처럼 CPU가 너무 오랫동안 놀게 된다.

![image-20210121141143386](../../TIL/image-20210121141143386.png) 

반면 멀티프로그래밍은, 주메모리에 여러개의 프로그램을 적재해서 수행할 수 있다. 그리고 입출력 장치를 이용할 때, 입출력 요청만 하고, 그 결과를 기다리지 않는다. 대신 다른 프로그램을 수행한다. 나중에 입출력 작업이 완료되면, 인터럽트가 발생한다. 그러면 제어가 인터럽트 처리 프로그램으로 넘어가서, 입출력작업 완료에 대한 처리를 해줄 수 있다. 단일 프로그래밍과 다르게, 입출력을 하는 동안 다른 프로그램을 처리할 수 있으니 낭비되는 CPU시간이 줄어들고, 그만큼 효율적으로 CPU를 쓸 수 있다는 장점이 있다. 

![image-20210121141155341](../../TIL/image-20210121141155341.png) 

#### 시분할 시스템

CPU의 시간을 **타임퀀텀**이라는 단위로 아주 잘개 쪼갠다. 그리고 프로그램을 이 타임퀀텀만큼만 실행한 다음 다른 프로그램을 실행한다. 여러 프로그램을 **번갈아가면서 타임퀀텀만큼만 아주 짧게 실행**하는 것이다. 타임퀀텀은 **사람의 기준**에서는 **매우 짧은 시간**이라서, 여러 프로그램을 번갈아가며 실행해도 **응답속도가 빠르다**. 그렇다보니 여러 사람이 시분할시스템을 **공유해서 이용**해도, 응답시간이 빠르다보니 마치 컴퓨터를 **독점해서 쓰는 것 같이 느끼게 해준다.**

