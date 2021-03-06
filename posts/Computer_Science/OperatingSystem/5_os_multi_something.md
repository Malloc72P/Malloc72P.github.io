---
sort: 5
title: 멀티 프로그래밍, 프로세싱, 태스킹, 스레딩
tags: [ os ]
---

개념이 너무 햇갈려서 제가 이해한 대로 다시 정리했습니다. 그래서 틀린 내용이 있을 수 있습니다. 혹시 틀린점이 있다면 깃허브 이슈탭에 글을 남겨주시면 감사하겠습니다.

## 멀티 프로그래밍

여러 프로세스를 번갈아가면서 수행되는 인터리빙 방식으로 동작하는 방식을 말한다. 번갈아 가면서 수행하는거지 동시에 여러 프로세스를 수행하는건 아니다. 그래서 병렬처리(Parallel Processing)이라고 할 수 없다. 

멀티프로그래밍 개념에서 말하고자 하는건, 단일 프로그래밍에서 저지른 CPU시간낭비를 최소화하는 것이다.

## 멀티 프로세싱

여러개의 CPU가 여러 프로세스를 병렬로 수행하는것을 말한다. 얘는 동시에 여러 프로세스를 수행할 수 있다. 

멀티프로세싱 개념에서 중요한 건, 여러개의 프로세스가 각자 여러개의 CPU로 디스패치되어 병렬로(동시에) 수행될 수 있다는 점이다.

## 멀티태스킹 [출처](https://velog.io/@chy0428/OS-%EB%A9%80%ED%8B%B0%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D-%EB%A9%80%ED%8B%B0%ED%94%84%EB%A1%9C%EC%84%B8%EC%8B%B1)

어떤 일을 수행하기 위한 명령어 집합을 태스크라고 한다. CPU스케줄러에 의해 태스크를 번갈아가면서 수행하는것을 멀티태스킹이라고 한다.

## 멀티스레딩

병렬처리를 위해 하나의 프로세스 안에 여러개의 스레드를 만들어서 처리하는 방법을 말한다. 스레드 대신 프로세스를 여러개 만들어서 처리하면 멀티프로세스(프로세싱아님)라고 한다.

멀티스레딩은 멀티프로세스보다 컨택스트 스위칭이 빠르다. 근데 컨택스트스위칭은 프로그램이 실행되면서 빈번하게 계속 발생한다. 그래서 컨택스트 스위칭이 프로세스보다 빠르다는 장점은, 멀티스레드가 멀티프로세스보다 나은 성능을 내는데 도움을 준다.

또한 스레드는 스택만 별도로 갖지, 힙과 데이터영역은 공유한다. 스레드 간 협력을 위해 데이터를 주고받거나 공유자원을 쓰는 경우, 간편하고 빠르게 힙이나 데이터 영역을 이용해서 통신하면 된다. 반면 멀티프로세스 방식으로 하면 이게 안된다. 각각의 프로세스는 분리된 메모리 영역을 갖기 때문에, 함부로 서로의 메모리에 접근할 수 없다. 그래서 프로세스 간 통신기법인 IPC(Inter process Communication)을 써야 한다. 물론 힙과 데이터영역으로 통신하는것보다 불편하다.  
