### Multiple Features

- 학습할 때 고려할 변수가 여러개임.
- 집값 예측이라고 하면 집의 위치만 생각할 게 아니라, 집의 위치, 건축년도, 사고이력 등을 봐야함
- x<sub>j</sub></sub><sup>i</sup>라고 했을 때 i는 몇 번 째 training sample인지, j는 어떤 샘플인지를 나타냄
  - 예를들면 x<sub>2</sub><sup>3</sup>는 3번 째 샘플에서 2번값이 무엇인지를 뜻함
    - 수식으로 표현하면 이런느낌임
    - h<sub>\theta</sub>(x) = \theta<sub>0</sub> + \theta<sub>1</sub>x<sub>1</sub> + \theta<sub>2</sub>x<sub>2</sub> + \theta<sub>3</sub>x<sub>3</sub> + ... + \theta<sub>n</sub>x<sub>n</sub>
    - 여기서 \theta 값들을 찾는 것이 학습의 목표.
    - \theta값들을 구하면 누군가 새로운 x 데이터들을 가져왔을 때 `output`인 `y`값을 예측할 수 있음
- 저 긴 수식을 짧게 쓰면 아래와 같음
  - h<sub>\theta</sub>(x) = \theta<sup>T</sup>x
  - matrix \theta는 하나의 row를 가진 matrix인데 transpose하면 column하나짜리로 바뀌고, 그러면 row 하나짜리 matrix인 x와 곱셈이 가능해짐

### Gradient Descent for Multiple Variables

- 그래프에서 global minima를 찾는 것.
- 수식이 좀 복잡한데 여기서 쓰기 어려움
  - 여기서 핵심은 \theta<sub>0</sub>, \theta<sub>1</sub>, \theta<sub>2</sub> 가 있다고 하면, 저 세개를 한번에 바꿔야함. 0을 바꾸고 그 값을 사용해서 1을 바꾸고 이러면 dynamic하지 못하기 때문

### Feature Scaling

- 값이 너무 클 경우 최저값을 찾는 Gradient Descent의 특성상 범위가 커져서 시간이 오래걸릴 수 있음.
  - range가 좁으면 \theta가 더 빨리 작아지고, 그러면 더 빨리 정답을 찾을 수 있음.
  - 일반적으로 scaling은 sample값에서 평균을 뺀 값을 sample의 갯수로 나눔

### Learning Rate

- 복잡한 수식에서의 \alpha 값. 너무 작으면 시간이 너무 오래걸리고 너무 크면 overshoot됨
- 너무 크면 J(\theta)가 작아지지 않고 커질수도 있음.

### Polynomial Regression

- best fit line이 linear가 아닐 경우를 뜻하는듯
  - 일반적으로 polynomial이면 억지로 끼워맞춘 느낌이 있는데 머신러닝은 다른가봄
  - polynomial을 사용하려면 scaling range가 매우 중요함. 제곱, 세제곱을 더할경우 range가 점점 더 커지기 때문임. 0 ~ 1,000,000 사이의 값은 더욱 오래걸림
