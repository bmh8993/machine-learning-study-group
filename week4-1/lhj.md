# Neural Networks

## Motivations
- 매우 많은 features들이 있을 때 머신러닝 시 좋은 결과를 내기 위한 해결책

- Non-linear Hypotheses
  - 일반적으로 기계분류에서 n은 대부분 매우 큼
  - n이 클떄 비선형적인 분류를 위해 요소를 추가하는 방식은 좋지 않음

- Suppose you are learning to recognize cars from 100\times100100×100 pixel images (grayscale, not RGB). Let the features be pixel intensity values. If you train logistic regression including all the quadratic terms (x_i,x_j) as features, about how many features will you have?
- A : 50 million ( 5 x 10^7 )

- Neurons and the Brain
  - 뇌를 모방하는 알고리즘, 계산에 대한 비용이 큼
  - 컴퓨터의 성능이 좋아짐에 따라 다시 각광
  - 하나의 학습알고리즘을 사용하는 뇌를 모방하는 것

## Neural Networks
- Model Representation
  - x_0~x3 : input wire, 노란색 원의 뉴런, output wire
  - 일반적으로 x_1, x_2, x_3 노드 추가, x_0는 필요한 상황에 추가적으로 표현
  - x_0 = (바이어스 유닛)bias unit/neuron(가독성을 높이기 위해 생략하기도함) 출력값 항상 1
  - activation function
    - g(z) = 1/1+e^-z
  - raw한 features(x1,x2,x3) 를 통해 그대로 학습하는 Logistic Regression 과 달리 Neural Network는 고유한 features 들인 a_1, a_2, a_3를 학습하여 h_theata(x)를 만든다.
  - Architecture : 서로 다른 뉴런들이 연결되어있는 구조
  - Intput Layer(첫번째 레이어), Output Layer(마지막 레이어, 하나의 뉴런을 갖고있음), 나머지 Layer는 Hidden Layer(training set에서 볼수 없기 때문)
  - 위첨자 : 레이어  아래첨자 : x번쨰 유닛
  - 세타^(i) 계산법 : s_(i+1) x (s_i) + 1

## Applications
- Example and intuitions
  - AND 연산 : 가중치 설정, AND 연산
  - OR 연산 : 1or 0 = 1, 0 or 0 = 0, 1 or 1 = 1
  - NOT 연산 : 입력 x1과 받대되는 출력값
    - x1= 0: g(10)~ 1, x1 = 1 : g(-10) ~ 0
------ Input, Output layer로 2개의 layer만 사용
  - XNOR 연산 : 입력이 같은값이면 1, 아니면 0
    - a1 = x1, x2 AND 연산, a2 = NOT x1 AND NOT x2 연산
    - h_theta(x) = a1 or a2
------ Hidden Layer까지 총 3개의 layer를 사용
- Example and intuitions 2
- Multiclass Classification
  - Neural Network를 사용하여 해결을 해야할 경우 One-vs-All 방식 사용
  - 4개의 카테고리로 분류하기 위해 4개의 Output Unit이 필요, 각각 Binary Value를 갖는 4차원 벡터가 됨. 가설함수의 근사치를 갖는 y는 4개의 벡터중 하나의 벡터를 갖음
  - multiple classification에서 가중치 계산
    - 세타^(i) 계산법 : s_(i+1) x (s_i) + 1
    - 10개의 카테고리로 분류하려고한다, 3개의 레이어가있고, 히든레이어는 2번레이어 이다.
    히든레이어 2는 5유닛을 갖고있다, one-vs-all method를 사용하여 묘사할때 세타(2)는 얼마나 많은 elements를 갖는가
      - 세타2 = ((s_2)+1) x s_(3) ?  = 60
      - output unit이 10개가 필요하기때문(10개의 카테고리로 분류)
