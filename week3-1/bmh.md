# Logistic Regression
변수 y가 이산형 값을 지니는 경우
- 0 = negative class
- 1 = positive class
분류 문제를 해결할 때에 선형회귀를 사용 X
-> 어떠한 값으로 h가 바뀜

- Logistic Regression
  - 0 <= h_theta(x) <= 1 (예측값의 볌위)
  - 분류 알고리즘으로 사용

## Hypothesis Representation
Logistic Regression의 범위

- 0 <= h_theta(x) <= 1 (예측값의 볌위)
<img width="335" alt="image" src="https://user-images.githubusercontent.com/45564139/95013325-8c075680-067a-11eb-8059-9959ea349f2e.png">
-> P(y=0|x;theta) + P(y=1;theta) = 1

g(z)의 그래프를 보면

y = 1(g(z)>= 0.5)일 경우에 z >=0 이고

y = 0(g(z) <0.5)일 경우에는 z <0 이다

## Decision Boundary
y = 1 or 1로 분류가 가능한 직선을 만들 수 있는 경우(예시는 1차함수)

## Non-linear decision boundaries
y = 1 or 1로 분류가 가능한 선이 직선이 아닌 경우(예시는 원)

## Cost Function
로지스틱 회귀에서 변수 theta를 결정하는 방법

-> 비용함수는 오차 제곱 1/2과 같다

-> 비볼록함수를 사용하면 전체 함수의 최소값에 도달한다는 보장이 없다

-> 로지스틱 회귀를 위한 새로운 비용함수를 확인해봐야한다.

## Logistic regression cost function
### if y =1
  - h(x)가 0에 가까워지면 cost는 무한대
### if y = 0
  - h(x)가 1에 가까워지면 cost는 무한

## Simplified Cost Funcition and Gradient Descent
하나의 식으로 합친 cost func
- Cost(hΘ(x),y) = -ylog(hΘ(x)) - (1-y)log(1-hΘ(x))

## Advanced Optimization
### 장점:
  - α manually하게 선택할 필요없음
  - 보통 gradient descent 보다 빠름
### 단점:
  - gradient descent 보다 더 복잡함

## Multiclass Classfication: (one-vs-all or one-vs-rest)
결과 값이 여러개로 분류되는 문제
ex)
- 이메일 분류시 여러개의 태그
- 병에걸리지않음 / 감기 / 독감
- 날씨(맑음, 흐림, 비, 눈)

세 개의 로지스틱 회기를 훈련시켜 각각 y=i 일 확률을 계산
