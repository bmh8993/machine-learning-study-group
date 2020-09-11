# 1주차

# What is Machine Learning?

### `Tom Mitchell`의 Machine Learning 정의

`Tom Mitchell`의 학습 과제 중심 Machine Learning 정의

- 프로그램이 일정 수준의 작업 성능(P)를 가지고 작업(T)을 수행한다고 했을 때, 경험(E)이 증가함에 따라 작업(T)를 수행하는 성능(P)이 향상될 수 있다.
- 이때 경험(E)로 부터 학습(learn)을 했다고 표현한다.

***즉, 경험(E)이 증가함에 따라 작업(T)을 수행하는 작업 성능(P)이 향상***

### 예시1. 체커 게임

경험(E) → 같은 게임을 수만 번 반복하는 과정

작업(T) → 체커 게임을 수행하는 행위

작업 성능(P) → 프로그램이 다음 판을 새로운 상대로 했을 때 그 판을 이길 `확률`

### 예시2. 이메일 프로그램

경험(E) → 유저가 메일을 스팸/정상 메일로 분류하는 것을 컴퓨터가 관찰하는 것

작업(T) → 스팸 메일 선별/신고하기

작업 성능(P) → 정확하게 분류된 메일의 비율

# Supervised Learning

### 지도학습(Supervised Learning)

- 우리가 알고리즘에게 데이터 집합을 주는데, 각 데이터에 '정답'이 포함돼있는 것
알고리즘의 역할은 '정답'을 더 많이 만들어내는 것
- 입력값에 대한 label이 존재

---

`상황 1` Housing pricie prediction

<img width="579" alt="Housing pricie prediction" src="https://user-images.githubusercontent.com/45564139/92838819-37294500-f41a-11ea-8afd-c278026f47ca.png">

- 집과 관련된 데이터가 있음
- 750평의 집을 팔려고 할 때 가격은?

### 회귀 문제(regression problem)

- 회귀문제라고 함은 연속된 값을 가진 결과를 예측하려 한다는 것
- 회귀는 보통 연속적인 숫자, 즉 예측값이 float 형태인 문제들을 해결하는데 사용된다.
- 가격은 사실 불연속이지만, 연속된 값을 가진 숫자라고 생각하고 회귀라는 용어는 우리가 이런 연속이라는 특징을 가진 값을 예측하려 한다는 것을 뜻함

⇒ 값을 두고 기준(그래프)을 그리는 것

연속 → 예측값 즉, 가격은 특정한 타입으로 분류 가능하지 않다. 100, 200, 300, 이런식으로 분류가 가능하지 않다.

---

`상황 2` Breast cance

<img width="579" alt="Breast cancer" src="https://user-images.githubusercontent.com/45564139/92839050-7eafd100-f41a-11ea-8675-c352d31eeb99.png">

- 종양의 사이즈에 따라 유방암인지 판단

<img width="309" alt="Breast cance 2 feature" src="https://user-images.githubusercontent.com/45564139/92839074-84a5b200-f41a-11ea-953b-5f7006713930.png">

### 분류 문제(classification problem)

- 데이터 집합이 주어졌을 때 학습 알고리즘이 해볼 수 있는 건, 데이터에 직선을 하나 맞춰서 악성 종양을 양성 종양과 분리해보는 것
- 하나 이상의 특징(feature, attribute)을 가지고 데이터 집합을 분류
- 무수히 많은 속성을 가지고 분류 가능
- 서포트 벡터 머신으로 무한한 개수의 특성을 다룰 수 있다.

⇒ 기준(그래프)을 두고 값을 분류 하는 것

불연속 → 특정한 타입으로 분류 가능, 예시처럼 양성, 악성 두 가지 뿐만아니라, 유방암의 종류 `cancer type 1` , `cancer type2` , `cancer type3` ...처럼 타입이 분류 가능하면 불연속이라 판단.

---

# Unsupervised Learning

### 비지도학습(Unsupervised Learning)

<img width="377" alt="Unsupervised Learning" src="https://user-images.githubusercontent.com/45564139/92839089-88d1cf80-f41a-11ea-9411-7d5907d2bf44.png">

- 데이터가 주어지면, 어떤 레이블이 없을 수도 있고, 있을 수도 있다
- 그래서 무엇을 할지, 또 각 데이터가 무엇인지 알 수 없다.
- 대신 "여기 데이터가 있는데, 여기서 어떤 구조를 찾을 수 있습니까"라고 물을 뿐
- 비지도 학습 알고리즘은 이 데이터를 두가지 서로 다른 클러스터(데이터 묶음)로 구분 지을 수도 있다.
- 그래서 이것은 클러스터링 알고리즘이라고 불린다.
