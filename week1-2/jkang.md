# Linear Regression with One Variable

### Model Representation

1. x<sup>i</sup>는 `input`을 뜻하고, y<sup>i</sup>는 `output`을 뜻함
2. (x<sup>i</sup>, y<sup>i</sup>) 는 하나의 `training sample`을 뜻함
   - 학습할 때 사용되는 최소의 단위, pair라고 이해하면 될듯
   - 이것들이 모이면 `training set`
   - Supervised Learning은 `training set`을 활용해서 y값을 최대한 잘 예측할 수 있는 h(x)를 찾는 것임
     - 여기서 h(x)는 `hypothesis`라고 불림
3. 집깂 예측과 같이 어떤 범위 내에서 값을 예측하는 것을 `regression`이라고 함.
   - O / X 퀴즈처럼 정답과 오답으로 값을 나눌 수 없을 때

### Cost Function

1. `cost function`을 활용하면 `hypothesis`의 정확도를 예측할 수 있음

   - 두 값의 차이를 제곱한 값의 평균을 낸 것
   - 제곱을 한 값의 평균을 내는 것은 어떤 h(x)는 y보다 크고 어떤 h(x)는 작을 수도 있기때문
   - 평균내면 어쩌면 0될지도 모름. 완벽하지 않은데 완벽한 것처럼 보일지도

2. 일반적으로 일직선을 찾고자 할 것임

   - 만약 일직선이 모든 `training set`을 통과하면 J(/theta<sub>0</sub>, /theta<sub>1</sub>)은 0임
   - 예측값과 실제값의 차이가 없기 때문
   - 따라서 우리의 목표는 J(/theta)가 0이 되기를 바라는 것
     - 미분값이 0인 지점
     - 빗변의 기울기가 0임

3. 예로 들어준 건 1차원적이나 실제로는 3차원인 경우가 많음
   - 이때는 `countour plot`이라고 하는 등고선 그래프가 활용됨
   - 2차원의 등고선 그래프에서는 가장 가운데쯤(산으로 따지면 정상) 이 J(/theta)인 경우

### Gradient Descent

1. Gradient Descent. 말 그대로 조금씩 작아지는 것.

   - /theta<sub>0</sub> 과 /theta<sub>1</sub>의 값을 dynamic하게 바꿔가면서 J(/theta)가 가장 작은 곳을 찾아가는 과정임
   - 여기서는 dynamic이라는 성질이 중요한데, 하나를 먼저 바꾸고 두번째 값을 바꾸는 것이 아니라 두개를 동시에 바꿔야함
     - 하나를 바꾸고 다른걸 바꾸고 이런식으로 하면 먼저 변환된 값이 다음 값에 영향을 미치기 때문

2. `Learning Rate`의 중요성

   - 새로운 값을 배정/치환할 때 사용되는 magnitude라고 보면 됨. 세기? 정도?
   - 너무 작으면 시간이 너무 오래걸리고 너무 크면 overshoot해서 J(/theta)가 mininum인 곳을 찾을 수 없음
   - 적당한 값을 고르는 것이 중요함
     - 적당한 값을 잘 고르면 언젠가는 minimum에 도달할 수 있음
     - 따라서 한 번 정하면 이걸 계속해서 줄일 필요는 없음

3. Batch Gradient Descent
   - `training set`전체를 훑는것,
   - local minima에 도달해서 거기서 빠져나오지 못하는 것을 대비하는듯 함
   - 같은 `training set`을 사용하지만 learning rate를 바꾸는듯?
