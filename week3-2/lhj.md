# Solving the Problem of Overfitting

## The Problem of Overfitting
- 과소적합 높은 편향을 갖고있다
  - 우리모델이 데이터에 제대로 맞지 않음
  - 강한 preconception 을 갖고있다
  - 강한 편향(bias)를 갖고 있다
- 다차원 함수를 이용함으로써 데이에 적합하게 맞출수있음(변수 늘어남)
- 과적합(overfitiing), 높은분산(high variance)
  - 고차항 함수를 갖는다고해서 이 함수가 데이터를 정확히 예측할거라고 생각되지 않음

- 로지스틱 리그레션
  - 고차항 함수(극단적), 정말 좋지않은 예측 -> 과적합, 일반화되지않음

It makes accurate predictions for examples in the training set, but it does not generalize well to make accurate predictions on new, previously unseen examples.

## 어떻게 과적합인가?
- 가설함수의 그래프 그려보기
- 학습 데이터가가 너무 적거나 너무 많은지 확인하기

- 과적합 문제를 해결하기위해
1. 특성의 갯수를 줄이는 방법
  - 모델 셀렉션 알고리즘, 수동적으로 특성을 선택
  - 문제점 : 특성을 버림으로써 문제점도 문제에 포함된 정보도 같이 버리게 됨
2. 레귤러리제이션(정규화)
  - 모든 특성을 남기되 각 특성이 갖는 영향 규모를 줄이는 것(새타값이 미치는 영향을 줄이는 것)
  - Regularization works well when we have a lot of slightly useful features.


## Cost Function
- Regularization
  - 파라미터가 정규화를 통해 작은 값을 갖게 되면 복잡한 가설함수들이 더욱 간단해질것이다.
  - 정규화를 통해 보다 smoothㅎ라고 simple해진 함수는 가설함수에 좋다.
  - 단 람다가 너무 크면 underfitting하는 문제가 발생하여 새타중 새타 제로만 남게 될것이다. 그렇기 때문에 적절한 람다값을 정해주는것이 중요함.

- Small values for parameters
  - "Simpler" hypothesis
  - Less prone to overfitting

- What if \lambdaλ is set to an extremely large value (perhaps too large for our problem, λ=10^10) ?
   - Algorithm results in underfitting (fails to fit even the training se

- Using the above cost function with the extra summation, we can smooth the output of our hypothesis function to reduce overfitting. If lambda is chosen to be too large, it may smooth out the function too much and cause underfitting.

## Regularized Linear Regression
- 정규화 선형회귀, 논리회귀 둘다 가능
- 선형 회귀에서 최적 파라미터를 찾는데는 Gradient Descent와 Normal Eqution을 이용하는 2가지 방법이 존재
- Non-invertibility
  -  It is said that X is non-invertible if m ≤ n. The correct statement should be that X is non-invertible if m < n, and may be non-invertible if m = n.

- linear regression 정규화 방법
1. Gradient Descent(경사하강법)
    - 1 - alpha*(lambda/m)는 항상 1보다 작아야 한다.
2. Normal Equation
  -  Normal equation 정규화를 사용하면 역행렬이 항상 존재함

## Logistic Regression 정규화
- 세타 제로에 대해서 따로 업데이트를 진행
The second sum, \sum_{j=1}^n \theta_j^2∑
j=1
n
​
 θ
j
2

  means to explicitly exclude the bias term, \theta_0θ
0
​
 . I.e. the θ vector is indexed from 0 to n (holding n+1 values, \theta_0θ
0
​
  through \theta_nθ
n
​
 ), and this sum explicitly skips \theta_0θ
0
​
 , by running from 1 to n, skipping 0. Thus, when computing the equation, we should continuously update the two following equations:
