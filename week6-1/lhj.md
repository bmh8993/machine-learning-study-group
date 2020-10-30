# Evaluating a Leaning Algorithm(Learning Algorithm 평가)
## Deciding What to Try Next
- 적당한 가정을 만들어 새로운 집합이 생길시 에러가 발생했다는것은 가정함수 h_𝜃(x^(l))이 틀렸다는 것
  - training example을 더 확보한다.
  - feature가 너무 많거나 적은지 확인하여 조절한다.
  - polynomial feature들을 더 추가한다.
  - regularize에 영향을 주는 λ값을 줄이거나 증가시킨다.

## Evaluating a Hypothesis
- 정확한 문제가 무엇인지 진단이 필요함.
- 가정 평가
  - 데이터집합을 training set, test set 두가지로 분류
  - 비율 7:3
  1. training set을 통해 J(𝜃)값을 최소로하는 𝜃값을 구함
  2. 구한 𝜃 값과 test set을 가지고 J_test(𝜃)를 계산
  3. 그 결과값이 test set error

  - Logistic regression의 경우도 마찬가지로 진행
- learning algorithm이 training set에 잘 맞는다고해서 그것이 좋은 가정이라는것을 의미하지 않는다.
- 좋은 가정 함수를 선택하기 위해서
  - polynmial degree를 테스트하고 error result를 확인

# Bias vs. Variance
## Diagnosing Bias vs. Variance
- polynomial d의 차수와 가정이 underfitting 이거나 overfitting인지 관계에 대해 확인
- polynomial d가 1인경우 5개의 데이터가 가정함수와 잘 맞지않은 경우 high bias(underfit)
- d=2인경우 가정함수와 잘 맞음 : just right
- d=4인경우 이상적인가정이라고 생각할수있지만, 새로운데이터가 들어오면 맞지않는 경우 : hig variance (overfit)

- Bias(underfit)상태는 J_train(𝜃)와 J_cv(𝜃)값이 매우 큰 경우
- Variance(overfit)상태는 J_train(𝜃)는 낮지만, J_cv(𝜃)는 J_train(𝜃)에 비해 매우 큰 경우

## Regularization and Bias/Variance
- Regularization을 적용한 Linear regression의 경우
  - cost function J(𝜃)에  λ/2m sigma(j=1~m)𝜃_j^2가 추가된 경우임
    - J(𝜃) = 1/2m sigma(i=1~m)(h_𝜃(x^(i))-y^(i))^2 에 위 람다식 추가
  - regularization 정도는 λ에 따라 결정
    - λ값이 큰경우 모든 theta값이 0에 가까워지므로 가정함수역시 theta zero값만 남게됨
      - 상수함수꼴의 그래프로 그려짐
      - 모든 data들에 잘 맞지 않게 되어 high bias 상태가 됨
    - λ이 적당한 값을 가지고 regularization하게 되면 잘 맞는 가정함수가 됨
    - λ값이 너무 작으면 regularization이 거의 적용되지 않으므로 High variance상태가 됨
- λ값을 선택하는 과정
  - λ값을 조금씩 증가시켜가면서 해당 λ값을 가지고 training data를 통해 regularization이 적용된 J(𝜃)값을 최소로하는 𝜃값을 구한다.
  - 그 각각의 𝜃값을 가지고 J_train(𝜃)값을 구한다.
  - λ=0인 경우로 구한다.
  - J_train(𝜃)에서 구한 𝜃값을 가지고 J_cv(𝜃)값을 구한다,.
  - J_cv(𝜃)값 또한 regularization이 적용되지 않은 λ=0식으로 구한다.
  - 그 후 각각 λ=0에 해당하는 J_cv(𝜃)중 최소값을 갖게하는 𝜃값을 선택하여 Test set들에 적용한다.
  - Test set 또한 regularization이 적용되지 않은 λ=0식으로 구한다.

- 그래프에서 λ값이 작은 경우 J_train(𝜃)값은 작지만 J_cv(𝜃)값은 매우 큰 것을 볼 수 있다.
  - variance 상태 (overfit)
  - train데이터에 대해서는 잘 맞지만 새로운 데이터가 들어왔을때 잘 맞지 않은 경우
- λ값이 커질수록  J_train(𝜃)값은 커지게 되고(error증가) J_cv(𝜃)역시 줄어들었다가 다시 커지는것을 확인할 수 있다.
  - bias
- 적당한 λ값을 선택해야 "just right"상태가 되는것을 확인할 수 있다.

## Learning Curves
- 기계 학습 가정 모델이 제대로 작동하는지 시각적으로 표현할 수 있는 유용한 도구 중 하나
- J_train(𝜃)값과 J_cv(𝜃) 값을 활용
- 그래프의 x축은 training set의 크기로 둠
- 가정함수 h_𝜃(x) = 𝜃_0 + 𝜃_1 x + 𝜃_2 x^2
  - 데이터가증가함에 따라 m이 많아질수록 error가 증가함
  - m=1일때는 J_train(𝜃)값은 거의 0에 수렴
  - m이 증가할수록 J_train(𝜃)값이 증가함
  - J_cv(𝜃)의 경우는 Jtrain(𝜃)의 반대

- High bias인 경우의 Learining Curves
  - 가정함수 h_𝜃(x) = 𝜃_0 + 𝜃_1 x
  - training set size가 작은 경우에는 J_train(𝜃)값이 매우 작고 J_cv(𝜃)가 매우 큼
  - training set size가 큰 경우 J_train(𝜃)와 J_cv(𝜃)가 모두 큰 error를 갖게 되고 서로 유사하게 됨
  - high bias 상태에서는 더많은 training data가 주어져도 error가 낮아지지 않음
  - 이 경우에는 가정을 바꿔야 함

- High variance 상태
  - polynomial = 100인 가정함수
  - training set size가 작은경우 J_train(𝜃)값은 작고, J_cv(𝜃)는 매우 큼
  - m(training set size)가 커질수록 J_train(𝜃)는 증가하고 J_cv(𝜃)값은 감소한다.
  - training set을 추가하는것이 J_train(𝜃)와 J_cv(𝜃)간의 차이를 줄이는데 도움이 됨

1. 더 많은 training example이 필요한 경우 : high variance
2. feature의 수를 줄여보는 시도를 해볼수있는 경우 : high variance
3. 더 많은 feature들을 더하는 경우 : high bias
   - h_𝜃(x) = 𝜃_0 + 𝜃_1 x 인 경우에는 잘 맞지 않음
   - h_𝜃(x) = 𝜃_0 + 𝜃_1 x + 𝜃_2 x^2 의 경우 잘 맞음
4. Polynomial feature들을 더하는 경우 = 3번과같은 high bias 상태 , 𝜃_2의 feature로 x^2를 추가한것
5. λ값을 줄이는 경우 : high bias
   - λ값이 크면 theta값이 0에 수렴하게되어 high bias 상태가 될 수 있음
6. λ을 증가시켜야 하는 경우 : high variance
   - λ값을 크게하여 theta의 값의 영향력을 줄일 필요가 있음.

- Neural network 적용
  - Hidden layer가 적거나 parameter들이 적은경우 high bias 가 될 가능성이 높음
    - computing 이 빠르다는 장점이 존재
  - parameter들이 많거나 hidden layer가 많은경우 overfitting(high variance)가 생길 가능성이 높음
    - 많은 computing 계산이 필요함
    - λ를 통해 regularization하여 overfitting 문제 해결 가능
