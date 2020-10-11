# Logistic Regression

## Classification

- 0 과 1의 값을 갖는 것. O / X 퀴즈 느낌?
- 스팸이냐 아니냐, 암세포냐 아니냐 등
- 0: negative class, 1: positive class
  - 암세포냐 아니냐로 봤을 때 0이 아니다 1이 맞다

### Thresholod

- 단어 뜻 그대로 하면 문지방을 뜻함
- 이걸 넘어야 1(positive class)이다.
- h<sub>θ</sub>(x) $\geq$ 0.5, 일 경우 y = 1, 0.5보다 작으면 y=0
- outlier가 있어서 linear projection이 이상해질 경우, 원래 1인것도 0으로 여겨질 수 있음

## Hypothesis Representation

- 0 $\leq$ h<sub>θ</sub>(x) $\leq$ 1인 것을 찾아야함
- h<sub>θ</sub>(x) => y = 1 일 확률
- h<sub>θ</sub>(x) = g(θ<sup>T</sup>x)
- h<sub>θ</sub>(x) = 1 / (1 + e<sup>-θ<sup>T</sup>x</sup>)
  - 이 모양을 sigmoid function이라고 부름

## Decision Boundary

- 0과 1을 나누는 경계선 느낌

## Cost Function

- y = 1, h<sub>θ</sub>(x) = 1 이면 Cost = 0.

  - 하지만 h<sub>θ</sub>(x) = 1 -> 이면 cost -> infinity

- y = 1 이면, cost function = -log(h<sub>θ</sub>(x))
- y = 0 이면, cost function = -log(10h<sub>θ</sub>(x))

## Simplified cost function and gradient descent

- 더하면 1이라고 놓고 식을 하나로 합친것밖에 안됨
- 간단하다고 볼 수는 없을듯
