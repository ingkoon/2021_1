# 알고리즘 2주차 정리

## 1. 알고리즘이란?
- 알고리즘은 문제를 해결하는 단계적 절차 또는 방법
- 주어지는 문제는 컴퓨터를 이용하여 해결 가능해야 함
- 입력이 주어지고 수행한 결과인 해를 출력

- 알고리즘의 요건
  - 정확성(Correctness)
    - 알고리즘은 주어진 입력에 대해 올바른 해를 주어야 한다.
  - 명확성(Definiteness, 수행성)
    - 알고리즘의 각 단계는 컴퓨터에서 수행가능해야 한다.
    - 명확하게 표현되어야 함. 모호성 배제
  - 유한성(Finiteness)
    - 알고리즘은 일정한 시간 내에 종료되어야 한다.
  - 효율성(Effciency)
    - 알고리즘은 효율적일수록 그 가치가 높아진다.
    - 구해진 해가 유효해야 한다
    - 
<br>  

----

<br>
<br>

## 2. 최초의 알고리즘
- 유클리드의 최대 공약수 알고리즘
  - 최대 공약수는 2개 이상의 자연수의 공약수들 중에서 가장 큰 수
  - 자연수의 최대공약수는 큰 수에서 작은 수를 뺀 수와 작은 수와의 최대공약수와 같다는 성질을 이용
  

## 3. 알고리즘의 표현 방법
- Algorithm의 표현
  1. 자연어(Natural Language)
  2. Algorithm 언어 의사코드(pseudo code)
  3. Flow chart
  4. 특정 Program언어(C, C++, Java 등)


- 자연어로의 표현
> **step1.** Divide the larger number by the smaller number, and get the remainder <br><br>
> **step2.** If the ramiander is zero, then the smaller number is **GCD** and stop. <br> otherwise, go to step 3 </br></br>
> **step3.** Replace the larger number by the smaller, and the smaller by the remainder. <br>Go to step1

</br>

- Algorithm 언어로의 표현
> **step1.** Remainder <- Larger MOD smaller <br><br>
> **step2.** if [remainder = 0] THEN GCD <- Smaller and STOP <br><br>
> **step3.** Larger <- Smaller </br>
>            Smaller <- Remainder </br>
>            Go To step 1.

<br>

----

<br>

## 4. 알고리즘의 분류

- 문제의 해결 방식에 따른 분류
  - 분할 정복알고리즘
  - 그리디 알고리즘
  - 동적 계획 알고리즘
  - 근사 알고리즘
  - 백트래킹 기법
  - 분기 한정 기법

- 문제에 기반한 분류
  - 정렬 알고리즘
  - 그래프 알고리즘
  - 기하 알고리즘

- 특정 환경에 따른 분류
  - 병렬 알고리즘
  - 분산 알고리즘
  - 양자 알고리즘
  
- 기타 알고리즘들
  - 확률 개념이 사용되는 랜덤 알고리즘
  - 유전자 알고리즘

|문제해결방식|문제 기반|특정환경 기반| 기타
|------|---|---|----|
|- 분할정복<br>- 그리디<br>- 동적 계획<br>- 근사<br>- 백트래킹<br>- 분기한정|- 정렬<br>- 그래프<br>- 기하|- 병렬<br>- 분산<br>- 양자|- 랜덤<br>- 유전자

<br>

----

<br>

## 5. 알고리즘의 효율성 표현
- ### 알고리즘의 효율성
  
|시간복잡도|공간복잡도|
|----|----|
|알고리즘의 <br>수행시간|수행시간동안의 <br> 메모리 공간 크기 등|

<br>

- ### 일반적으로 시간복잡도가 주로 사용
  - 시간복잡도는 알고리즘이 수행하는 
  **기본적인 연산 횟수를 입력 크기에 대한 함수** 로 표현
  - 예시
    - 10장의 숫자 카드 중에서 최대숫자찾기 순차탐색으로 찾는 경우에 숫자 비교가 기본적인 연산이고, 총 비교 횟수는 9
    - n장의 카드가 있다면,(n-1)번의 비교 수행: 시간복잡도는 (n-1)

  <br>

- ### Algorithm 복잡도의 의미
  - Computation time에 의한 측정의 비효율성
    1. computer기종마다 능력의 차
    2. program 작성자의 능력의 차
    3. 측정을 위한 수정 작업에 많은 시간 소요
   - Complexity = Amount of Computation(계산량)
     - 기본 연산의 횟수
       - 연산의 횟수가 데이터 사이즈에 따라 달라짐
     - 보조연산은 무시
       - 초기값 설정, 반복횟수 계산, while문의 조건의 판단, 배열의 첨자기 계산 등....

  <br>

  -  ### 알고리즘의 복잡도 표현방법
     -  최선 경우 분석(best case analysis)
     -  평균 경우 분석(average case analysis)
     -  최악 경우 분석(worst case analysis)

  - ### Complexity의 표현
    - Best case
      - 타당성이 부족
      - 예) 탐색 알고리즘: B(n) = 1 (n에 관계 없이)
    - Average case
      - 타당성이 있음
      - 계산이 어렵다
    - Worst case
      - 데이터의 사이즈에 따라 달라짐
      - Average case와 선형적으로 비례하는 성질이 있음
    - Complexity
      - 알고리즘을 평가하는 기본 수단
      - Algorithm을 수행할 때 최악의 경우에 수행되는 기본 연산 횟수로 표현함
  
<br>

----

<br>

## 6. 복잡도의 점근적 표기

- 시간 (또는 공간)복잡도는 입력 크기에 대한 함수로 표기
- 단순한 함수로 표기하기 위해
  - **점근적 표기 (Asymptotic Notation)**를 사용
  - 입력 크기 n이 무한대로 커질 때의 복잡도를 간단히 표현하기 위해 사용
  - 
|빅오 표기|빅오메가 표기|세타 표기|
|---|---|---|
|복잡도의 **점근적 상한**|복잡도의 **점근적 하한**|O-표기와 Ω-표기가 같은 경우에 사용
|복잡도가 f(n) = 2n<sup>2</sup>-8n+3라고 하면<br>교차점 이후의 모든 n에 대하여 <br> - cn<sup>2</sup>>f(n)을 만족하는 c가 존재, 단 c>0<br>다항식의 최고차 항만 계수없이 취하면 됨<br>따라서 f(n)의 O-표기는 O(n<sup>2</sup>)|f(n) = 2n<sup>2</sup>-8n+3의 오메가 표기는 Ω(n<sup>2</sup>)</br> f(n) = Ω(n<sup>2</sup>)은 n이 증가함에 따라 2n<sup>2</sup>-8n+3>cn<sup>2</sup>을 만족하는 c가 존재<br>예를 들어 c = 1 <br> O-표기 때와 마찬가지로, Ω-표기도 복잡도 **다항식의 최고차항만 계수없이**취하면 된다.| f(n) = 2n<sup>2</sup>+10n+3 = O(n<sup>2</sup>) = Ω(<sup>2</sup>)이므로, f(n) = θ(n<sup>2</sup> <br> f(n)은 n이 증가함에 따라 n<sup>2</sup>과 **동일한 증가율**을 가진다 라는 의미이다

<br>

|O-표기|의미|
|---|---|
|O(1)|상수 시간(Constant time)|
|O(n)|선형시간(Linear time)|
|O(nlogn)|로그 선형 시간(Logarithmic time)|
|O(n<sup>2</sup>)|제곱 시간(Quadratic time)|
|O(2<sup>n</sup>)|지수 시간(Exponential time)|

<br>

## 7.왜 효율적인 알고리즘이 필요한가?
- ### 10억개의 숫자를 정렬
  - PC에서 O(n<sup>2</sup>) 알고리즘
    - 버블 정렬
    - 300여년
  - O(nlogn) 알고리즘
    - 퀵정렬
    - 5분

<br>

|O(n<sup>2</sup>)|1,000|1백만|10억|
|---|---|---|---|
|PC|<1초|2시간|300년|
|슈퍼컴|<1초|1초|**1주일**|

<br>

|O(nlogn)|1,000|1백만|10억|
|---|---|---|---|
|PC|<1초|1초|5분|
|슈퍼컴|<1초|1초|**<1초**|

<br>

  - 효율적인 알고리즘은 슈퍼컴퓨터보다 더 큰 가치가 있다.
  - 값비싼 H/W의 기술 개발보다 **효율적인 알고리즘 개발이 훨씬 더 경제적**