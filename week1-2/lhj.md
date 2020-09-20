# Linear Regression with One Variable

## 훈련 집합
목적 : 학습 알고리즘이 어떻게 돌아가느냐
- Learning Algorithm
- m : Number of training examples
- x's : "input" variable / features
- y's = "output" variable / "target" variable
- (x, y) - one training example
- (x<sup>i</sup>, y<sup>i</sup>) - i<sup>thata training example</sup>
- h : 가설(x에서부터 y까지의 maps)
  - h<sub>Θ</sub>(x) = Θ<sub>0</sub> + Θ<sub>1</sub>x (모형들의 파라미터 Θ)
  - 가설 h를 어떻게 표현할 것인가에 대해
  - x의 선형함수인 y를 예측하는것
  - x의 직선함수인 y를 예측하는것
- 선형 함수를 쓰는 이유 : 간단한 단계부터 비선형함수까지 학습할 것
  - 예) 선형회귀의 값은 하나(=x) 모든 가격 예측
  - 단일변량(하나의 값) 선형 회귀

## 비용 함수(Cost Function)
 - 주어진 데이터에 가장 가까운 일차함수 그래프를 얻는것이 목적
 - 2개의 파라미터, Θ 를 어떻게 고를 것이냐가 문제
  - 선택에 따라 다른가설, 다른 가설함수를 갖게 됨
  - 직선이 자료와 얼마나 일치하는가
- 최소값 찾기
- 1/m2 평균값 최소화된 훈련집합에서 합계의 제곱을 곱한값으로 접근
- 선형회귀에 대한 저반적인 목적 함수
- 비용함수를 알아내기 위한 공식
  - J(Θ<sub>0</sub>, Θ<sub>1</sub>) : cost function (squard error function/Mean squared error)
  - 예제
    1. 가설함수(h(x))와 비용함수(J(Θ<sub>1</sub>))의 이해
    2. Θ<sub>0</sub>, Θ<sub>1</sub> 설정


## Parameter Learning
- gredient descent 알고리즘 : 기계학습의 모든곳에 사용되는 알고리즘
1. Θ<sub>0</sub>, Θ<sub>1</sub> 초기값 추측( 일반적으로 0,0설정)
2. 조금씩 바꿈 J(Θ<sub>0</sub>, Θ<sub>1</sub>)를 줄이기위해
3. 시작점에따라 다른지역적 최적값에 도달
    - **:=** 할당한다는 기호
        >ex) a:=b b의값을 a에 할당한다.
        a := a+1 a에 1을 더한다는 뜻
        a = b 참/거짓의 의미 (a의 값과 b의값과 같다고 주장하고있는것)
        α : Learning rate(훈련 비율)

- 동시에 값을 바꾸는이유 ?
  - 기울기하강에서 값을 대입하는 방식

- α 값에 따른 문제접근 차이
    - α값이 매우 작다면 기울기하강이 느리다. 최소값에 이동하기에 많은 이동이 필요함
    - α 매우 크다면 최소값보다 더가거나 값을 바꾸거나 방향을 바꾸는것도 어려워질수있음
    - α 고정되어있다면, 하강 기울기는 최소값에 영향을 미치지 못함

- Θ<sub>1</sub> 값이 지역적 최적 최소값이면 미분계수는 0 , 기울기 탄젠트값은 0
    - 하강 기울기 Θ<sub>1</sub> = Θ - 알파 값에 0 곱한값과 같음

- 기울기 하강을 이용한 비용함수차의 제곱을 최소화하는 것
  - 부분 미분계수 , 함수 J에 끼치는 영향

- CONVEX function : 전역 최적값만 갖을뿐 지역 최적값은 없음
    - 기울기 하강은 항상 전역 최적값에 접근

- "batch" Gradient Descent (집단 기울기 하강)
  - 기울기하강의 단계를 지나다보면 m개의 훈련예제들의 값을 더하게됨
  - 모든 훈련예제들의 전체 집단을 나타냄
  - 몇몇 하강기울기는 집단의 값과 다를때가 있음
  - 전체적인 훈련집합을 보는것이아닌 훈련집합의 작은 부분집합을 볼것

Gradient descent can converge even if \alphaα is kept fixed. (But \alphaα cannot be too large, or else it may fail to converge.)

For the specific choice of cost function J(\theta_0, \theta_1) used in linear regression, there are no local optima (other than the global optimum).
