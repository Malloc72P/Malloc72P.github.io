---
sort: 3
title: 자바에서의 비동기처리
tags: [ java, async ]
---

## 자바에서의 비동기처리

### 비동기 함수를 만들어보자.

어떤 태스크를 작은 태스크로 나눈다고 치자. 그렇게 해서 fx랑 gx가 생겼고, 얘네 처리하는데 긴 시간이 걸린다고 치자.

```java
void testThread() throws InterruptedException {
    Result result = new Result();
    Thread t1 = new Thread(()->{result.left = workerFx(NUMBER_OF_OPERATION);});
    Thread t2 = new Thread(()->{result.right = workerGx(NUMBER_OF_OPERATION);});

    t1.start();
    t2.start();
    t1.join();
    t2.join();
    return result.left + result.right;
}
```

이걸 ExecutorService를 써서 구현해보자

```java
int test2() throws InterruptedException, ExecutionException {
    //엑시큐터스의 nFTP메서드로 엑시큐터서비스라는 스레드풀을 생성한다.
    ExecutorService executorService = Executors.newFixedThreadPool(2);

    //엑시큐터서비스에 태스크를 제출한다.
    Future<Integer> left = executorService.submit(()->workerFx(NUMBER_OF_OPERATION));
    Future<Integer> right = executorService.submit(()->workerGx(NUMBER_OF_OPERATION));
    System.out.println("submit task complete!");

    int sum = left.get() + right.get();
    executorService.shutdown();
    return sum;
}
/**** output
submit task complete!
Fx >> Thread ID : 13 >> Start Task... 
Gx >>Thread ID : 14 >> Start Task... 
Gx >> Thread ID : 14 >> Jobs Done... 
Fx >> Thread ID : 13 >> Jobs Done... 
*/
```

엑시큐터서비스의 스레드 풀에 작업 workerFx와 workerGx를 맡겼다. 그런 다음 submit task complete를 출력하게 시켰다. 실제로 submit이 먼저 출력되고, workerFx와 workerGx의 출력이 뒤늦게 찍혔다. 다시말해서 스레드풀에 일은 시켰지만, 이걸 기다리진 않은것이다. 다만, 아래에서 Future클래스의 인스턴스로 get()메서드를 호출하는걸 볼 수 있는데, 여기선 블로킹된다. 다시말해서, 이 작업이 끝나길 기다린다는 것이다. 위에서 봤던 엄격한 포크/조인이라고 할 수 있겠다.

여하튼 책은 이게 맘에 안든다고 한다. submit메서드같은 불필요한 코드로 오염되었느니, 명시적 반복으로 병렬화를 수행하던 코드를 스트림을 이용해 내부반복으로 바꾼것처럼 비슷한 방법으로 해결해야 하느니 하는데, 무슨 소리인지 이해가 안간다. 일단 그냥 따라해보자

```note
나중에 더 공부해서 내공이 쌓이면 이해안되는 부분을 다시 공부해볼 수 있도록 하자!
```

여튼 자바의 Future를 이용하면 개선할 수 있단다. 아니면 Flow인터페이스를 이용하면 된다고 한다. 일단 Future형식 API부터 보자.

### Future 인터페이스로 비동기 함수 구현

* 리턴타입을 Future로 설정한다.

* CompletableFuture타입의 인스턴스A를 만든다.

* 시간이 걸리는 태스크를 실행한다. 완료하면 인스턴스A.complete(myValue)를 통해 완료와 결과값을 

  알리도록 설정한다.

* CompletableFuture타입의 인스턴스A를 리턴한다. 이때 주의할 점은, 리턴시점에 태스크가 끝났는지 안끝났는지는 아무도 모른다. 너무 빨리 끝나는 태스크라서 이미 끝났을 수 도 있고, 아직 진행중일 수 도 있다. 

* 메서드를 호출한 쪽은 Future타입의 인스턴스를 받는다. 해당 비동기작업의 결과를 기다리고 싶으면 get을 써서 기다릴 수 있다.

```java
Future<Integer> futureWorkerFx(int x){
    CompletableFuture<Integer> futureSum = new CompletableFuture<>();
    new Thread(() -> {
        int sum = 0;
        for (int i = 0; i < x; i++) {
            sum++;
        }
        futureSum.complete(sum);
    }).start();
    return futureSum;
}
//test3가 비동기 함수 호출한 메서드이다.
int test3() throws InterruptedException, ExecutionException {
    Future<Integer> futureLeft = futureWorkerFx(NUMBER_OF_OPERATION);
    Future<Integer> futureRight = futureWorkerGx(NUMBER_OF_OPERATION);

    return futureLeft.get() + futureRight.get();
}
```

이렇게 해서 비동기함수를 구현했다.

### 비동기함수의 예외처리

근데 예외처리는 어떻게 할까? 비동기함수 내부에서 문제가 생겼다. 근데 이걸 어떻게 외부에 해야 알릴 수 있을까?

```java
public static Future<Integer> exceptionCheckedFutureWorkerFx(int x){
    CompletableFuture<Integer> futureSum = new CompletableFuture<>();
    new Thread(() -> {
        try {
            int sum = 0;
            for (int i = 0; i < x; i++) {
                sum++;
            }
            sum /= 0;//강제로 예외를 발생시킨다.
            futureSum.complete(sum);
        }catch (Exception ex){
            futureSum.completeExceptionally(ex);
        }
    }).start();
    return futureSum;
}
/*

exceptionCheckedFutureWorkerFx >> Thread ID : 13 >> Start Task... 
exceptionCheckedFutureWorkerFx >> Thread ID : 14 >> Start Task... 
Exception in thread "main" java.util.concurrent.ExecutionException: java.lang.ArithmeticException: / by zero
	at java.base/java.util.concurrent.CompletableFuture.reportGet(CompletableFuture.java:395)
	at java.base/java.util.concurrent.CompletableFuture.get(CompletableFuture.java:1999)
	at _7_ASIO.Practice.asyncPractice.test4(asyncPractice.java:62)
	at _7_ASIO.Practice.asyncPractice.main(asyncPractice.java:17)
Caused by: java.lang.ArithmeticException: / by zero
	at _7_ASIO.Practice.asyncPractice.lambda$exceptionCheckedFutureWorkerFx$5(asyncPractice.java:97)
	at java.base/java.lang.Thread.run(Thread.java:834)
*/
```

CompletableFuture인스턴스의 completeExceptionally()메서드로 비동기함수 내부에서 발생한 에러를 전파할 수 있다.

### 비동기함수 쉽게 만들기 supplyAsync

CompletableFuture클래스에 supplyAsync메서드가 있는데, 이걸로 비동기함수를 쉽게 만들 수 있다.

```java
//SupplyAsync메서드
public static <U> CompletableFuture<U> supplyAsync(Supplier<U> supplier) {
    return asyncSupplyStage(ASYNC_POOL, supplier);
}
//SupplyAsync메서드에서 호출하는 메서드
static <U> CompletableFuture<U> asyncSupplyStage(Executor e,
                                                 Supplier<U> f) {
    if (f == null) throw new NullPointerException();
    CompletableFuture<U> d = new CompletableFuture<U>();
    e.execute(new AsyncSupply<U>(d, f));
    return d;
}
//봐도 잘은 모르겠지만, 우선 ASYNC_POOL이라는걸 이용해서 실행해주는 모양이다.
//아래는 내 코드이다. 이렇게 간단해진다.
public static Future<Integer> getFxAsync(int x){
    return CompletableFuture.supplyAsync(()->workerFx(x));
}
```

