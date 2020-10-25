# Neural Networks : Learning
## Cost Function and Backpropagation(역전파)
### Cost Function
#### Neural Network
- L = total num of layers in network
- s_l = num of units(not counting bias unit) in layer l
- k = num of units in output layerRecent resurgence : State-of-the-art technique for many applications

#### Classification
- Binary classification
  - y = 0 or 1, 1output unit
- Multi-class classification (K calsses)
  - K개의 분리된 클래스들에대해 각각의 Output unit을 가짐
  - K output units
  - 실수가 아닌 K차의 Output Vector h_theta(x)
  - K는 바이너리가 아니므로 k >= 3 만족

#### Cost Function
- Neural Network에서 사용할 Cost Function은 Logistic Regression의 비용함수를 일반화시킨 함수
- K개의 Output을 가짐
- h_theta(x)는 k차원의 행령, k_theta(x)_i는 행렬의 i번째 요소
- 각각의 Output Unit h_theta(x)를 모두 더한것

- Suppose we want to try to minimize J(\Theta)J(Θ) as a function of \ThetaΘ, using one of the advanced optimization methods (fminunc, conjugate gradient, BFGS, L-BFGS, etc.). What do we need to supply code to compute (as a function of \ThetaΘ)?
    - J(Θ) and the (partial) derivative terms ∂/∂𝜃_ij^(l) for every i,j,l

- the double sum simply adds up the logistic regression costs calculated for each cell in the output layer
- the triple sum simply adds up the squares of all the individual Θs in the entire network.
- the i in the triple sum does not refer to training example i

### BackPropagation Algorithm(역전파 알고리즘)
- J(Θ)를 최소화하기 위해 매개변수 Θ를 찾아야함
  - 그러기 위해 경사도하강법이나 다른 최적화 알고리즘을 사용해야함
  - J(Θ)를 구하고 이를 편미분하는 것을 구해야함
  - Θ_ij^(l) 은 실수 임
- Cost Function을 최소화 시키는 알고리즘

- Given training set {(x(1), y^(1)⋯(x^(m), y^(m)))}
  - set Δ_i,j^(l) := 0 for all (l,i,j)

#### Gradient Computation
- 𝛿_j(4) = a_j^(4) - y_j
- 𝛿^(3) = (Θ^(3))^T𝛿^(4). * g'(z^(3)) // g'(z^(3)) : a^(3) .* (1-a^(3))
- 𝛿^(2) = (Θ^(2))^T𝛿^(3). * g'(z^(2)) // g'(z^(2)): a^(2) .* (1-a^(2))
- Suppose you have two training examples (x^{(1)}, y^{(1)})(x (1),y (1)) and (x^{(2)}, y^{(2)})(x(2),y(2)). Which of the following is a correct sequence of operations for computing the gradient? (Below, FP = forward propagation, BP = back propagation).
  - FP using x^{(1)}x(1) followed by BP using y^{(1)}y(1). Then FP using x^{(2)}x(2) followed by BP using y^{(2)}y(2).

### Backpropagation Intuition


## Backpropagation in Practice

### Implementation Note: Unrolling Parameters
### Gradient Checking
- 역전파를 이용하여 많은 버그가 발생할 수 있는데, 이를 Gradient Descent나 다른 최적화 알고리즘에 적용하면 Cost Function이 잘 감소하여 문제가 없는거서철 보일 수 있다.
- 성능을 저하시키는 Bug를 발견하지 못할 확률이 존재
- 이를 해결하기 위해 Gradient Checking을 Model에 적용하여 검사하는것이 필요함

- What is the main reason that we use the backpropagation algorithm rather than the numerical gradient computation method during learning?
  - The numerical gradient algorithm is very slow.

### Random Initialization
- Optimization Algorithm 을 위한 초기 theta값 지정
- 초기 theta = 0 이면 Logistic Regression에서만 잘 작동하고 Neural Network 에서는 올바르게 작동하지 않음

- Symmetry Problem
  - 모든 i, j, L에 대하여 theta_ij^(l) = 0 으로 초기화했다고 가정
    - 결과값
      - theta_01^1 = theta_02^2
      - a_1^(2) = a_2^(2)
      - 𝛿_1^(2) = 𝛿_2^(2)
      - ∂/∂𝜃_01^1*J(𝜃) = ∂/∂𝜃_02^2 J(𝜃)
  - 매번의 업데이트가 끝날떄마다 parameter theta가 같아지고, Layer의 Feature도 같은 값을 갖게 된다. 이런 상황이 지속되면 Hidden Unit이 많은 경우라 하더라도 모든 Hidden Unit이 같은 Feature를 가지며 결국 하나의 Feature를 갖는 Neural Network가 되는 문제
  - Random Initialization을 사용하여 Symeetry Breaking을 수행
  - Initializer each Θ_ij^(l) to a random value in [−𝜖, 𝜖]

- Consider this procedure for initializing the parameters of a neural network: Pick a random number r = rand(1,1) * (2 * INIT_EPSILON) - INIT_EPSILON Set Θ_ij^(l)=r for all i,j,li,j,l. Does this work?
  - No, because this fails to break symmetry.

- If the dimensions of Theta1 is 10x11, Theta2 is 10x11 and Theta3 is 1x11.
  - Theta1 = rand(10,11) * (2 * INIT_EPSILON) - INIT_EPSILON;
  - Theta2 = rand(10,11) * (2 * INIT_EPSILON) - INIT_EPSILON;
  - Theta3 = rand(1,11) * (2 * INIT_EPSILON) - INIT_EPSILON;

### Putting it Together
#### Training a neural network
- L = total num of layers in network num of input units : Feature들의 갯수 (x^(i)의 차수)
- Num of output units: Class들의 개수
- Hidden Layer: Default = 1 but if hidden layer > 1 , have same num of hidden units in every layer is better

- Hidden Unit의 수는 많으면 많을수록 좋음
- Hidden Layer가 같은 수의 Hidden Unit의 개수를 지닌다면 성능이 좋음
- Hidden Unit의 개수는 Input unit과 output unit등을 고려하여 상대적으로 선정

1. Randomly initializer weights
2. implement forward propagation to get h_thata(x^(i)) for any x^(i)
3. Implement code to compute cost function J(theta)
4. Implement backpropagation to compute partial derivatives ∂/∂𝜃_jk^(l)*J(𝜃)
5. Use gradient checking to compare ∂/∂𝜃 J(𝜃) comuted using backprop vs using numerical extimate of gradient of J(𝜃), Then disable gradient checking code
6. User Gradient Descent or advanced optimization method with backprop to ry to minimize J(𝜃) as a function of parameters 𝜃

1. 𝜃를 0에 근사한 작은 값을 초기화
2. 임의의 x에 대한 h_𝜃(x^(i))를 구하는 Forward Propagation과 J(𝜃)를 구하는 코드, 그리고 Partial derivatives를 구하기 위한 VackPropagation 코드 구현
3. 모든 Training Example(for i=1:m)에 대하여 학습
4. 그안에서 FP BP가 수행되어 𝑎^(𝑙),𝛿^(𝑙),Δ^(𝑙) 가 구해짐
5. BP가 올바르게 작동하는지 Gradient Checking 수행 후 정상작동시 꺼줌
6. 최적화 알고리즘 사용하여 최소 J(𝜃)값 구함
7. J(𝜃)가 Non-Convex면 Local Optima로 수렴할수 있지만 그 값은 Global Optima에 근접한 상당히 좋은 값임

- Suppose you are using gradient descent together with backpropagation to try to minimize J(Θ) as a function of Θ. Which of the following would be a useful step for verifying that the learning algorithm is running correctly?
  - Plot J(Θ) as a function of the number of iterations and make sure it is decreasing (or at least non-increasing) with every iteration.


#### Gradient Descent for neural network
- 2개의 Parameter값을 갖는 Neural Network에 대한 Gradient Descent 알고리즘이 수행되었을 시, 이 알고리즘은 Random 위치에서 시작하여 내리막길으 따라가며 Optima를 찾는 것
- 여기서 BP가 하는 역할은 Gradient Descent가 내려가는 방향을 체크하는 것임
