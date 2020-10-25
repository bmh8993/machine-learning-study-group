# Neural Networks: Learning

## Cost Function

- L : 네트워크 안의 layer 수
- s<sub>l</sub> : layer **l** 안에 있는 유닛의 숫자
- K: output unit/class의 수

- h<sub>theta</sub>(x)<sub>k</sub> = k<sup>th</sup> output의 hypothesis
  - logistic regression에서 사용한 cost function의 공식을 살짝 재사용함
    - 하지만 몇몇 합계들(sigma를 사용한 항목들)이 추가됨
      - 대괄호 안에 output node의 갯수만큼 도는게 추가됨(k=1, K에 해당하는 것)
    - theta를 포함한 항렬이 여러개일 수 있음
      - 현재의 theta 행렬의 column 수는 현재 layer의 node의 갯수와 일치함
        - transpose해서 사용하려면 이게 맞을 수 밖에 없음
      - 현재 theta 행렬의 row 수는 다음 layer의 node의 갯수와 일치함
      - 차이가 negative(음수)일 수 있어서 제곱을 추가함

## Backpropagation Algorithm

- backpropagation: cost function을 최소화하는 것

1. a<sup>(1)</sup> := x<sup>(t)</sup>
2. 각 layer들에 대해 a<sup>(l)</sup>을 계산
3. delta<sup>(L)</sup> = a<sup>(L)</sup> - y<sup>(t)</sup>

   - L은 layer의 총 갯수를 뜻함.
   - a<sup>(L)</sup>은 지난 layer의 activation unit의 output의 벡터값
     - 에러는 실제값과 예측값의 차이일뿐임
     - 결국 이 에러를 최소화 하는것이 머신러닝의 역할

4. layer의 delta값은 현재 layer의 theta 행렬과 다음 layer의 delta값을 곱해서 얻어짐
   - 그리고 그 함수를 g'으로 곱함
     - g'은 z<sup>l</sup>이라는 input의 activation 함수 g의 미분값임

## Backpropagation Intuition

- delta<sub>j</sub><sup>(l)</sup>는 a<sub>j</sub><sup>(l)</sup>의 에러를 나타냄
  - 에러는 결국 cost function의 미분값에 해당
