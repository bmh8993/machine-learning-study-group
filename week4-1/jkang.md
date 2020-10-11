# Neural Networks

## Non-linear hypothesis & Neurons and the Brain

- 뇌가 인식하는 것에 대한 설명
- 청력을 담당하는 부분도 학습을 통해 시력을 담당하게 될 수 있음

## Model Representation

- neuron을 보면, 신호를 받는 부분 (dendrite)와 신호를 내보내는 부분 (axon)이 나누어짐
- 여러개의 섹션을 통해 output layer가 만들어짐

  - machine learning에서는 input layer가 있고, 이후 여러 단계의 hidden layer를 거쳐 output layer가 만들어짐
  - input layer와 hidden layer들이 어떻게 연결되어 있는지, 혹은 어떻게 연결시킬지를 파약해야 함

- a<sub>1</sub><sup>(2)</sup> = g(z<sub>1</sub><sup>(2)</sup>)
- a<sub>2</sub><sup>(2)</sup> = g(z<sub>2</sub><sup>(2)</sup>)
- a<sub>3</sub><sup>(2)</sup> = g(z<sub>3</sub><sup>(2)</sup>)

if x = a<sup>(1)</sup>,
z<sup>(j)</sup> = Θ<sup>(j-1)</sup>a<sup>(j-1)</sup>
같은 논리로, z<sup>(j+1)</sup>인 경우에는 우측이 j의 superscript를 가짐

- 수식으로 문제는 풀 수 있는데 정확하게 이해는 못한듯...
