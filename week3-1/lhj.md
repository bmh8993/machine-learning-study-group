# Classification and Representation
## Classification(분류문제)
- 0 : negative class 분류
- 1 : positive class 분류
- 선형회귀를 분류문제에 추가하는것은 좋은생각이아님
  - 벗어 난 값 하나로 그래프의 기울기가 바뀌기 때문 (negative effection)

- Classification: y= 0 or 1

- Logistic Regression
  - 0 <= h_theta(x) <= 1 (예측값의 볌위)
  - 분류 알고리즘으로 사용

To attempt classification, one method is to use linear regression and map all predictions greater than 0.5 as a 1 and all less than 0.5 as a 0. However, this method doesn't work well because classification is not actually a linear function.

The classification problem is just like the regression problem, except that the values we now want to predict take on only a small number of discrete values. For now, we will focus on the binary classification problem in which y can take on only two values, 0 and 1. (Most of what we say here will also generalize to the multiple-class case.) For instance, if we are trying to build a spam classifier for email, then x^{(i)}x
(i)
  may be some features of a piece of email, and y may be 1 if it is a piece of spam mail, and 0 otherwise. Hence, y∈{0,1}. 0 is also called the negative class, and 1 the positive class, and they are sometimes also denoted by the symbols “-” and “+.” Given x^{(i)}x
(i)
 , the corresponding y^{(i)}y
(i)
  is also called the label for the training example.



## Hypothesis Representation
- Logistic Regression Model
  - 0 <= h_theta(x) <= 1 (예측값의 볌위)
- sigmoid function = logistic function
- P(y=0|x;theta) + P(y=1;theta) = 1


## Decision Boundary
- Non-linear decision boundaries
  - h(x) = g(-1 + x_1^2 + x_2^2)
  - y = 1 , -1 + x_1^2 + x_2^2 >= 0
  - x_1^2 + x_2^2 >= 1 (circle)

- decision boundary is the line that separates the area where y = 0 and where y = 1. It is created by our hypothesis function.


# Logistic Regression Model
## Cost Function
- J(Θ) = 1/m(i=1~m,sigma(Cost(h_Θ(x^(i), y))))
  - Cost(h_Θ(x^(i)),y(i)) = 1/2 (h_Θ(x^(i) - y^(i)))^2

## Logistic regression cost function
- Cost(h_Θ(x), y) = -log(h_Θ(x)) if y =1, -log(1-h_Θ(x)) if y=0
  - Cost = 0 if y =1, h_Θ(x) = 1
  - if y =1
    - h(x)가 0에 가까워지면 cost는 무한대로감
    - y = 1 확률이 0일때를 직관적으로 보여준다
    - 만약 y=1이라는 값이 나오면 알고리즘을 다시고려해야한다, 엄청난 비용을 부과
  - if y = 0
    - -log(1-z) 함수
    - h(x)가 1에 가까워지면 cost는 무한대로 감

## Simplified Cost Funcition and Gradient Descent
- Cost(hΘ(x),y) = -ylog(hΘ(x)) - (1-y)log(1-hΘ(x))
  - Note: y= 0 or 1 always
  - 위의 두식을 한 식으로 압축한것
  - 최대우도 측정법의 원리를 이용한 통계로부터 유도된 공식(몰라도 됨)
  - voltex한 모형을 갖음
  - *logistic regression을 적용할 때 필수적으로 사용하는 비용함수*
  - 매개변수 최적화를 위해 J(Θ)를 최소화하는 Θ를 찾아야함
    - Θ 집합을 얻을 것
  - 경사하강법(Gradient Descent) 적용
    - J(Θ) = -1/m[\~]
  - Vector rise implementation
    - Θ:= Θ - α*1/m(i=1~m(sigma(h_Θ(x^(i))-y^(i))\*x^(i))

## Advanced Optimization
- Optimization algorithm
  - Gradient descent
  - conjugate gradient
  - BFGS
  - L-BFGS
- Advantages:
  - α manually하게 선택할 필요없음
  - 보통 gradient descent 보다 빠름
- Disadvantages:
  - gradient descent 보다 더 복잡함


# Multicalss Classification
## Multiclass Classfication: One-vs-all
- Musticlass classification
  - y = 0, 1조건 대신 y = 0~n까지의 경우 생각
  - ex)여러개의 태그를 가진 폴더/태그
    - 병에걸리지않음 / 감기 / 독감
    - 날씨: 맑음, 흐림, 비, 눈
  - prediction = max_i(h_Θ^(i)(x))
- 요약
  - 각각의 클래스 i에 대해 y=i일 확률을 예측하도록 함
  - 새로운 input x가 주어질때 예측을 하기 위해서 각각의 h를 새로운 x에 대해 전부 수행한 뒤 최대값이 나온 클래스 i를 고르면 된다.
  - 가장 높은 확률을 주는 i값이라면 y가 그값이라고 예측 가능함
