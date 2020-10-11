# Multiple features

하나 이상의 변수나 features를 다루기

m = traning 데이터 개수

n = feature 개수

x<sup>(i)</sup> = 데이터 하나에 입력되는 feature i

x<sub>j</sub><sup>(i)</sup> = feature i 안에서 j 번째

- feature가 많은 경우 다음과 같이 표현

h<sub>θ(x)</sub> = θ<sub>0</sub> + θ<sub>1</sub>x<sub>1</sub> + θ<sub>2</sub>x<sub>2</sub> + ... + θ<sub>n</sub>x<sub>n</sub>

여기서 x<sub>0</sub>  = 1이라고 했을 때

⇒ h<sub>θ</sub>(x) = θ<sup>T</sup>X

---

# Gradient Descent for Multiple Variables

여러개의 feature가 있을 때에 경사 하강법을 적용하는 방법

<img width="1016" alt="1" src="https://user-images.githubusercontent.com/45564139/95010780-0f1eb180-0667-11eb-8ff4-9fdc41f3e66a.png">

---

# Gradient Descent for Practice 1 - Feature Scaling

## 1. feature scaling

feature scaling을 하기 이전에는 수없이 많은 경로를 통해 최소 값을 찾을 수 있음($J(θ)$의 그래프가 얇고 긴 타원형의 그래프이기 때문에) feature scaling을 하게 되면 빠르게 최소값을 찾아갈 수 있음($J(θ)$의 그래프가 전보다 원에 가까운 타원의 그래프 이기 때문에)이다

x<sub>i</sub>를 조절해야하는데 -1, 1과 가까운 수면 좋다. 100처럼 과하지 않게 크거나 0.0001처럼 과하게 작지 않으면 된다.(사람마다 규칙은 다름 응교수님은 -3~3까지 ok)

## 2. mean normalization

- feature scaling 이후에 mean normalization이라는 것을 할 수 있다.

평균적으로 집의 크기가 1000이면

x<sub>1</sub> = size-1000/2000→ $-0.5≤x_1≤0.5$

평균적으로 방의 개수($x_2)$가  2개 이면

x<sub>2</sub> = bedrooms-2/5→-0.5≤x_2≤0.5$

(x - 평균값) / (max - min) 또는

(x - 평균값) / (표준편차)

사실 5 -1 =4 이지만 너무 정확할 필요가 없다

feature scaling은 너무 정확할 필요가 없다

---

# Gradient Descent for Practice 2 - Learning Rate

## 1. debugging → gradient descent가 잘 돌아가게 하기 위한 방법

→ 반복 회수에 따른 cost Func의 최소값

수렴하는지 안하는지 테스트하는 알고리즘(automatic convergence test)

⇒ 증명하는 방식은 cost func의 감소량이 어떤 작은 값보다 작을 때,

⇒ 즉, 한 번 반복했을 때 0.001 보다 작을 때

### gradient descent가 제대로 동작하지 않을 때, 확인사항

1. 반복회수가 커질 수록 최소값도 커진다
→ 이때는 더욱 작은 learning rate를 사용해야한다

    단, 코드의 오류가 없다는 가정하에 판단할 것

2. 작고 커지고를 반복한다
→ 이때는 더욱 작은 learning rate를 사용한다.

### learning rate에 따른 그래프 변화

## 2. learning rate(알파)를 고르는 방법, 어떤 값으로 시작할까?

- learning rate가 적절히 작으면 매 반복마다 cost func의 값이 줄어든다
- 너무 작을 경우는 피하는 게 좋다

너무 작을 때는 오랜 시간이 걸려서 수렴

너무 큰 경우에는 매 반복 마다 감소하지 않고 천천히 수렴하게 됨

하지만 대부분의 문제는 theta가 매 번 감소하지 않는다

### 앤드류 응 교수님의 learning rate 찾는 방법

1. 이전 값에서 3배만큼 증가하여 시험
2. 가능한 범위 내에서 가장 작은 값과 가장 큰 값을 찾는다.
3. 그리고 그 범위 내에서 더욱 조금씩 변화를 주어 적당한 learning rate를 찾는다

---

# Features and Polynomial Regression

## feature를 간단하게 선택하는 방법 & 적절한 feature의 선택으로 강력한 학습 알고리즘을 만드는 방법

예를 들어서 집의 가격을 판단할 때 집의 가로 길이, 세로 길이가 중요한 요소라고 가정하자

이때
x<sub>1</sub> = frontage(가로길이)

x<sub>2</sub> = depth(세로길이)

이렇게 하면 feature의 개수가 2개가 된다. 하지만 새로운 방식으로 이해하면

x<sub>1</sub>= 집의 크기(가로 * 세로)

가 되기 때문에 가장 기본적인 가설의 형식(1차 함수)을 만들 수 있다.

## polynomial regression(선형 회귀를 이용하여 복잡한 비선형 함수에 적용)

polynomial regression = 다항 회귀

multivariant linear regression의 구조를 이용하여 알고리즘을 수정하는 것이 가능하다.

---

# Normal Equation

- 특정 선형 회귀 문제에서 파라미터 θ의 최적의 값을 구하는 방법
- 지금까지는 gradient descent를 선형회귀에 사용했고 J(θ)를 최소화 하기 위한 것으로 gradient descent를 여러 번 반복하고 나면, 최소값으로 수렴하였다.
- 하지만 Normal Equation는 θ를 분석적으로 구하는 방법, 한 번의 실행으로 최적의 값을 구함

\theta = (X<sup>T</sup>X)<sup>-1</sup>X<sup>T</sup>y

## Gradient Descent와 Normal Equation 중에 결정하기

Gradient Descent

장점:

1. n 이 클 경우에 효과적이다.

단점:

1. 적당한 learing_rate를 찾아야한다.
2. 많은 반복이 필요하다

Normal Equation

장점:

1. learning_rate를 찾을 필요가 없다
2. 반복을 할 필요가없다

단점:

1. (X<sup>T</sup>X)<sup>-1</sup>을 찾아야한다. n이 크면 클수록 힘들다
    - feature의 개수가 n 이라면 X는 m * n
    (X<sup>T</sup>X)의 사이즈는 n * n이 될 것이다
    - 행렬의 역행렬을 구하는데 걸리는 시간은 O(n<sup>3</sup>)이다

즉, n이 작으면 gradient Descent, 크면 Normal Equation
크다 작다의 기준은 10^6 기준

---

# Normal Equation Noninvertibility

Norrmal Equation이 적용이 안되는 경우

(X<sup>T</sup>X)<sup>-1</sup>이 없는 경우

- 역행렬을 구할 수 있는 행렬은 한정되어 있음(비가역행렬(non-invertible matrix), 특이행렬(singular matrix), degenerate matrix 라고 부름)
- 하지만  (X<sup>T</sup>X)<sup>-1</sup>이 없는 경우는 거의 없음
- octave에서 역행렬을 구하는데 pinv(pseudo-inverse)를 사용하면 강제로 값을 구할 수 있다

### 역행렬이 없는 원인

1. 문제에 불필요한 feature를 가지고 있는 경우
예시로 x<sub>1</sub> = size in feet<sup>2</sup>, x<sup>2</sup>=size in m<sup>2</sup>
여기서 x<sub>1</sub>과 x<sub>2</sub>의 관계를 만들 수 있는데
    - x<sub>1</sub>=(3.28)<sup>2</sup> * x<sub>2</sub>

    이처럼 두 feature가 서로 관련이 있고 이와 같은 선형방정식이라면 역행렬이 없다는게 즉명됨

2. 많은 feature를 가지고 학습 알고리즘을 사용할 때
feature가 많은데 데이터의 개수가 적으면 방정식을 계산하지 못하기 때문에
    - 이럴 때에는 feature를 몇 개를 없애거나, egularization을 사용
- 역행렬이 없을 경우 응교수님의 추천 방법은 feature를 보고 불필요한 feature를 제거하는 것
