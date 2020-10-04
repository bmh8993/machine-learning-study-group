# Multivariate Linear Regression

다변량 선형 회귀
multivariate linear regression
Y값을 예측하는 여러개의 feature 혹은 변수를 표현하는 말

- x<sub>j</sub><sup>(i)</sup> = value of feature j in the ith training example
- x<sup>(i)</sup> = the input (features) of the ith training example
- m = the number of training examples
- n = the number of features

추론의 파라미터를 지정하는 법


## Gradient Descent
- 목적 : cost funtion J(Θ)가 최소화되는 Θ 값을 찾는 것
- 여러개의 feature가 있고 feature의 단위크기가 비슷하다면 서로다른 feature라도 범위가 같다면 Gradient Descent 더 빠르게 수렴할 수 있다.
### Feature Scaling
- feature의 범위가 매우 작은 범위나 매우 큰 범위는 범위설정을 다시해줘야함
- feature가 같은 크기나 정확하게 똑같은 범위가 아니더라도 걱정할 필요없음
- Gradient Descent가 훨씬 빨라지면 되기 때문
- Feature Scaling를 진행하면 적은수의 반복으로도 수렴가능
### Mean normalization
 if x<sub>i</sub> represents housing prices with a range of 100 to 2000 and a mean value of 1000, then, x<sub>i</sub> := (price-1000)/1900

## Debugging
- Gradient Descent가 잘 돌아가게하기 위한 방법
- learning rate α 구하는 방법


### 그래프 분석
- Gradient Descent할때마다의 cost function의 값
- Gradient Descent잘 돌아간다면 J(Θ)는 매 반복마다 감속해야 함
- 고반복(300~400이상) Gradient Descent 거의 수렴한 상태 cost function이 더 이상 줄어들지 않기 때문 = 수렴했는지 아닌지 알수 있음
- 필요한 반복회수는 경우에 따라 다름, 사전에 알기 어려움 그래프를 그리고 그것을 보면서 확인하는것이 일반적
- 그래프 외에는 test를 하는 알고리즘이 존재한다 = automatic convergence test
  - J(Θ)의 감소량이 어떤 작은값 입실론ε(10^-3)보다 작을때, 즉 한번 반복했을때 ε보다 작을 때
  - 하지만 이 임계값을 결정하는것도 여러움
  - 그렇기 때문에 그래프를 그리는 것이 더 좋다.
- Gradient Descent가 제대로 동작하지 않을 때 주의사항
  - J(Θ)가 횟수마다 증가할시 제대로 동작하지 않는 것
    - 코드의 오류가 없다는 가정하에 알파의 값이 너무 커서 발생함
    - 이 때 더 작은 알파를 사용해야한다.
    - 보통 어떤 함수를 최소화 하려고할때 발생
  - J(Θ)값이 커졌다 작아졌다 반복되는 형상
    - 위의 case와 동일하게 대처
    - 단 너무 적게 설정하지 않는 것이 중요 (너무 천천히 수렴하기 때문)
- 알파값 세팅은 보통 10배차이정도로 설정한다
  - 교수는 0.001 0.003 0.01 0.03 0.1 0.3 1 이런식으로 설정함
    - 가능한 가장 작은값과 가능한 가장 큰값을 설정
    - 각각에서 조금씩 좁혀나감
  - 알파값에 따른 J(Θ)를 그림
  - J(Θ)가 빠르게 감소할 때의 알파 값을 선택

## Polynomial Regression (다항 회귀)
- feature를 선택하는것과 밀접하게 관계있음
- data를 잘 표현하는 모델을 만들것인가?
  - multivatiant linear regression의 구조 이용하여 알고리즘 간단히 수정
  - 3차 함수를 만들면서 크기의 범위차이가 매우 커지게되면 feature scailing을 적용시켜 서로 비슷한 범위를 가질수 있게 한다
  - 집값예시에서 2차식 모델은 data를 표현하는데 적합하지않다. 집을 예시로헀을때 사이즈에따라 가격이 증가하다가 떨어지기 때문
  - 3차식 말고 다른방법 : 2제곱 대신 2제곱근 방식을 택하는것
    - h<sub>Θ</sub>(x) = Θ<sub>0</sub>+Θ<sub>1</sub>(size)+Θ<sub>2</sub>√(size)
      - 갈수록 평편해지지만 하강하진 않음
  - 자동으로 어떤 feature를 선택할지 골라주는 알고리즘 존재

# Computing Parameters Analytically
- Normal equation: method to solve for Θ analytically
- J 최소화 :  J 편미분, 각각 모든 파라미터 Θ_j에 따라 차례대로 미분하여 모두 0가 되게하여 Θ값을 구함
- design matrix
- (X^TX)^-1X^Ty
- pinv(X'\*X)\*X'*y
  - pinv : 행렬의 역행렬을 계산하는 함수

## gradient descent vs normal equation
- 가정 : m training examples, n features
- gradient descent
  - 알파 정해야함 (최적의 알파)
  - 많은 반복필요 (느려질수있음)
  - n이 매우 많을때 효과적임
- normal equation
  - 알파 선택할 필요없음 (편리, 구현간단)
    - feature scaling 할 필요없음
  - 반복필요 없음
  - (X'X)의 역행렬을 계산해야함
  - n이 매우 많으면 느려짐
    - 일반적으로 n이 1만을 넘어서면 gradient descent로 하는게 나음(정확한 시점은 정해져있지않음)

## Normal equation Noninvertibility
- pinv vs int
  - pinv : 역행렬이 없어도 theta값을 정확히 계산
- 행렬 X'X 역행렬이 없는경우나 특이행렬인 경우 (희귀한 경우)
  1. 문제에서 불필요한 features가 존재할경우 (추천)
      - 붎필요한 행렬이 feature가 있으면 지워야할 것들은 지우는것이 좋음
  2. 너무 많은 feature가 존재할경우 (m이 n보다 작거나 같을 경우)
     - ex) m=10, n=100이면 세타가 101차원
       - 10개의 training example로 101개의 파라미터를 표현하려 하는 것
       - 해결 방안 : feature몇개를 제거하거나 regularization 사용(후반에 배울 주제)
