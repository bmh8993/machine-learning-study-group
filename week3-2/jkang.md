# Regularization

- 문제 해결을 위해 정보를 추가하는 것

## The problem of overfitting

- 어떻게든 추세선을 맞추려고 별짓을 다하는 느낌
- training set에서는 정답을 가져올 수 있지만, training set에 포함되지 않은 데이터가 들어올 경우 에러가 발생할 확률이 높음
- 그래서 아래와 같은 방법들을 추천함
  - feature수를 줄임
    - 덜 중요한 것들을 제거하는 것 (x<sub>i</sub> 에서 i == n 이었다고 하면, 이걸 i == n-20 과 같은 식으로 수정)
  - Regularization
    - 변수들을 모두 가지고 가되, 그들의 가중치를 조절하는 것
    - i == n이나 θ<sub>1</sub>, θ<sub>2</sub>등의 값을 조절함
      - 그것들이 영향을 덜 미치도록 -> 덜 중요하니까 덜 영향을 미치는게 맞는듯

## Cost Function

- 앞의 상수를 조절하여 해당 변수가 끼치는 영향을 조절할 수 있음
- lambda라는 regularization parameter가 추가됨
- lambda가 너무 크면 어떡하나?
  - 큰게 나쁜것은 아님
  - 하지만 overfitting을 해결할 수 없음
  - underfitting될지도 -> training set 조차도 못맞출지도 모름
  - gradient descent가 global mininum을 갖지 못할지도 모름

## Regularized Linear Regression

- lambda와 함께 새로운 행렬이 추가됨
- (0,0) == 0이고 나머지 diagnal 은 1임

## Regularized Logistic Regression
