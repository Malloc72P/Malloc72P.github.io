---
sort: 1
title: 문제 목록
tags: [ 알고리즘, 백준 ]
---

### 유용한 링크

> [Typora Shortcut](https://support.typora.io/Shortcut-Keys/)

### 잊으면 안되는 것


* 문제풀때 덤비지 말 것. 요구사항 다 이해한 다음 어떻게 풀지 고민할 것
* 그림이 주어지면 최대한 이용할 것. 그림에 풀이가 숨어있는 경우가 많다.

#### 문제푸는 스킬

* 문제의 입력이 어떻게 해서 출력이 나오는지 안 다음 알고리즘을 짜야한다. 문제를 배껴가면서 이해하려 하지마라. 시간만 오래걸릴 뿐이다. 지문을 읽어가면서 이해해라

* **최대공약수는 유클리드 호제법**을 써서 구해라(abb bab)

* StringBuilder와 append 연속호출로 출력을 다 만든다음에 출력하면 성능이 좋다. 근데 이거가지고 안풀릴게 풀리는 케이스는 거의 없다는 건 알아둬라.

* **소수는 에라토스테네스의 체**를 이용해서 구해라. 

* N이 소수인지 알고 싶다면,  √N까지만 mod해라.

* 패턴찾는 문제는 직접 써보면서 찾으면 쉬울 수 있다.

* **모듈로 연산의 결과는 0 ~ n-1**이 된다. 여기서 주의할 점은, 
  * **절대로 n이상이 되지 않는다**는 것
  * **시작점이 0**이라는 것. 그래서 입력의 시작점이 1이라면, 모듈로 연산에 넣기 전에 -1해서 넣고, 출력은 +1해야한다.
  
* 문제를 분할해서 푸는데, 중복된 분할작업이 나온다면 그건 DP로 풀어라.

* DP로 문제풀땐 작은 문제부터 풀어서 큰 문제를 풀 수 있도록 시도하는게 답일 수 있다.

  반대로 큰 문제를 나눠가야 풀리는 경우도 있다.

### 백준

| 문제번호 | 이름 | 유형 | 풀었음 | 다시 품 | 체감난이도 | 혼자 품 |
| :-------: | :------: | :------: | :---: | :-----: | :---: | :---: |
| [10951](https://www.acmicpc.net/problem/10951) | A+B-4 | 입출력 |  |  | :one: | :1st_place_medal: |
| [9093](https://www.acmicpc.net/problem/9093) | 단어뒤집기 | 스택 | :ballot_box_with_check: |             | :one: |  |
| [9012](https://www.acmicpc.net/problem/9012) | 괄호체크 | 스택 | :ballot_box_with_check: |             | :one: |  |
| [1874](https://www.acmicpc.net/problem/1874) | 스택수열 | 스택 | :ballot_box_with_check: |             | :two: |  |
| [1406](https://www.acmicpc.net/problem/1406) | 에디터 | 스택 | :ballot_box_with_check: | | :one: |  |
| [17413](https://www.acmicpc.net/problem/17413) | 단어뒤집기2 | 스택, 큐 | :ballot_box_with_check: | | :one: | :1st_place_medal: |
| [10799](https://www.acmicpc.net/problem/10799) | 쇠막대기 | 스택 | :ballot_box_with_check: | | :three: | :1st_place_medal: |
| [17298](https://www.acmicpc.net/problem/17298) | 오큰수 | 분류 | :ballot_box_with_check: | | :four: |  |
| [17299](https://www.acmicpc.net/problem/17299) | 오등큰수 | 자료구조, 스택 | :ballot_box_with_check: | | :one: | :1st_place_medal: |
| [2609](https://www.acmicpc.net/problem/2609) | GCD,LCM | 수학 | :ballot_box_with_check: | | :one: | :1st_place_medal: |
| [1978](https://www.acmicpc.net/problem/1978) | 소수찾기 | 수학 | :ballot_box_with_check: | | :three: | :1st_place_medal: |
| [1929](https://www.acmicpc.net/problem/1929) | 소수구하기 | 수학 | :ballot_box_with_check: | | :four: | :1st_place_medal: |
| [6588](https://www.acmicpc.net/problem/6588) | 골드바흐 | 수학 | :ballot_box_with_check: | | :four: | :1st_place_medal: |
| [9613](https://www.acmicpc.net/problem/9613) | GCD합 | 수학 | :ballot_box_with_check: | | :three: | |
| [1403](https://www.acmicpc.net/problem/1403) | 1만들기 | DP | :ballot_box_with_check: | | :five: |  |
| [11726](https://www.acmicpc.net/problem/11726) | 2xn 타일링 | DP | :ballot_box_with_check: | | :six: |  |
| [11727](https://www.acmicpc.net/problem/11727) | 2xn 타일링2 | DP | :ballot_box_with_check: | | :six: | |
| [9095](https://www.acmicpc.net/problem/9095) | 1,2,3더하기 | DP | :ballot_box_with_check: | | :four: | |
| [11052](https://www.acmicpc.net/problem/11052) | 카드구매1 | DP | :ballot_box_with_check: | | :five: | :1st_place_medal: |
| [16194](https://www.acmicpc.net/problem/16194) | 카드구매2 | DP | :ballot_box_with_check: | | :five: | :1st_place_medal: |
| [15990](https://www.acmicpc.net/problem/15990) | 123더하기 5 | DP | :ballot_box_with_check: | | :six: | :1st_place_medal: |
| [10844](https://www.acmicpc.net/problem/10844) | 쉬운 계단수 | DP | :ballot_box_with_check: | | :six: | :1st_place_medal: |
| [2193](https://www.acmicpc.net/problem/2193) | 이친수 | DP | :ballot_box_with_check: | | :four: | :1st_place_medal: |
| [11053](https://www.acmicpc.net/problem/11053) | 가장 긴 증가하는 부분수열 | DP | :ballot_box_with_check: | | :four: | :1st_place_medal: |
| [14002](https://www.acmicpc.net/problem/14002) | 가장 긴 증가하는 부분수열4 | DP | :ballot_box_with_check: | | :four: | :1st_place_medal: |
| [1912](https://www.acmicpc.net/problem/1912) | 연속합 | DP | :ballot_box_with_check: | | :four: | :1st_place_medal: |
| [1699](https://www.acmicpc.net/problem/1699) | 제곱수의 합 | DP | :ballot_box_with_check: | | :six: | :1st_place_medal: |
| [2225](https://www.acmicpc.net/problem/2225) | 합분해 | DP | :ballot_box_with_check: | | :six: | :1st_place_medal: |
| [1149](https://www.acmicpc.net/problem/1149) | RGB거리 | DP | :ballot_box_with_check: | | :four: | :1st_place_medal: |
| [1309](https://www.acmicpc.net/problem/1309) | 동물원 | DP | :ballot_box_with_check: | | :four: | :1st_place_medal: |
| [11057](https://www.acmicpc.net/problem/11057) | 오르막수 | DP | :ballot_box_with_check: | | :four: | :1st_place_medal: |
| [9465](https://www.acmicpc.net/problem/9465) | 스티커 | DP | :ballot_box_with_check: | | :six: | :1st_place_medal: |
| [2156](https://www.acmicpc.net/problem/2156) | 포도주 시식 | DP | :ballot_box_with_check: | | :six: | :1st_place_medal: |
| [1932](https://www.acmicpc.net/problem/1932) | 정수삼각형 | DP | :ballot_box_with_check: | | :six: | :1st_place_medal: |
| [11055](https://www.acmicpc.net/problem/11055) | 가장 큰 증가 부분 수열 | DP | :ballot_box_with_check: | | :four: | :1st_place_medal: |
| [11722](https://www.acmicpc.net/problem/11722) | 가장 긴 감소하는 부분 수열 | DP | :ballot_box_with_check: | | :four: | :1st_place_medal: |
| [11054](https://www.acmicpc.net/problem/11054) | 가장 긴 바이토닉 부분수열 | DP | :ballot_box_with_check: | | :four: | :1st_place_medal: |
| [11398](https://www.acmicpc.net/problem/11398) | 연속합2 | DP | :ballot_box_with_check: | | :seven: | |
| [2133](https://www.acmicpc.net/problem/2133) | 타일 채우기 | DP | :ballot_box_with_check: | | :seven: | |
|  |  | | | | | |
|  |  | | | | | |



***



### 프로그래머스

|                           문제번호                           |        이름        | 유형 |         풀었음          | 다시 풀었음 | 체감 난이도 | 혼자 풀었는지 여부 |
| :----------------------------------------------------------: | :----------------: | :--: | :---------------------: | :---------: | :---------: | :----------------: |
| [64061](https://programmers.co.kr/learn/courses/30/lessons/64061?language=java) |    크레인 게임     | 배열 | :ballot_box_with_check: |             |    :two:    | :1st_place_medal:  |
| [42840](https://programmers.co.kr/learn/courses/30/lessons/42840) |      모의고사      | 배열 | :ballot_box_with_check: |             |    :one:    | :1st_place_medal:  |
| [12930](https://programmers.co.kr/learn/courses/30/lessons/12930) | 이상한 문자 만들기 |  큐  | :ballot_box_with_check: |             |   :three:   | :1st_place_medal:  |
| [42748](https://programmers.co.kr/learn/courses/30/lessons/42748) |      K번째 수      | 배열 | :ballot_box_with_check: |             |    :one:    | :1st_place_medal:  |



### 해커랭크

|                             이름                             | 유형  |         풀었음          | 다시 풀었음 | 체감 난이도 | 혼자 풀었는지 여부 |
| :----------------------------------------------------------: | :---: | :---------------------: | :---------: | :---------: | :----------------: |
| [Diagonal Difference](https://www.hackerrank.com/challenges/diagonal-difference/problem) | 배열  | :ballot_box_with_check: |             |    :one:    | :1st_place_medal:  |
| [Time Conversion](https://www.hackerrank.com/challenges/time-conversion/problem) | 배열  | :ballot_box_with_check: |             |    :one:    | :1st_place_medal:  |
| [Number Line Jumps](https://www.hackerrank.com/challenges/kangaroo/problem) | 수학? | :ballot_box_with_check: |             |    :one:    | :1st_place_medal:  |
| [Save the Prisoner!](https://www.hackerrank.com/challenges/save-the-prisoner/problem) | 수학? | :ballot_box_with_check: |             |   :three:   | :1st_place_medal:  |

***



### 이모지

| 	유형	 | 	이모지	 |
| :-----: | :-----: |
| 풀었음 | :ballot_box_with_check: |
|    다시 풀었음     |                       :checkered_flag:                       |
|    체감 난이도     | :one:<br />:two:<br />:three:<br />:four:<br />:five:<br />:six:<br />:seven:<br /> |
| 혼자 풀었는지 여부 |                      :1st_place_medal:                       |

