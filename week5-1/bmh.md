# Cost Function

> Neural Network의 Cost function에 대해 알아보자

<img width="699" alt="스크린샷 2020-11-08 20 30 38" src="https://user-images.githubusercontent.com/45564139/98463781-443b9800-2201-11eb-8e8e-095f62cafde0.png">

$L$ = 네트워크 레이어의 총 개수

$S_1$ = 각 레이어의 개수

```
그림에서 s_1 은  Layer 1이기 때문에 3개, s_2는 Layer 2이기 때문에 5
```

$S_L$ = Layer의 총 개수이므로 마지막 레이어를 의미

$K$ = output의 개수

---

`Binary classification`은 y = 0 or 1일 때밖에 없으므로 $K$ = 1

지난 수업 기준`Multi-class classification`   $K$는 무조건 3보다 크다($S_1$이 3이라서 그런가?)

<img width="705" alt="스크린샷 2020-11-08 20 31 04" src="https://user-images.githubusercontent.com/45564139/98463787-56b5d180-2201-11eb-852a-98608b855476.png">

<img width="700" alt="스크린샷 2020-11-08 20 31 17" src="https://user-images.githubusercontent.com/45564139/98463789-5b7a8580-2201-11eb-93f8-08748343a465.png">

Logistic regression에서 NN의 cost function으로의 변형

# Backpropagation Algorithm

Backpropagation은 neural-network에서 cost function을 최소화 하기위한 기법

→ 최적의 parameter들의 집합인 theta 값을 구하여 최소의 $J(Θ)$를 구하는 것

→ Θ를 사용해서 $J(Θ)$의 값을 구하고 편미분을 해서 최소의 값을 만드는 Θ를 찾을 수 있다.

## Forward propagation

<img width="667" alt="스크린샷 2020-11-08 20 33 38" src="https://user-images.githubusercontent.com/45564139/98463829-b0b69700-2201-11eb-9466-9b282962462d.png">

```
h_Θ(x)를 구하는 방식

값을 구하는 과정의 예시인데 앞으로 전파를 시키는 방식
1. a^(1)은 첫번째 레이어의 활성값, x에 대입
2. z^(2)는 Θ^(1) * a^(1)
3. a^(2)는 sigmoid 함수에 z^(2)를 적용, 두번째 레이어의 활성값

반복
```

<img width="704" alt="스크린샷 2020-11-08 20 33 45" src="https://user-images.githubusercontent.com/45564139/98463831-b3b18780-2201-11eb-98b9-1069b67c3baa.png">


각 노드에 대해 $\delta_j^{(l)}$을 계산하는 것

$\delta_j^{(l)}$의 의미는 l 레이어의 노드 j에 대해서 오류를 잡는다는 의미

$a_j^{(l)}$의 의미는 l 레이어의 노드 j에 대해서 활성화를 의미

내가 뽑고자 하는 target값과 실제 모델이 계산한 output이 얼마나 차이가 나는지 구한 후 그 오차값을 다시 뒤로 전파해가면서 각 노드가 가지고 있는 변수들을 갱신하는 알고리즘인 것이다.

- 참고

<img width="320" alt="스크린샷 2020-11-08 20 33 51" src="https://user-images.githubusercontent.com/45564139/98463832-b7450e80-2201-11eb-9baf-da6eb83a185b.png">

---

### 결론

Input Data인 x가 입력이 되었을 때 현재 v, w 값에 의해 출력되는 값이 실제 Input Data의 출력 값과 일치하다면,해당 네트워크는 예측을 정확하게 수정한 것이기 때문에 수정할 필요가 없음.
반면, Input Data의 입력에 대해 네트워크가 예측한 값이 실제 나와야 하는 값과 다르다면,
네트워크는 향후 같은 상황에서 제대로 예측하기 위해 네트워크를 수정해야 함.(v, w 웨이트 값들)

# Gradient Checking

- 참고

    [http://blog.naver.com/PostView.nhn?blogId=samsjang&logNo=221042879658&categoryNo=0&parentCategoryNo=0&viewDate=&currentPage=1&postListTopCurrentPage=1&from=postView](http://blog.naver.com/PostView.nhn?blogId=samsjang&logNo=221042879658&categoryNo=0&parentCategoryNo=0&viewDate=&currentPage=1&postListTopCurrentPage=1&from=postView)

Train이 제대로 되고 있는지 확인하는 방법의 하나이다.

Backpropagation은 구현이 매우 어렵기 대문에 버그가 발생해도 어디서부터 고쳐야할지 마땅하지가 않다. 그럴 때 gradient checking 을 사용한다.

<img width="701" alt="스크린샷 2020-11-08 20 33 56" src="https://user-images.githubusercontent.com/45564139/98463835-ba3fff00-2201-11eb-89e9-e75e12aa18d6.png">


## 아이디어

- 기울기하강과 비슷하다. 미분을 하지 않고 기울기를 만들어낸다

    <img width="425" alt="스크린샷 2020-11-08 20 34 03" src="https://user-images.githubusercontent.com/45564139/98463839-be6c1c80-2201-11eb-9e71-1dd9db6f1c02.png">

- 세타를 기준으로 Epsilon이라고 정의된 수치만큼 더하고 빼서 그 사이의 J값을 직선으로 연결하면 빨간색 선과 같이 본래의 것과 비슷한 기울기를 가지는 직선을 만들어 낼 수 있다.
- `J를 세타로 편미분한 값 = 위의 식 = 기울기` 이때 Epsilon이라는 값은 아주 작은 0.0001 정도의 값이 된다.
사이가 많이 벌어지면 기울기와 전혀 다른 값이 되므로 아주 작은 값으로 만든다.
- 설명한 개념을 사용해서 Parameter 세타를 편미분하여 계산할 때 아래 그림과 같이 편미분의 대상이 되는 세타에 +E, -E를 해주고 2E로 나누어주어 구현을 하면 된다.

    <img width="663" alt="스크린샷 2020-11-08 20 34 09" src="https://user-images.githubusercontent.com/45564139/98463842-c1ffa380-2201-11eb-804c-dac8c7a7651c.png">

# Random Initialization(랜덤 초기화)

***NN은 파라미터를 무작위 초기화를 해야한다***

경사하강법 알고리즘이나 고급최적화 알고리즘을 실행할 때 파라미터 쎄타의 초기값을 결정해야한다.
파라미터 쎄타의 초기값을 0으로 설정하면 로지스틱 회귀에서는 제대로 동작하겠지만, 인공지능 망에서는 제대로 동작하지 않는다.
→즉, 가중치인 파라미터 쎄타가 동일한 값을 가지는 대칭문제가 발생한다.
→ 파라미터 또는 가중치 θ는 - ε과 +ε 사이의 값으로 랜덤  초기화를 해야한다.
