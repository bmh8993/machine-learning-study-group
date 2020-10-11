# The Problem of Overfitting
선형회귀와 로지스틱 회귀에 모두 적용되는 용어
#### high bias, underfitting
- 잘 안맞는 가설
- 간단하거나 적은 특징을 다룰 때
#### overfitting, high variance
- 너무 과하게 잘 맞는 가설
- 가설이 가능한 많은 연습용 데이터에 잘 들어맞는 경우 새로운 데이터(학습 데이터)에 대해서 일반화가 불가능
- 학습 데이터로는 비용함수가 거의 0에 가까움
- 다항 함수를 만들면 이와 같은 현상이 발생(불필요한 커브)

## overfitting 발생 여부를 판단하는 방법
### 직접 가설 함수를 그려보는 방법
- 하지만 feature가 많은 경우 다항식의 차수를 선택하기 어려워 시작적으로 그리기가 힘들 수 있다.
- 어떤 feature를 선택하여 그릴지도 고민해야 해서 매우 복잡
- 또한 feature의 수보다 data의 수가 적으면 overffing이 발생할 수 있다.

## overfit 문제를 해결하는 방법

### 1. feature를 줄이는 방법
### 2. regularization
- 각각의 파라미터에 대해 패널티를 설정한 후, 비용함수를 재정립하고 이에 따라 파라미터의 영향력을 줄여나감으로서
- overfitting을 해결

# Regularized linear Regression
## cost function
- theta_0를 고려하지 않음
- theta_0를 포함하는 것과 별 차이가 없어서 신경쓰지 않음
- 람다는 Regularization Parameter를 뜻하고 적절한 값을 정하는 것이 중요
- 너무 큰 값응ㄹ 주면 모든 파라미터가 사라지기 때문에 가설함수에는 theta_0만 남게되어 underfintting

## Gradient Descent
- ragularization 과정에서 theta_0에 대해서 penalize를 하지 않았다 그래서 gradient descent를 적용할 때
이를 따로 처리해주어야한다.
- leaning_rate > 0,m > 0, lambda > 0를 만족하므로 1-alpha(lambda/m) < 1 이다.
- 결국 반복하는 과정에서 theta_j가 점점 작아짐

## Normal Equation
- j = 1부터 시작이지만 0인 경우를 더해서 (n+1) * (n+1)의 크기
- 역행렬의 존재를 항상 보장

# Regularized Logistic Regression
## cost func
<img width="532" alt="image" src="https://user-images.githubusercontent.com/45564139/95672873-1e5dac00-0bdf-11eb-8b05-1fde06bd6366.png">

Regularized Logistic Regression의 cost func

## Gradient Descent

- 외관상으로는 Linear Regression과 같은 것으로 보이지만 h_theta(x)가 달라서 똑같이 동작하지 않음
