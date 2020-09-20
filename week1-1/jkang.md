### Machine Learning 소개

- 코드를 일일이 작성하지 않고 컴퓨터가 스스로 `learning` 하게 하는 것
- Tom Mitchell의 정의에 따르면 `task`에 대해 `performance`를 측정하면 `experience`를 통해 performance가 발전한다고 함
- 경험을 통해 코드가 스스로 `performance`를 올리는 것

### Supervised Learning

- 정답을 가진 데이터를 가지고 학습하는 것
  - `input` 과 `output`의 관계를 알고 학습
  - MRI보고 이건 암이다 아니다를 알고 학습
- `Regression`과 `Classification`으로 나누어짐
  - `Regression`은 continuous output
    - output이 range느낌. 집값같은경우. 3억일수도 4억일수도 5억일수도
  - `Classification`은 discrete output
    - output이 O/X 퀴즈. 맞다 혹은 틀리다

### Unsupervised Learning

- 정답을 모르고 학습함.
  - `input`과 `output`의 관계에 대해 아는 것이 없음
  - `input`들의 관계를 가지고 학습함
- `clustering`과 `non-clustering`으로 나누어짐
  - `clustering`은 `input`들을 구분지을 수 있을 때. 그들을 그룹화함
    - 학생들을 놓고 봤을 때, 그들의 거주지역, 성적, 성별, 등에 따라 나누는 것
  - `non-clustering`은 `input`들을 구분할 수 없을 때
    - 학생들을 놓고 봤을 때 누군지 식별하는 느낌
